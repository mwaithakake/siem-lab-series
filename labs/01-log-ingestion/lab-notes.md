🧪 Lab 01: Log Ingestion with Splunk

Part of the "Building My Own SIEM" GitHub Series

This lab covers the foundational step in any SIEM: ingesting log data from various sources and organizing it into indexes. The lab uses Splunk Enterprise to simulate real-world ingestion, indexing, and data exploration.

🧠 Objectives

✅ Create custom indexes for different log types

✅ Upload sample log datasets into Splunk

✅ Analyze index sizes, event counts, and average event characteristics

✅ Understand how Splunk organizes data internally and how to manage permissions


## 📦 Datasets Used

| Filename              | Index Name     | Description                              |
|-----------------------|----------------|------------------------------------------|
| `buttercupgames.zip`  | buttercupgames | Demo data from Splunk tutorial           |
| `a.zip`               | threatglass    | Bro logs from Threatglass (Part A)       |
| `mutillidae.zip`      | mutillidae     | /var/log data from Mutillidae server     |
| `maccdc2012.log`      | maccdc         | Snort Fast Alerts from MACCDC 2012       |




🔧 Steps Taken
1. 🗂️ Viewed Splunk Data Directory
    Navigated to /opt/splunk/var/lib/splunk/
    Used sudo su - and:
    du -hs /opt/splunk/var/lib/splunk/*
    Observed index sizes, access permissions, and how Splunk stores indexed data.

📸 Screenshot:
![Screenshot from 2025-07-01 15-20-40](https://github.com/user-attachments/assets/7e7fb570-87d8-40f7-9dc6-e983847c38df)



2. 📁 Created Custom Indexes
   
Used Splunk Web UI: Settings > Indexes > New Index

Created the following indexes:

buttercupgames

threatglass

mutillidae

maccdc

📸 Screenshot:
![Screenshot from 2025-07-01 14-53-59](https://github.com/user-attachments/assets/a31c1ef4-893f-47cc-b058-549335e9ef23)



3. 📄 Uploaded Log Files via Web Interface
   
Used: Settings > Add Data > Upload

Ingestion settings:

   Source Type: Automatic
   
   Host Settings: Segment in path, Segment number: 1
   
   Index: selected corresponding custom index


💡 Notes:
.zip files like buttercupgames.zip had to be unzipped, and contents uploaded individually using
Monitor > Files & Directories

Some files could not be previewed but were still indexed properly



4. 🔍 Verified Ingestion
   
Opened Search & Reporting and ran:

index=buttercupgames

index=threatglass

index=mutillidae

index=maccdc

Adjusted time picker to All Time since data was dated months or years back

📸 Screenshot:
![Search Results](https://github.com/user-attachments/assets/a8753350-45d8-4572-ab95-5dd2a01d66f6)


📊 Observations

| Index          | Event Count | Index Size | Avg. Event Size | Compressed File Size | Lines/Event |
|----------------|-------------|------------|------------------|-----------------------|-------------|
| buttercupgames | 0           | 1 MB       | N/A              | N/A                   | N/A         |
| threatglass    | 936K        | 198 MB     | ~10 KB           | ~20 MB                | ~10         |
| mutillidae     | 226K        | 19 MB      | ~9 KB            | ~12 MB                | ~6          |
| maccdc         | 39.1K       | 4 MB       | ~8 KB            | ~10 MB                | ~5          |


🔹 How to Calculate:

Avg. event size = Index size / Event count

Lines per event = Search logs, count line patterns



🧠 Reflections & Lessons Learned

😌 threatglass dataset took longer due to size and file format

🧱 Segmenting by path helps with assigning host field

🕒 Old logs require changing Splunk time picker to "All Time"

📦 Splunk compresses data after ingestion

🔐 Linux permissions required understanding sudo, su -, and ownership issues


📍 Next Steps

In the next lab, I’ll begin correlating data and building dashboards, alerts, and reports from the logs ingested here.


🔗 Related Repos

This lab is part of the "Building My Own SIEM" GitHub series.

https://github.com/mwaithakake/siem-lab-series




