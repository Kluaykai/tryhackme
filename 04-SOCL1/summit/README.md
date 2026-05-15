📝 Walkthrough & Detection Steps (Sample 1 - 6)
Level 1: Hash Values (Trivial - ง่ายสุด)
Behavior: มัลแวร์ตัวแรกถูกส่งเข้ามา โค้ดตรงไปตรงมา

Detection/Log: ได้ค่า Hash (MD5/SHA256) จากหน้า Malware Sandbox

Action (Remediation): นำค่า Hash ไปใส่ใน Blocklist (Manage Hashes)

Attacker Impact: แฮกเกอร์เปลี่ยนโค้ดแค่ 1 บิต ค่า Hash ก็เปลี่ยนแล้ว (หลบง่ายมาก)

Level 2: IP Addresses (Easy - ง่าย)
Behavior: แฮกเกอร์เปลี่ยนโค้ดเพื่อเปลี่ยน Hash มัลแวร์พยายามเชื่อมต่อกลับไปหา C2 Server

Detection/Log: พบ "Unusual IP address" ขาออกจาก Network Logs

Action (Remediation): สร้าง Firewall Rule ทิศทาง Egress (ขาออก) โดยตั้งค่า Source เป็น Any, Destination เป็น IP เป้าหมาย และ Action เป็น Deny

Attacker Impact: แฮกเกอร์หลบได้โดยการเปลี่ยนไปใช้ IP/Server เครื่องอื่น

Level 3: Domain Names (Simple - ธรรมดา)
Behavior: แฮกเกอร์ซ่อน IP ปลายทางไว้หลังชื่อเว็บ (Domain Name)

Detection/Log: ตรวจพบ DNS Request ไปยังโดเมนที่น่าสงสัยในหมวด Network Activity

Action (Remediation): นำชื่อโดเมนไปใส่บล็อกใน DNS Filter / DNS Rule Manager

Attacker Impact: แฮกเกอร์ต้องเสียเงินและเวลาไปจดทะเบียน Domain Name ใหม่

Level 4: Host Artifacts (Annoying - น่ารำคาญ)
Behavior: แฮกเกอร์เริ่มโจมตีที่ตัวเครื่อง โดยพยายามเข้าไปแก้ไขค่าใน Windows Registry เพื่อปิดการทำงานของ Windows Defender

Detection/Log: พบกิจกรรมจาก Sysmon แจ้งเตือนการแก้ไข Registry Key (DisableRealtimeMonitoring = 1)

Action (Remediation): สร้างกฎตรวจจับด้วย Sigma Rule

Target: Registry Modification

Condition: ระบุ Path และ Value ของ Registry ที่ถูกแก้

MITRE ATT&CK: Defense Evasion (TA0005)

Attacker Impact: แฮกเกอร์ต้องกลับไปรื้อโค้ดมัลแวร์เพื่อหาวิธีปิด Antivirus แบบใหม่

Level 5: Network Artifacts (Challenging - ท้าทาย)
Behavior: มัลแวร์พยายามส่งสัญญาณชีพจร (Network Beaconing) กลับไปหาแฮกเกอร์เพื่อรอรับคำสั่งอย่างต่อเนื่อง

Detection/Log: ตรวจพบการส่งข้อมูล HTTP Request (POST) ด้วยขนาดข้อมูล (Size) และความถี่ (Frequency) ที่ซ้ำๆ กันอย่างเป็นแพทเทิร์น

Action (Remediation): สร้าง Sigma Rule ตรวจจับแพทเทิร์นเครือข่าย

Target: Network Connections

Condition: กำหนด Destination IP/Port เป็น Any (ไม่สนว่าส่งไปไหน) แต่โฟกัสที่การดักจับ Size และ Frequency ที่เจาะจง

MITRE ATT&CK: Command and Control (TA0011)

Attacker Impact: แฮกเกอร์เริ่มปวดหัว เพราะถึงจะเปลี่ยน IP/Domain หนีไปเรื่อยๆ แต่ถ้ารูปแบบการส่งข้อมูลยังเหมือนเดิมก็จะถูกจับได้อยู่ดี

Level 6: TTPs - Tactics, Techniques, Procedures (Tough - ยากมาก)
Behavior: การขโมยข้อมูลต้องมีการนำไฟล์มารวมกันไว้ก่อน (Data Staging) มัลแวร์พยายามใช้ cmd.exe สร้างไฟล์ Log ชั่วคราวเตรียมส่งออก

Detection/Log: ตรวจพบ File Activity ในการสร้างไฟล์ %temp%\exfiltr8.log

Action (Remediation): สร้าง Sigma Rule เพื่อดักจับ "พฤติกรรมหรือขั้นตอนการทำงาน"

Target: File Creation

Condition: ดักจับการสร้างไฟล์ใน Path %temp% ที่มีชื่อไฟล์ระบุเจาะจง

MITRE ATT&CK: Exfiltration (TA0010)

Attacker Impact: แฮกเกอร์ไปต่อไม่ได้แล้ว เพราะนี่คือการบล็อกที่ "วิธีคิดและขั้นตอนการลงมือ" การจะหาเทคนิคขโมยข้อมูลแบบใหม่โดยไม่สร้างไฟล์เลยนั้นทำได้ยากมากถึงมากที่สุด

🔑 Key Takeaways สำหรับงาน SOC Analyst
การบล็อกระดับล่างของพีระมิด (Hash, IP, Domain) มักถูกจัดการอัตโนมัติด้วยระบบเครื่องมือพื้นฐาน

คุณค่าของ SOC Analyst อยู่ที่การวิเคราะห์ Log จาก SIEM / Sysmon เพื่อสร้าง Rule ดักจับพฤติกรรมในระดับ Artifacts และ TTPs

ต้องแยกให้ออกระหว่าง Benign (การทำงานปกติของระบบ) และ Malicious (พฤติกรรมอันตราย) จากข้อมูลที่มีสัญญาณรบกวน (Noise) จำนวนมาก

การสร้าง Detection Rule ที่ดี ควร Map เข้ากับ MITRE ATT&CK Framework เสมอ เพื่อให้รู้ถึงเป้าหมายที่แท้จริงของแฮกเกอร์