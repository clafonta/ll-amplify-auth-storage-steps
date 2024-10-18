### Troubleshooting


**Issue:** 
I have a NextJS app, using Amplify auth. 
When I try to create an account with the aws-amplify component, 
I'm told ```Auth UserPool not configured.``` 

**What's The fix?!** I have no idea. I've spent a ton of hours to try to 
figure this out, matching configs with all things in AWS 
environments, all things perfectly configured, with no 
success. I wish there were more debug tools. 

**The workaround:** Start from scratch. Follow this tutorial from 
the start and only _after_ you get Authentication working with 
AWS Cognito, then layer in your application code. Yes, painful. 
