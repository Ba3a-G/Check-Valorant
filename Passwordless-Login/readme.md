# Password-less Login
Don't want to share password with us? We got you covered. But before moving forward...
## Can we steal your account if you share your password?
Absolutely not! Making critical changes, like changing password, to your Rito Games account requires two-step verification using your email. Basically, Riot Games emails you an OTP. So, no one can steal your account even if you share your password. However, they can login and play with your account.
But you can trust us and we will strive to maintain your trust. Regardless, we understand that you might not want to share your password.
## How to not share your password and still use our tools?
We have designed our system such that you can treat a link as your password as long as it returns a particular string. Let me explain this in plain English. Let's take an example of [this link](https://swl7yooy41.execute-api.us-east-1.amazonaws.com/demo/).
Go ahead and open it in your browser. It returns: `https://playvalorant.com/opt_in#access_token=eyJ...expires_in=3600`.
### But what it is?
Well, it contains something called as _access token_ for your account. Access Tokens can be treated as temporary (see the end of the string, it says `expires_in=3600`) password to access your account programatically only. You can not use your Access Token to login with Riot Client as you normally do with your password.
## How to set up your own Passwordless Login URL?
Don't worry. It's not as difficult as it sounds. Plus, we have prepared a few tutorials. You can also tweet me [@Ba3a_Gamzo](https://twitter.com/Ba3a_Gamzo) for help, or you can follow the easiest method, i.e. enter your password on our website. Below are the few methods that you can employ to create your own URL. This is a one time setup and you don't have to repeat it everytime you want to check your store. You can treat this URL as your password on all of our tools.
### DIY (for devs)
Do it yourself. Just make sure that you are using https and it does not take more than 4 seconds to load. You can use [this](https://github.com/RumbleMike/ValorantClientAPI/blob/master/Docs/RSO_AuthFlow.py) awesome script for reference.
### Amazon Web Services (AWS)
We will use AWS Lambda and AWS API Gateway to create you a serverless function that returns your Access Key on an URL. That way you don't have to share your password with us, it will stay on _your_ AWS account. Let's get building, shall we?
The process is very simple and will take 20 minutes at max, just follow along.
#### Create an AWS account (max 10 minutes)
Go to [this link](https://aws.amazon.com/free/) and create a free AWS acocunt. Just follow along the prompt. They have a very generous free usage policy, you don't have to pay anything.
#### Create a Lambda Function (max 5 minutes)
AWS Lambda is an event-driven compute service. Just know that it responds with something when you do something. In our case, it will respond with your access token when we request an URL.
1. Go to [this URL](https://console.aws.amazon.com/lambda/home?region=us-east-1)
2. Click on Create Function
3. Enter a name in the 'Function Name' field. You can enter anything.
4. Select 'Python 3.9' from the Runtime dropdown
5. Click on 'Create Function' at the bottom of the page
6. This will take you to the function overview page
7. Scroll down a bit and you will see 'Code Source' heading
8. Click on 'Upload From' dropdown on the right side of the page
9. Select 'S3 URL' from the dropdown
10. Enter this URL in the field: https://checkvalorant.s3.amazonaws.com/public/lambda_function.zip
11. Click on 'Save' button
12. Go to 'Configuration' tab
13. Go to 'Environment variables' tab from the left sidebar
14. Click on 'Edit' button
15. Enter 'password' in the key field and enter _your password_ in the value field
16. Repeat the same with 'username' in the key field and _your username_ in value field
17. Click on save button

#### Create an API (max 5 minutes)
AWS API Gateway allows you to access AWS resources through an API. Think of it as the safe gateway to your AWS data. In our case, it will help us communicate with AWS Lambda.
1. Go to [this URL](https://console.aws.amazon.com/apigateway/main/apis?region=us-east-1)
2. Click on 'Create API'
3. Click on 'Build' in the REST API box
4. Enter a name in 'API Name' field
5. Leave everything as default
6. Click on 'Create API' button
7. Click on 'Actions' > 'Create Method'
8. Select 'GET' from the newly generated dropdown
9. Click on the Tick mark next to it
10. Click on the newly generated 'GET' button
11. Select 'Use Lambda Proxy integration'
12. Start typing your Lambda Function name and select it from the list
13. Click on 'Save', then 'OK'
14. Again, click on 'Actions'
15. Click on 'Deploy API'
16. Select 'New Stage' from the dropdown & enter any name
17. Click on 'Deploy'
18. And Done!

The URL next to 'Invoke URL' is all you need. Try to open it in your browser. You should see a response similar to above. If yes, you can use the URL as your password. If no, something is wrong. You know where to [find me](https://twitter.com/Ba3a_Gamzo).

### More methods coming soon
