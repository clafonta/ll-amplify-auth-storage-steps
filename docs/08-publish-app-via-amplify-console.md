### Deploy your app via Amplify console
When connecting Amplify to Github for CI/CD, be sure the Service Role has 
the following permission policy: 

```AdministratorAccess-Amplify``` 

If you review the 'Trust relationships' tab, it should look like: 

```javascript
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "amplify.amazonaws.com"
            },
            "Action": "sts:AssumeRole"
        }
    ]
}
```
