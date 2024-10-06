### Create a new Next.js app. 

First, let's create a new Next.js app using the latest version. 

```shellscript
npx create-next-app@latest my-amplify-app
cd my-amplify-app
```

When prompted, choose the following options:

```
✔ Would you like to use TypeScript?  Yes
✔ Would you like to use ESLint?  Yes
✔ Would you like to use Tailwind CSS?  Yes
✔ Would you like to use `src/` directory?  Yes
✔ Would you like to use App Router? (recommended)  Yes
✔ Would you like to customize the default import alias (@/*)? No
```


### Install Amplify CLI and initialize the project

Now, let's install the Amplify CLI and initialize our project.

```shellscript
npm install -g @aws-amplify/cli
amplify init
```

> [!WARNING]  
> We're going to stick with Gen 1 for setup for ease of use.




Follow the prompts to set up your Amplify project. Choose defaults for most options, but make sure to select "JavaScript" as the programming language.

### Add Amplify Auth

Let's add authentication to our project.

```shellscript
amplify add auth
```

Choose the default configuration for a quick setup, or customize it based on your needs. Here's what I chose: 

> [!TIP]  
> We're going to use `Email` instead of the default `Username`. 

```
Using service: Cognito, provided by: awscloudformation
 
 The current configured provider is Amazon Cognito. 
 
 Do you want to use the default authentication and security configuration? Default configuration
 Warning: you will not be able to edit these selections. 
 How do you want users to be able to sign in? Email
 Do you want to configure advanced settings? No, I am done.
✅ Successfully added auth resource llnextappf628f981 locally

```

### Add Amplify Storage

Now, let's add storage capabilities to our project.

```shellscript
amplify add storage
```

Select "Content" for the storage service, and choose the default options for a quick setup.

```typescript
? Select from one of the below mentioned services: Content (Images, audio, video, etc.)
✔ Provide a friendly name for your resource that will be used to label this category in the project: · s3cd2aa16a
✔ Provide bucket name: · llnextappd0b462876af74e629dbb43b2e568c698
✔ Who should have access: · Auth and guest users
✔ What kind of access do you want for Authenticated users? · create/update, read, delete
✔ What kind of access do you want for Guest users? · read
✔ Do you want to add a Lambda Trigger for your S3 Bucket? (y/N) · no

```


### Push the changes to the cloud

Let's push our local changes to set up the backend resources in AWS.

```shellscript
amplify push
```

This command will provision the necessary resources in your AWS account.

### Install Amplify JavaScript libraries

Now, let's install the required Amplify libraries in our Next.js project. 

```shellscript
npm install aws-amplify @aws-amplify/ui-react
```



That's it! You've now created a Next.js app with the App Router with Amplify Auth and Storage set up.

Next, let's [add a simple Dashboard page to the app.](02-add-a-dashboard-page-and-layout.md)