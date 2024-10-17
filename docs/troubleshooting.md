### Troubleshooting


**Issue:** 
I have a NextJS app, using Amplify auth. 
When I try to create an account with the aws-amplify component, 
I'm told ```Auth UserPool not configured.``` 

FIX: try ```amplify update auth``` and make sure a user pool is setup . 