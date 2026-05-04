# 🔍 Introduction to Splunk (SIEM Basics)

A foundational guide to understanding Splunk, a leading Security Information and Event Management (SIEM) solution used to collect, analyze, and correlate network and machine logs in real-time.

## 📌 Overview (ภาพรวม)
Splunk provides deep visibility into network activities, helping Security Operations Center (SOC) analysts speed up threat detection and incident response by centralizing logs from various sources (Firewalls, Web Servers, Windows Event Logs, etc.).

## 🏗️ Core Components (องค์ประกอบหลัก 3 ส่วน)
Splunk operates using three main components working together:
1.  **Splunk Forwarder:** A lightweight agent installed on endpoints to collect and send data (logs) to the Splunk instance. (หน่วยกวาดล้างและส่งข้อมูล)
2.  **Splunk Indexer:** Parses, normalizes, categorizes, and stores the incoming data as events (field-value pairs), making it searchable. (หน่วยจัดระเบียบและเก็บข้อมูล)
3.  **Splunk Search Head:** The Web UI where analysts use SPL (Search Processing Language) to search indexed logs and create visualizations/dashboards. (หน้าต่างค้นหาและแสดงผล)

## 📥 Data Ingestion Methods (วิธีการนำข้อมูลเข้า)
From the "Add Data" panel, data can be ingested via:
*   **Upload:** Manually uploading local files (e.g., CSV, JSON) for one-time analysis.
*   **Monitor:** Continuously collecting data from files and ports on the Splunk instance.
*   **Forward:** Receiving data from external Splunk Forwarders.

## 💻 Practical SPL Commands (คำสั่งค้นหาพื้นฐานที่ใช้ในแล็บ)
During the practical investigation of the `VPN_logs` index, the following SPL (Search Processing Language) queries were utilized:

*   **Search by Index:**
    `index="VPN_Logs"`
    *(ค้นหา Event ทั้งหมดที่อยู่ในกล่องข้อมูล VPN_Logs)*

*   **Filter by Specific Field Value:**
    `index="VPN_Logs" UserName="Maleena"`
    *(ค้นหาประวัติการใช้งาน VPN ของผู้ใช้ที่ชื่อ Maleena)*

*   **Search by IP Address:**
    `index="VPN_Logs" Source_ip="107.14.182.38"`
    *(ค้นหาว่า IP นี้ทำกิจกรรมอะไรบ้าง หรือผูกกับ Username ไหน)*

*   **Exclude Specific Data (The NOT operator):**
    `index="VPN_Logs" NOT Source_Country="France"`
    *(ค้นหาข้อมูลการเชื่อมต่อจากทุกประเทศ **ยกเว้น** ประเทศฝรั่งเศส)*

---
**Compiled by:** Piyangkoon (Frame) Tongrujiroj
**Focus:** SOC Analyst Foundation / SIEM Fundamentals / Log Analysis