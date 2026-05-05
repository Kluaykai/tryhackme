# 🔍 Introduction to Elastic Stack (ELK) & Kibana

A foundational guide to understanding the Elastic Stack (ELK), a powerful collection of open-source tools used by SOC teams for log management, search, and real-time visualization.

## 🏗️ Core Components (องค์ประกอบหลัก 4 ส่วน)
1. **Beats (Data Shippers):** Lightweight host-based agents installed on endpoints to collect and send specific data (e.g., Winlogbeat for Windows logs, Packetbeat for network traffic). (เอเจนต์เก็บข้อมูลตามเครื่อง)
2. **Logstash (Data Processing Engine):** Collects data from Beats/ports/files, parses, filters, normalizes it, and sends it to Elasticsearch. (ตัวคัดกรองและจัดระเบียบข้อมูล)
3. **Elasticsearch (Search & Analytics Engine):** A database that acts as a full-text search and analytics engine for JSON-formatted documents. (ฐานข้อมูลสำหรับเก็บและค้นหา)
4. **Kibana (Visualization Tool):** The web UI where analysts explore, investigate (using the Discover tab), and visualize data stored in Elasticsearch. (หน้าต่าง UI สำหรับค้นหาและสร้างกราฟ)

## 🛠️ Kibana Discover Tab (เครื่องมือหลักในการสืบสวน)
*   **Index Pattern:** Tells Kibana which Elasticsearch data to explore (e.g., `vpn_connections`).
*   **Time Filter:** Crucial for narrowing down logs to a specific timeframe (e.g., Jan 1 to Jan 31). *Always check this first if logs are missing!*
*   **Fields Pane:** Shows parsed fields from logs. Used to quickly filter values (e.g., finding the top `SourceIP` or `UserName`).

## 💻 KQL (Kibana Query Language) Basics
KQL is the special language used in the search bar to precisely filter ingested logs.

*   **Free Text Search:** Searches the entire document for a specific word.
    *   Example: `security` (Finds any log containing the word security)
*   **Wildcard Search (*):** Matches parts of a word.
    *   Example: `United*` (Finds United States, United Kingdom, etc.)
*   **Field-based Search:** Searches specific fields. Syntax is `Field : Value`.
    *   Example: `UserName : "Johny Brown"`
*   **Logical Operators (AND | OR | NOT):**
    *   **AND:** `Source_Country : "United States" AND UserName : "James"`
    *   **OR:** `UserName : "James" OR UserName : "Albert"`
    *   **NOT:** `Source_Country : "United States" AND NOT (source_state : "New York")`

## 📊 Visualizations & Dashboards
*   **Visualization:** Converting raw logs into charts (pie charts, bar charts, tables) to easily identify trends or correlations (e.g., tracking failed login attempts).
*   **Dashboard:** Combining multiple visualizations and saved searches into a single, comprehensive view for real-time SOC monitoring.

---
**Compiled by:** Piyangkoon (Frame) Tongrujiroj
**Focus:** SOC Analyst Foundation / SIEM Fundamentals / Log Analysis