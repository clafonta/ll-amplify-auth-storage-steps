# ll-amplify-auth-storage-steps
A guideline to build a NextJS app with [Amplify](https://docs.amplify.aws/). 

* We'll use the Amplify CLI to procure AWS backend resources.
* We'll not use Amplify Studio
* You need an AWS Account. 
* You need to create an AWS Profile in your local dev environment.  

## Table of Contents

* [01 - Create your Nextjs app.](docs/01-create-your-next-app-add-amplify.md)
* [02 - Create a Dashboard page.](docs/02-add-a-dashboard-page-and-layout.md)
* [03 - Add authentication-required to the Dashboard layout.](docs/03-add-required-auth-to-the-dashboard.md)
* [04 - Add the ability to upload files to S3.](docs/04-add-upload-files-to-storage.md)
* [05 - Add a the ability to view files in a gallery.](docs/05-add-image-gallery.md)
* [06 - Add an API and GraphQL capabilities.](docs/06-add-data-and-graphql.md)
* [07 - Create a page to leverage the API.](docs/07-add-company-crud.md)

## Introduction

For detailed information on each topic, please click the links in the table of contents above.

> [!IMPORTANT]  
> You may notice in this walkthrough the use of bloated HTML instead of using React components. 
> This is on purpose to help avoid the need to import and/or create custom components. 
> In the real world, I would recommend building components which helps reduce code bloat, 
> drives consistency, and helps with your sanity. 
