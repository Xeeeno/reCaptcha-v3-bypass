# reCaptcha-v3-bypass
How to solve reCaptcha v3 and get a 'human like (>0.7–0.9)' score

Step 1: Sign Up for capsolver.com
To start using capsolver.com, you need to sign up for an account. Visit the website and click on the 'Sign Up' button. You will be prompted to enter your email address and create a password. Once you have provided the necessary information, click on the 'Sign Up' button to create your account.
Step 2: Add Funds to Your Account
Before you can start solving reCaptcha v3, you need to add funds to your capsolver.com account. Click on the 'Add Funds' button and select your preferred payment method. Follow the on-screen instructions to complete the payment process.
Step 3: Solve reCaptcha v3
To solve reCaptcha v3, we will use a test page to verify the score of our tokens. The page will be https://antcpt.com/score_detector, we will need proxies (residentials, datacenter, mobile proxies works) and also a capsolver key with balance. It's pretty simple of how to solve reCaptcha v3, you just need the right websiteUrl, websiteKey, pageAction and also a good proxy.
By default, the pageAction is verify, but the site can customize, so remember that you must check if it's verify or a custom one.
For solve reCaptcha v3 for the test site, we will just need to send to capsolver this information:
POST https://api.capsolver.com/createTask
{
  "clientKey":"yourapiKey",
    "task":
        {
          "type":"ReCaptchaV3Task",
        "websiteURL":"https://antcpt.com/score_detector",
        "websiteKey":"6LcR_okUAAAAAPYrPe-HK_0RULO1aZM15ENyM-Mf",
        "pageAction": "homepage",
        "proxy":"yourproxy"
        }
}
Step 4: Check the Results
We will need to retrieve the getTaskResult method until the captcha is solved.
Example:
POST https://api.capsolver.com/getTaskResult
Host: api.capsolver.com
Content-Type: application/json

{
    "clientKey":"YOUR_API_KEY",
    "taskId": "TASKID OF CREATETASK" //ID created by the createTask method
}
After the captcha has been solved, you can check the captcha token by sending the token to the site, example:
var request = require('request');
var options = {
  'method': 'POST',
  'url': 'https://antcpt.com/score_detector/verify.php',
  'headers': {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    "g-recaptcha-response": "here the token of capsolver"
  })

};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});
And the test page will give the response of the score of the token.
In conclusion, solving reCaptcha v3 can be a daunting task, but with the help of capsolver.com, it can be done quickly and efficiently. By following the steps outlined above, you can easily solve reCaptcha v3 and get a 'human like' score.
