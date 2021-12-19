# Passwordless Login
Don't want to share password with us? We got you covered. But before moving forward...
## Can we steal your account if you share your password?
Absolutely not! Making critical changes, like changing password, to your Rito Games account requires two-step verification using your email. Basically, Riot Games emails you an OTP. So, no one can steal your account even if you share your password. However, they can login and play with your account.
But you can trust us and we will strive to maintain your trust. Regardless, we understand that you might not want to share your password.
## How to not share your password and still use our tools?
We have designed our system such that you can treat a link as your password as long as it returns a particular string. Let me explain this in plain English. Let's take an example of this link here: `link here`.
Go ahead and open it in your browser. It returns: `https://playvalorant.com/opt_in#access_token=eyJ...expires_in=3600`.
### But what it is?
Well, it contains something called as _access token_ for your account. Access Tokens can be treated as temporary (see the end of the string, it says `expires_in=3600`) password to access your account programatically only. You can not use your Access Token to login with Riot Client as you normally do with your password.
## How to set up your own Passwordless Login URL?
Don't worry. It's not as difficult as it sounds. Plus, we have prepared a few tutorials. You can also tweet me [@Ba3a_Gamzo](https://twitter.com/Ba3a_Gamzo) for help, or you can follow the easiest method, i.e. enter your password on our website. Below are the few methods that you can employ to create your own URL.
### DIY (for devs)
Do it yourself. Just make sure that it does not take more than 4 seconds to load. You can use this awesome script for reference.
### Amazon Web Services (AWS)
We will use AWS Lambda and AWS API Gateway to create you a serverless function that returns your Access Key on an URL. That way you don't have to share your password with us, it will stay on _your_ AWS account. Let's get building, shall we?
The process is very simple, just follow along.
#### Create an AWS account
Go to [this link](https://aws.amazon.com/free/) and create a free AWS acocunt. Just follow along the prompt. They have a very generous free usage policy, you don't have to pay anything.
#### Updating the tutorial soon ...
