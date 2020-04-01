# qlik-version-control

### Simple example implementing version control for Qlik Sense load scripts
**Currently this does not version the front end / visuals of an application - only the load script*

## Features

- Folder structure to allow managing script for multiple applications 
- Two branches (master and test) - the master branch is used for production apps, and the test is used for development
- Whenever the code is updated, the respective branch will sync to an S3 bucket (test or prod based on the branch) - *uses a GitHub Action: [jakejarvis s3-sync action](https://github.com/jakejarvis/s3-sync-action)*
- Qlik Sense Cloud uses the Amazon S3 connector to access the file, and use the load script by leveraging a `Must_Include` statement


## GitHub Project Structure - what gets synced to my S3 Bucket

    | qlik_environment
    |----   apps
    |--------   Market Segmentation (folder represents an app)
    |------------   LoadScript (folder containing components of the load script)
    |----------------   market_segmentation.qvs (load script file)
    |------------   metadata.qvs (generates metadata and changelog)
