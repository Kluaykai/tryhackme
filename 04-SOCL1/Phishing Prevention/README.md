🎯 Objective
ศึกษาและทำความเข้าใจเกี่ยวกับกลไกการตรวจสอบความถูกต้องของอีเมล (Email Authentication) วิเคราะห์ทราฟฟิกเครือข่ายโปรโตคอล SMTP/IMF ผ่านโปรแกรม Wireshark เพื่อตรวจจับภัยคุกคาม และเรียนรู้เทคนิคการป้องกันการโจมตีประเภท Phishing ในระดับองค์กร

🔑 Core Concepts & Authentication Rules
ในการเฝ้าระวังความปลอดภัยของอีเมล ระบบจะใช้กฎ 3 ข้อหลักทำงานร่วมกันเพื่อพิสูจน์ตัวตนและป้องกันการปลอมแปลงโดเมน (Email Spoofing):

SPF (Sender Policy Framework): ดึงข้อมูล DNS TXT record ของโดเมนผู้ส่งมาตรวจสอบว่า หมายเลข IP Address ของเซิร์ฟเวอร์ที่ส่งอีเมลมานั้น มีรายชื่ออยู่ในกลุ่มที่ได้รับอนุญาต (Authorized Senders) หรือไม่

DKIM (DomainKeys Identified Mail): การเข้ารหัสลับแบบกุญแจสาธารณะ (Public Key Cryptography) โดยเซิร์ฟเวอร์ต้นทางจะลงลายเซ็นดิจิทัล (Digital Signature) ไว้ใน Header ของอีเมล และเซิร์ฟเวอร์ปลายทางจะใช้ Public Key จาก DNS มาถอดรหัสเพื่อตรวจสอบความถูกต้องของข้อมูล (Data Integrity) และยืนยันตัวตนผู้ส่ง (Non-repudiation)

DMARC (Domain-Based Message Authentication, Reporting, and Conformance): ทำหน้าที่เป็นตัวตัดสินใจขั้นเด็ดขาด โดยนำผลลัพธ์จาก SPF และ DKIM มาพิจารณาร่วมกับนโยบาย (Policy) ที่โดเมนต้นทางกำหนดไว้ ซึ่งมีความเข้มงวด 3 ระดับ:

p=none: ปล่อยผ่าน (Monitor/Log เท่านั้น)

p=quarantine: กักกัน (ส่งเข้ากล่องจดหมายขยะ/Spam)

p=reject: ปฏิเสธการรับ (บล็อกและทิ้งอีเมลฉบับนั้นทันที)

🎛️ S/MIME Protocol (Secure/Multipurpose Internet Mail Extensions)
มาตรฐานการรับส่งอีเมลแบบเข้ารหัสขั้นสูงเพื่อความปลอดภัยแบบ End-to-End:

Digital Signature: ผู้ส่งใช้ Private Key ของตนเองในการเซ็นกำกับ เพื่อทำหน้าที่ยืนยันตัวตน (Authentication) ป้องกันการปฏิเสธความรับผิดชอบ (Non-repudiation) และรักษาความถูกต้องของข้อมูล (Data Integrity)

Encryption: ผู้ส่งใช้ Public Key ของผู้รับในการเข้ารหัสเนื้อหา ทำให้อีเมลฉบับนั้นมีเพียงผู้รับตัวจริงที่มี Private Key คู่กันเท่านั้นที่สามารถเปิดอ่านได้ ช่วยรักษาความลับของข้อมูล (Confidentiality) ได้อย่างมีประสิทธิภาพ

🦈 SMTP Traffic Analysis Workflow (Wireshark)
เทคนิคการใช้ Wireshark แกะรอยและตรวจสอบบันทึกทราฟฟิกเครือข่าย (.pcap) ของโปรโตคอล SMTP และ IMF (Internet Message Format):

Useful Filters:

smtp: กรองเฉพาะแพ็กเก็ตที่เป็นโปรโตคอล SMTP ทั้งหมด

smtp.response.code: กรองเฉพาะรหัสสถานะการตอบกลับจากเซิร์ฟเวอร์ปลายทาง

imf: กรองโครงสร้างเนื้อหาภายในอีเมล (Internet Message Format) เช่น ข้อมูลผู้รับ/ผู้ส่งที่แท้จริง และไฟล์แนบ

Key SMTP Status Codes:

220: Service ready (เซิร์ฟเวอร์พร้อมให้บริการ)

552: Requested mail action aborted (ส่งไม่สำเร็จเนื่องจากขนาดเกิน หรือตรวจพบปัญหาด้านความปลอดภัย/Malware)

553: Requested action not taken (ส่งไม่สำเร็จเนื่องจากกล่องจดหมายปลายทางไม่อนุญาต หรือโดเมนถูกบล็อกโดยบัญชีดำ เช่น Spamhaus)

Incident Investigation Tricks:

การค้นหาพฤติกรรมต้องสงสัยโดยใช้ฟังก์ชัน Find Packet (Ctrl + F) เปลี่ยนโหมดเป็น String และค้นหาใน Packet Details เพื่อหา Keyword สำคัญ เช่น ชื่อโดเมนอันตราย

การตรวจสอบโครงสร้าง MIME Multipart Media Encapsulation เพื่อหาชื่อไฟล์แนบอันตราย (เช่น document.zip หรือ attachment.scr) รวมถึงตรวจสอบฟิล์ด Content-Transfer-Encoding เพื่อดูรูปแบบการเข้ารหัสไฟล์ (เช่น base64)

🛡️ Enterprise Technical Defenses
ระบบควบคุมความปลอดภัยสมัยใหม่ที่องค์กรนำมาใช้รับมือกับภัยคุกคามทางอีเมล:

Secure Email Gateways (SEGs): ด่านแรกในการสแกนอีเมลเพื่อตรวจจับการพยายามแอบอ้าง พลางตัว หรือปลอมแปลงชื่อผู้ส่ง

Sandboxing: สภาพแวดล้อมเสมือนจริงที่ถูกแยกส่วนออกไปอย่างปลอดภัย ใช้สำหรับรันไฟล์แนบหรือลิงก์ต้องสงสัย เพื่อเฝ้าดูพฤติกรรมและแนวโน้มการทำงานที่เป็นอันตราย (Malicious Behavior) โดยไม่สร้างความเสี่ยงให้แก่ระบบงานจริง

Link Rewriting: เปลี่ยน URL ต้องสงสัยให้วิ่งผ่านระบบตรวจสอบขององค์กรก่อน เพื่อสแกนความปลอดภัยแบบ Real-time ก่อนอนุญาตให้ผู้ใช้งานเข้าถึงเว็บปลายทาง