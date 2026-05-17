🛡️ README: Threat Hunting with MITRE ATT&CK Navigator (APT28)
Role: SOC Analyst (Sunny)
Organization: E-corp (ผู้ผลิตแร่หายากสำหรับหน่วยงานรัฐบาลและเอกชน)
Threat Actor: APT28 (Advanced Persistent Threat 28 - กลุ่มแฮกเกอร์ระดับรัฐบาลที่มีความเชี่ยวชาญสูง)
Tool: MITRE ATT&CK Navigator

📖 Executive Summary
รายงานฉบับนี้จัดทำขึ้นเพื่อวิเคราะห์และแกะรอยพฤติกรรมการโจมตี (TTPs) ของกลุ่มแฮกเกอร์ APT28 ที่มีแนวโน้มจะโจมตีองค์กร E-corp โดยใช้เครื่องมือ MITRE ATT&CK Navigator ในการกางแผนผังกลยุทธ์ (Tactics) และเทคนิค (Techniques) ทั้งหมด เพื่อเตรียมความพร้อมในการทำ Detection และ Incident Response

🕵️‍♂️ Attack Lifecycle Analysis (วิเคราะห์วงจรการโจมตีของ APT28)
เราจะแบ่งพฤติกรรมของ APT28 ออกเป็นเฟสต่างๆ ตาม MITRE Framework เพื่อให้เห็นภาพรวมของเหตุการณ์ (Storyline) ตั้งแต่เริ่มสอดแนมไปจนถึงการขโมยข้อมูล

Phase 1: Infiltration (การเจาะระบบด่านแรก)
Recon & Initial Access: APT28 เริ่มต้นด้วยการสอดแนมเป้าหมายและเจาะระบบด่านแรกไปพร้อมๆ กันผ่านเทคนิค Spearphishing Link (T1598.003 / T1566.002) โดยส่งอีเมลหลอกลวงที่แนบลิงก์อันตรายมาให้พนักงานในองค์กร

Resource Development: เพื่อให้การส่งอีเมลดูแนบเนียนและน่าเชื่อถือ กลุ่มนี้มักจะทำการแฮก Email accounts (T1586.002) ของบุคคลภายนอกมาก่อน เพื่อใช้เป็นฐานในการส่ง Spearphishing

Phase 2: Execution & Persistence (การรันโค้ดและการฝังตัว)
User Execution: เมื่อพนักงานได้รับอีเมล APT28 จะอาศัยความผิดพลาดของพนักงาน (Social Engineering) ในการกด Malicious Link (T1204.001) หรือรัน Malicious File (T1204.002) ด้วยตนเอง

Scripting Interpreters: เมื่อมัลแวร์ทำงาน มันจะเรียกใช้เครื่องมือที่มีอยู่แล้วในระบบ (Living off the Land) อย่าง PowerShell (T1059.001) และ Windows Command Shell (T1059.003) เพื่อรันสคริปต์อันตราย

Maintaining Persistence: เพื่อรับประกันว่ามัลแวร์จะทำงานทุกครั้งที่เหยื่อเปิดคอมพิวเตอร์ APT28 จะฝังค่าสคริปต์ที่ถูกทำ Obfuscation ไว้ใน Registry Run Keys / Startup Folder (T1547.001)

Phase 3: Evasion & Discovery (การหลบหลีกและการสำรวจเครือข่าย)
Defense Evasion: เพื่อหลบเลี่ยงการตรวจจับจากระบบ EDR/Antivirus พวกเขาใช้วิธี System Binary Proxy Execution โดยอาศัยไฟล์ระบบที่ปลอดภัยอย่าง Rundll32 (T1218.011) ในการประมวลผลโค้ดมัลแวร์แทน

Discovery: เมื่อฝังตัวสำเร็จ แฮกเกอร์จะติดตั้งเครื่องมืออย่าง tcpdump เพื่อทำ Network Sniffing (T1040) ดักจับและทำความเข้าใจโครงสร้างเครือข่ายภายในของ E-corp

Phase 4: Lateral Movement & Exfiltration (การเคลื่อนตัวและการขโมยข้อมูล)
Lateral Movement: APT28 กระโดดไปยังเครื่องเซิร์ฟเวอร์อื่นๆ ในเครือข่ายผ่านช่องโหว่หรือการใช้เครื่องมือ Remote Services โดยพุ่งเป้าไปที่ SMB/Windows Admin Shares (T1021.002)

Target Repository: เป้าหมายหลักในการขโมยทรัพย์สินทางปัญญา (Intellectual Property) ของ E-corp คือระบบศูนย์กลางเอกสารอย่าง SharePoint (T1213.002)

Command and Control (C2) / Exfiltration: ในขั้นตอนสุดท้าย เพื่อส่งข้อมูลที่ขโมยมาออกไปสู่เซิร์ฟเวอร์ C2 ภายนอกโดยไม่ให้ Firewall จับผิดได้ พวกเขาจะใช้เทคนิคพรางตัวผ่าน External Proxy (T1090.002) หรือ Multi-hop Proxy (T1090.003)

💡 Blue Team Action Items (ข้อเสนอแนะสำหรับการป้องกัน)
จาก TTPs ที่วิเคราะห์ได้ ทีม SOC ควรดำเนินการตามขั้นตอนต่อไปนี้:

Email Security: อัปเดตกฎ Anti-Spam และระบบตรวจสอบ URL ในอีเมลเพื่อบล็อก Spearphishing Link

Endpoint Detection (EDR): * เฝ้าระวัง Process ของ Rundll32.exe ที่มีการเรียกใช้งานสคริปต์ที่น่าสงสัย

แจ้งเตือนเมื่อมีการแก้ไข Registry Run Keys หรือไฟล์ใน Startup Folder โดย Command Shell หรือ PowerShell

Network Security: * ตรวจสอบและจำกัดการเข้าถึง SMB ระหว่างเครื่อง Client ด้วยกัน

ตรวจสอบทราฟฟิกขาออก (Egress) ที่เชื่อมต่อไปยัง Proxy ที่ไม่รู้จัก หรือพฤติกรรม Network Sniffing ภายในเครือข่าย