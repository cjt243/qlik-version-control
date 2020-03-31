# qlik-version-control

### Simple example implementing version control for Qlik Sense load scripts
**Currently this does not version the front end / visuals of an application - only the load script*

## Features

- Folder structure that allows multiple environments (QSEoW, QCS, etc)
- Two branches (master and test) - the master branch is used for production apps, and the test is used for development
- Whenever a commit is pushed or a PR is merged, the respective branch will sync to an S3 bucket (test or prod based on the branch) - *uses a GitHub Action: [jakejarvis s3-sync action](https://github.com/jakejarvis/s3-sync-action)*
- Qlik Sense Cloud uses the Amazon S3 connector to access the file, and use the load script by leveraging a `Must_Include` statement


## GitHub Project Structure - what gets synced to my S3 Bucket

    | qlik_environments
    |----   ctripp-qsb (represents my Qlik Sense Business tenant)
    |--------   Market Segmentation (folder represents an app)
    |------------   LoadScript (folder containing components of the load script)
    |----------------   market_segmentation.qvs (load script file)
    |------------   metadata.qvs (generates metadata and changelog)