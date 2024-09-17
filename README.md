# Google Cloud Storage Management with gcloud CLI

A comprehensive repository for managing Google Cloud Storage using the `gcloud` CLI. This repository contains a detailed Markdown file documenting various commands and operations for interacting with Google Cloud Storage, including:

## Basic Operations
- Commands for listing, creating, and deleting buckets and objects.

## File Management
- Copying, moving, downloading, and uploading files.

## Bucket and Object Configuration
- Setting ACLs, metadata, encryption, and lifecycle policies.

## Advanced Features
- Handling CORS configurations, retention policies, and generating signed URLs.

## Storage Classes
- A comparison of different storage classes like `STANDARD` and `NEARLINE` to guide appropriate usage based on access frequency and cost.

## Overview
This document provides a comprehensive list of `gcloud` CLI commands for Google Cloud Storage. It covers basic and advanced operations, configuration settings, and comparisons of storage classes.

## Table of Contents
1. [Setup and Authentication](#setup-and-authentication)
2. [List Buckets](#1-list-buckets)
3. [Create a Bucket](#2-create-a-bucket)
4. [Delete a Bucket](#3-delete-a-bucket)
5. [Upload a File](#4-upload-a-file)
6. [Download a File](#5-download-a-file)
7. [Copy a File](#6-copy-a-file)
8. [Move a File](#7-move-a-file)
9. [Delete a File](#8-delete-a-file)
10. [List Objects in a Bucket](#9-list-objects-in-a-bucket)
11. [Describe a Bucket](#10-describe-a-bucket)
12. [Describe an Object](#11-describe-an-object)
13. [Search and Filter](#12-search-and-filter)
14. [Update Object Metadata](#13-update-object-metadata)
15. [Apply Object Retention Policy](#14-apply-object-retention-policy)
16. [Set Bucket Website Configuration](#15-set-bucket-website-configuration)
17. [Remove Bucket Website Configuration](#16-remove-bucket-website-configuration)
18. [Set Bucket Labels](#17-set-bucket-labels)
19. [Get Bucket Labels](#18-get-bucket-labels)
20. [Change Object Storage Class](#19-change-object-storage-class)
21. [Enable Bucket Versioning](#20-enable-bucket-versioning)
22. [Disable Bucket Versioning](#21-disable-bucket-versioning)





# Setup and Authentication.
Before using these commands, ensure you have authenticated and set up the gcloud CLI:
```bash
gcloud auth login
gcloud config set project YOUR_PROJECT_ID
```

# 1. List Buckets
To list all buckets in your project:
```bash
gcloud storage buckets list
```

# 2. Create a Bucket
To create a new bucket:
```bash
gcloud storage buckets create gs://YOUR_BUCKET_NAME
```

# 3. Delete a Bucket
To delete a bucket (bucket must be empty):
```bash
gcloud storage buckets delete gs://YOUR_BUCKET_NAME
```

# 4. Upload a File
To upload a file to a bucket:
```bash
gcloud storage cp LOCAL_FILE_PATH gs://YOUR_BUCKET_NAME/
```

# 5. Download a File
To download a file from a bucket:
```bash
gcloud storage cp gs://YOUR_BUCKET_NAME/REMOTE_FILE_PATH LOCAL_FILE_PATH
```

# 6. Copy a File
To copy a file within a bucket or between buckets:
```bash
gcloud storage cp gs://SOURCE_BUCKET/FILE_PATH gs://DESTINATION_BUCKET/FILE_PATH
```

# 7. Move a File
To move (copy and delete) a file within a bucket or between buckets:
```bash
gcloud storage mv gs://SOURCE_BUCKET/FILE_PATH gs://DESTINATION_BUCKET/FILE_PATH
```

# 8. Delete a File
To delete a file from a bucket:
```bash
gcloud storage rm gs://YOUR_BUCKET_NAME/FILE_PATH
```

# 9. List Objects in a Bucket
To list all objects in a bucket:
```bash
gcloud storage objects list --bucket=YOUR_BUCKET_NAME
```

# 10. Describe a Bucket
To get detailed information about a bucket:
```bash
gcloud storage buckets describe gs://YOUR_BUCKET_NAME
```

# 11. Describe an Object
To get detailed information about an object:
```bash
gcloud storage objects describe gs://YOUR_BUCKET_NAME/FILE_PATH
```

# 12. Search and Filter
```bash
gcloud storage objects list --bucket=YOUR_BUCKET_NAME --prefix=YOUR_PREFIX
```

# 13. Update Object Metadata
To update metadata of an object:
```bash
gcloud storage objects update gs://YOUR_BUCKET_NAME/FILE_PATH --metadata=key=value
```

# 14. Apply Object Retention Policy
To set a retention policy on an individual object:
```bash
gcloud storage objects update gs://YOUR_BUCKET_NAME/FILE_PATH --retention-policy=retention_period=3600s
```

# 15. Set Bucket Website Configuration
To set up a bucket for website hosting:
```bash
gcloud storage buckets update gs://YOUR_BUCKET_NAME --website-main=index.html --website-notFound=error.html
```

# 16. Remove Bucket Website Configuration
To remove website hosting configuration from a bucket:
```bash
gcloud storage buckets update gs://YOUR_BUCKET_NAME --no-website
```

# 17. Set Bucket Labels
To add or update labels on a bucket:
```bash
gcloud storage buckets update gs://YOUR_BUCKET_NAME --labels=key1=value1,key2=value2
```

# 18. Get Bucket Labels
To retrieve the labels assigned to a bucket:
```bash
gcloud storage buckets describe gs://YOUR_BUCKET_NAME --format='value(labels)'
```

# 19. Change Object Storage Class
To change the storage class of an object (e.g., from STANDARD to NEARLINE):
```bash
gcloud storage objects update gs://YOUR_BUCKET_NAME/FILE_PATH --storage-class=NEARLINE
```

# 20. Enable Bucket Versioning
```bash
gcloud storage buckets update gs://YOUR_BUCKET_NAME --versioning
```

# 21. Disable Bucket Versioning
To disable versioning on a bucket:
```bash
gcloud storage buckets update gs://YOUR_BUCKET_NAME --no-versioning
```
