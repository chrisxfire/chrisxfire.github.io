---
title: notes > web > msid > shared access signatures
date: 2022-05-11T13:23:24-0600
draft: true
---
Share Access Signatures
A signed URI that points to one or more storage resources.
Includes a token that contains a special set of query parameters.

Types of Shared Access Signatures
- User delegation SAS
  - Secured with AAD credentials and also by permissions specified for the SAS.
  - Applies to Blob storage only.
- Service SAS
  - Secured with the storage account key.
  - Applies to Blob, Queue, and Table Storage, and Azure Files.
- Account SAS
  - Secured with the storage account key
  - Applies to Blob, Queue, and Table Storage.

How SAS's Work
- 2 components needed:
  - URI to the resource in Azure Storage that is being accessed (`host.tld/patient-images/patient-116139-nq8z7f.jpg?`)
  - SAS token that you've created to authorize access (`sp=r&st=2020-01-20T11:42:32Z&se=2020-01-20T19:42:32Z&spr=https&sv=2019-02-02&sr=b&sig=SrW1HZ5Nb6MbRzTbXCaPm%2BJiSEn15tC91Y4umMPwVZs%3D`)

Best Practices
- Always use HTTPS.
- User Delegation SAS is the most secure. Use it whenever possible.
- Set expiration time to the smallest useful value.
- Apply the principle of least-privilege.
- Create a middle-tier servie to manage users and access to storage when risk of using SAS is unacceptable.
