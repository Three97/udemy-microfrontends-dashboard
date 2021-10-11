# Microfrontends with React: A Complete Developer's Guide

## Build incredibly scalable apps with a microfrontend architecture

> by Stephen Grider [on Udemy](https://www.udemy.com/course/microfrontend-course/).

## Running locally

There are four projects in this repository:
| App | Description | Language | local dev |
|-----|-------------|----------|-----------|
| container | Orchestrates the overall application | React | http://localhost:8080 |
| marketing | Subapplication handling pricing and landing page | React |http://localhost:8081 |
| auth | VERY simple auth app for signing in | React | http://localhost:8082 |
| dashboard | Orchestrates the overall application | Vue | http://localhost:8083 |

You can run each subapplication in isolation (though there appears to be an error with the dashboards app when running locally) by navigating to the associated folder in a terminal window and `npm run start`. 

This seems to work well with a multi-tabbed terminal like [iTerm](https://iterm2.com/) for Mac. You can create 4 tabs, 1 for each directory. Visual Studio Code, of course, has this same functionality if you prefer to work in that IDE.

> **NOTE** First time runs will require `npm install` to get all the dependencies and whatnot.

## Hosted in AWS

Secrets configured in GitHub and are used in the deployment scripts under the `.github/workflows` folder.

| Secret | Explanation of value |
|--------|----------------------|
| PRODUCTION_DOMAIN | used for specifying URL for where subapps are hosted |
| AWS_S3_BUCKET_NAME | the S3 bucket name assigned to you - where the bits are bucketed |
| AWS_ACCESS_KEY_ID | value used for accessing AWS artifacts |
| AWS_SECRET_ACCESS_KEY | value used for accessing AWS artifacts |
| AWS_DISTRIBUTION_ID | CloudFront™ distribution ID |

For this project, it is hosted here https://d107z2cii32a58.cloudfront.net

## Corrections

* add a region to the aws cli commands in each of the `.yml` files in order for them to work properly.
* add a prefix `/` to `devServer.historyApiFallback.index` property for `devConfig` in each of the applications (container, marketing, auth, dashboard). This was particularly important for the auth project as it would not work without it. The other subapps didn't seem to matter if it was there or not, so I added it to all of them.
* there are console errors when running the dashboard project in development mode. The error is related to `chart.js/auto` but when deployed to S3, it seems to work fine. I suspect it has something to do with what npm packages have been installed globally on my development machine.

## Final Thoughts

This was a great course and I'm glad I stuck with it all the way to the end. Stephen Grider explains these somewhat complex concepts in an easy-to-understand way. 
