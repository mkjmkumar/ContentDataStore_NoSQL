# ContentDataStore_NoSQL
Content Data Store (CDS) as document store replacement

1.	Definition of Content Data Store (CDS).
 “CDS provide storage facilities to massive datasets where data is in the form of text, images, pdfs and scanned documents. This massive dataset organized, manipulated, processed and managed by CDS along with storage facilities”

“CDS is a Fast Data Ingestion and Fast Lookup system”

2.	CDS Components.
This POC contains four main components of CDS system – Ingestion system, Agent, Image Store and UI. The typical communication between the components is as follows.

a.	Ingestion System: Custom Java Web interface (DiP – for future) to load data in batch. 
b.	Agent: Agent is Tesseract OCR, text extract facility and a scheduled program. Agent processes the images, pdfs and scanned documents to extract content and store them in Hbase. Load structured data into Hive for aggregations, and Images file will be stored in candidate database, if size is more than 10 MB it will be stored in HDFS and metadata will be stored in Hbase. If image size is less than 10 MB it will stored directly into HBase MOB data type column.
c.	Image Store: Hbase and HDFS, data flow as per above point b.
d.	Reporting and Downstream: - We have downstream and reporting system where we sent summarize aggregated data files to external system (downstream). Reporting system where users are directly connected and can retrieve image based on data fetched on application system.
