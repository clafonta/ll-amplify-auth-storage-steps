### Use Amplify to setup an API backend and resources.

This will demonstrate how to manage data in DynamoDB and manage the data via AWS AppSync for GraphQL.

#### Add API via Amplify CLI

Run the following from the root of your project

```bash
amplify add api
```

Make the following selections. 
```
? Select from one of the below mentioned services: GraphQL
? Here is the GraphQL API that we will create. Select a setting to edit or continue Authorization modes: API key (default, expiration time: 7 days from now)

>>> IMPORTANT! Change Authorization modes from ```API key``` to ```Amazon Cognito User Pool``` <<<<

? Choose the default authorization type for the API Amazon Cognito User Pool
Use a Cognito user pool configured as a part of this project.
? Configure additional auth types? No
? Here is the GraphQL API that we will create. Select a setting to edit or continue Continue
? Choose a schema template: Blank Schema
✅ GraphQL schema compiled successfully.
```

Let's add a Schema _before_ getting amplify to push our updates. We'll place the file within the Amplify directory within the project.  

```graphql
# amplify/backend/api/<project name>/schema.graphql
# This "input" configures a global authorization rule to enable public access to
# all models in this schema. Learn more about authorization rules here: https://docs.amplify.aws/cli/graphql/authorization-rules
input AMPLIFY { globalAuthRule: AuthRule = { allow: public } } # FOR TESTING ONLY!

type Company @model @auth(rules: [{allow: public}]) {
    id: ID!
    name: String!
    description: String
    industry: String
    tags: [String]
    projects: [Project] @hasMany
    employees: [Employee] @hasMany
    createdAt: AWSDateTime!
    updatedAt: AWSDateTime!
}

type Project @model @auth(rules: [{allow: public}]) {
    id: ID!
    name: String!
    description: String
    status: ProjectStatus!
    startDate: AWSDate
    endDate: AWSDate
    tags: [String]
    companyID: ID! @index(name: "byCompany")
    company: Company! @belongsTo(fields: ["companyID"])
    employees: [Employee] @manyToMany(relationName: "ProjectEmployee")
    attachments: [Attachment] @hasMany
    createdAt: AWSDateTime!
    updatedAt: AWSDateTime!
}

enum ProjectStatus {
    PLANNING
    IN_PROGRESS
    COMPLETED
    ON_HOLD
    CANCELLED
}

type Employee @model @auth(rules: [{allow: public}]) {
    id: ID!
    name: String!
    email: String! @index(name: "byEmail")
    position: String
    department: String
    hireDate: AWSDate
    tags: [String]
    companyID: ID! @index(name: "byCompany")
    company: Company! @belongsTo(fields: ["companyID"])
    projects: [Project] @manyToMany(relationName: "ProjectEmployee")
    uploadedAttachments: [Attachment] @hasMany
    createdAt: AWSDateTime!
    updatedAt: AWSDateTime!
}

type Attachment @model @auth(rules: [{allow: public}]) {
    id: ID!
    name: String!
    description: String
    type: AttachmentType!
    tags: [String]
    file: S3Object!
    projectID: ID! @index(name: "byProject")
    project: Project! @belongsTo(fields: ["projectID"])
    uploadedBy: ID! @index(name: "byUploader")
    uploader: Employee! @belongsTo(fields: ["uploadedBy"])
    createdAt: AWSDateTime!
    updatedAt: AWSDateTime!
}

enum AttachmentType {
    DOCUMENT
    IMAGE
    VIDEO
    OTHER
}

type S3Object {
    bucket: String!
    region: String!
    key: String!
    contentType: String
    size: Int
}

```


Then run the following to get Amplify to provision the needed backend resources in AWS. 
```bash
amplify push
```

You'll be asked a few questions. Here are some of the answers: 

```bash
? Do you want to generate code for your newly created GraphQL API"" Yes
? Choose the code generation language target: typescript
? Enter the file name pattern of graphql queries, mutations and subscriptions"" src/graphql/**/*.ts
? Do you want to generate/update all possible GraphQL operations - queries, mutations and subscriptions: Yes
? Enter maximum statement depth [increase from default if your schema is deeply nested]: 2
? Enter the file name for the generated code: src/API.ts
```

Now, we should be ready leverage our API. 


Let's [create a page to leverage the API.](../docs/07-add-company-crud.md)

