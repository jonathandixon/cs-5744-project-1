---
id: file-storage-design
title: File Storage Design
sidebar_label: File Storage Design
---

Medical records may come in a variety of formats, including various document types and images. It will not always be useful or performant to extract and structure the information contained in those records. This is where the document storage component comes in. The purpose of the document storage component is to securely and persistently store any files a user uploads to the system.

The file storage component occupies the lowest tier of our architecture. This is important, because it means the document store will only be accessible internally from the REST API. Amazon S3 is an easy choice for the file storage component. This product is affordable, well supported, mature, and easy to configure. Each file uploaded the system can be dumped to an S3 bucket and related to an entity within the database component. S3 provides the necessary security controls to ensure the data is only accessed by our REST API.

<figure>
  <img src="assets/file-storage.png" alt="Diagram of relational DB and S3 bucket."/>
  <figcaption>File S3 location is stored in database along with file metadata.</figcaption>
</figure>

Amazon S3 for the file storage component helps to satify the non-functional requirements, <abbr title="Appropriate measures should be taken to ensure data servers are secured.">NR-7</abbr>, <abbr title="Data backups should be created daily (minimum).">NR-8</abbr>, and <abbr title="Data backups should be securely stored separately NRom data servers.">NR-9</abbr>.
