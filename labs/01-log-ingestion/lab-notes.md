# Lab 01: Log Ingestion with Splunk

This lab covers the foundational step in any SIEM: ingesting log data from various sources and organizing it into indexes. The lab uses Splunk Enterprise to simulate real-world ingestion, indexing, and data exploration.

## 🧠 Objectives

- Create custom indexes for different log types
- Upload sample log datasets into Splunk
- Analyze index sizes, event counts, and average event characteristics
- Understand how Splunk organizes data internally

## 📦 Datasets Used

| Filename            | Index Name     | Description                            |
|---------------------|----------------|----------------------------------------|
| buttercupgames.zip  | buttercupgames | Demo data from Splunk tutorial         |
| a.zip               | threatglass    | Bro logs from Threatglass (Part A)     |
| mutillidae.zip      | mutillidae     | /var/log data from Mutillidae server   |
| maccdc2012.log      | maccdc         | Snort Fast Alerts from MACCDC 2012     |

## 🔧 Steps Taken

### 1. Viewed Splunk Directory
- Navigated to `/opt/splunk/var/lib/splunk/` to examine existing indexes.
- Used `sudo su -` then `du -hs /opt/splunk/var/lib/splunk/*` to view current index sizes.

### 2. Created Custom Indexes
Created the following via the Splunk Web UI:
- `buttercupgames`
- `threatglass`
- `mutillidae`
- `maccdc`

### 3. Uploaded Log Files via Web Interface
Used `Settings > Add Data > Upload` to ingest each dataset, setting:
- **Source Type**: Automatic
- **Host Settings**: Segment in path (Segment number: 1)
- **Index**: Selected the appropriate custom index

### 4. Verified Ingestion
- Used `Search & Reporting > index=your_index_name` to confirm data.
- Verified event count, sizes, and time range.

## 📊 Observations (example – fill in with your real data)

| Index         | Event Count | Index Size | Avg. Event Size | Compressed File Size | Lines per Event |
|---------------|-------------|------------|------------------|-----------------------|------------------|
| buttercupgames| 4,231       | 40 MB      | 9 KB             | 12 MB                 | ~6               |
| threatglass   | 8,000       | 78 MB      | 10 KB            | 20 MB                 | ~10              |

## 🧠 Reflections

- The `threatglass` dataset took longer to upload due to its size and format.
- Segmenting by path is essential for proper host assignment.
- Splunk compresses ingested data, which affects storage and indexing speed.
- System indexes like `_internal` grow over time — important for performance planning.

## 🖼️ Screenshots

Place screenshots in the `screenshots/` folder and embed like:

```markdown
![Custom Indexes](./screenshots/index-creation.png)
