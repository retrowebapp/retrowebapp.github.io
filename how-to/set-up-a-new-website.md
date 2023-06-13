## How to:
# Set up a new website

__Ruth Webster, June 13th 2023__

This how-to guide will walk you through the process of buying a .com domain
name, and hosting a minimal 'Coming soon' page on GitHub.

The domain registration will cost $9.73 USD per year, and the GitHub hosting is
free (and will hopefully be free forever).

---

This guide uses six placeholders:
- Substitute `mydomainname` with your own domain name
- Substitute `dn` with a two-letter acronym of your domain name
- Substitute `Kim` with your own first name
- Substitute `Doe` with your own second name
- Substitute `kimdoe` with your own username
- Substitute `13/6/2024` with the date one year from today

---

## I. Set up Brave

1. Download, install, and open the [Brave browser](https://brave.com/download/)
2. In Brave, install and enable the 'Ghostery' extension
3. In Brave, install and set up the 'Avast Online Security & Privacy' extension
4. In Brave, log out of Google, Microsoft, or any other accounts

## II. Create a Buttercup vault and an outlook email address

1. Download, install, and open the [Buttercup](https://buttercup.pw/) app
2. Archive -> New Archive -> `dn`-`mydomainname`-2023.bcup
3. Choose a secure, unique password which you won't forget
4. Click '+ ADD ENTRY'
5. Title: outlook.live.com -> Username: `mydomainname`
6. Click the magic wand icon -> 'USE THIS', and then 'SAVE'
7. In Brave, visit https://outlook.live.com/
8. Click 'Create free account' -> '`mydomainname`' @outlook.com -> 'Next'
9. Click the copy icon which appears when you hover on the password in Buttercup
10. Paste it into the 'Create password' field in Brave
11. For the Brave 'Save password?' popup, click 'Never'
12. First name: `Kim` -> Surname: `Doe`
13. Country/region: [your country] -> Date of birth: [your date of birth]
14. Stay signed in? Select 'Don't show this again' and click 'No'
15. Visit https://outlook.live.com/ - you should see the inbox
16. For the '...asking you to Open email links' popup, click 'Block'

## III. Create a porkbun.com account

1. In Buttercup, click '+ ADD ENTRY'
2. Title: `13/6/2024` domain porkbun.com -> Username: `kimdoe`
3. Click the magic wand icon -> 'USE THIS', and then 'SAVE'
4. In brave, visit https://porkbun.com/ -> click 'SIGN IN'
5. Under 'Create a New Account', USERNAME: `kimdoe`
6. PASSWORD: [pasted from Buttercup]
7. EMAIL: `mydomainname`@outlook.com - will be kept private
8. FIRST OR GIVEN NAME: `Kim` -> LAST NAME: `Doe` - will be kept private
9. ADDRESS: [your home or business address] - will be kept private
10. PHONE NUMBER: [your home or business phone number] - will be kept private
11. Tick the "I acknowledge that I have read and agree..." checkbox
12. Select 'No. I don't want your awesome emails :('
13. Click 'Create Account'
14. For the Brave 'Save password?' popup, click 'Never'
15. In Outlook, find the 'porkbun.com | Account Verification' message
16. Click the 'Verify Email Address' link
17. Tick the "I acknowledge that I have read and agree..." checkbox
18. Click 'Submit'
19. Visit https://porkbun.com/account and scroll to '2FA - Email Based (beta)'
20. Click the red slider under 'Enable email based two factor authentication.'
21. Click 'Ok' in the popup
22. In Outlook, find the 'porkbun.com | 2FA' message
23. Copy-paste the 2FA code under 'Verification code' in the popup
24. Copy-paste the backup codes into a Buttercup field labelled '2FA Codes'
25. Click 'Close' on the 'Backup 2FA Codes' popup

## IV. Buy the `mydomainname`.com domain

1. Visit https://porkbun.com/products/domains
2. In the big search field: `mydomainname`.com
3. Click the '+' next to '`mydomainname`.com $9.73 / year renews at $9.73'
4. Click 'Checkout' -> Registration: 1 Year -> click 'Continue to Billing'
5. Click 'PayPal' -> tick "I acknowledge ..." -> click 'Continue to PayPal'
6. Enter your email ... started: `mydomainname`@outlook.com -> click 'Next'
7. Under 'Pay With Debit or Credit Card', Country/region: [your country]
8. Email address: [an existing email address] -> Mobile: [your mobile number]
9. Fill in your card details
10. Total you'll pay: [should be $9.73]
11. Billing address: [the name and address on your credit or debit card]
12. Disable 'Save information & create your PayPal account'
13. For the Brave 'Save card?' popup, click 'No, thanks'
14. Click 'Continue'
15. After a short delay, you should see a green 'Thank You! ...'
16. Below, '`mydomainname`.com' should say 'Pending initial ... check status.'
17. Refresh the page, until you see the round icons
18. Click 'Details' -> AUTO RENEW: toggle from green to red

> __HOT TIP:__ Set yourself a repeating calendar event with an alarm, to remind
> you to renew your domain registration, for $9.73.

## V. Set up email forwarding

1. Continuing from the page above, click the round email icon
2. Under 'Option 2: Email Forwarding', When ... an email to: info
3. Deliver it to: `mydomainname`@outlook.com

## VI. Create a GitHub account

1. In Buttercup, click '+ ADD ENTRY'
2. Title: GitHub -> Username: `mydomainname`
3. Click the magic wand icon -> 'USE THIS', and then 'SAVE'
4. In brave, visit https://github.com/ -> click 'Sign up'
5. Enter your email: info@`mydomainname`.com
6. Create a password: [pasted from Buttercup]
7. Enter a username: `mydomainname`
8. Would you like to ... via email: n
9. Solve the puzzle, and click 'Create account'
10. In Outlook, find the 'Your GitHub launch code' message
11. Copy-paste the launch code under 'Enter code'
12. For the questions, 'Just me' -> click 'Continue'
13. Don't tick any interests -> click 'Continue'
14. Click 'Continue for free'

## VII. Create the website repo

1. At https://github.com/ click the '+' icon near the top right corner
2. Click 'New repository'
3. Repository name: `mydomainname`.github.io (a special name, for the apex domain)
4. Description: `mydomainname`.com
5. Keep 'Public' selected -> tick the 'Add a README file' checkbox
6. Click 'Create repository'

## VIII. Create an 'Coming soon' homepage

1. Click 'Add file' -> 'Create new file'
2. For 'Name your file', enter 'index.html'
3. For 'Enter file contents here', copy-paste the minimal page below
4. Click 'Commit changes...'
5. Commit message: 'adds minimal "Coming soon" page'
6. No 'Extended description', and keep 'Commit ... main branch' ticked
7. Click 'Commit changes'
8. Visit https://`mydomainname`.github.io/ - at first it will show a default page
9. After a minute or two, it should show the new 'Coming soon' page

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>mydomainname.com</title>
  </head>
  <body>
    <h1>mydomainname.com</h1>
    <p>Coming soon</p>
  </body>
</html>
```

## IX. Point `mydomainname`.com to the GitHub repo

1. Visit https://porkbun.com/account/domainsSpeedy
2. Click the small 'DNS' link under '`mydomainname`.com'
3. Check under 'Current Records' - there's 1 'CNAME' and no 'A' records
4. Under 'Quick DNS Config', click 'GitHub' and click 'Ok' to confirm
5. Host: www [the default]
6. Answer: `mydomainname`.github.io -> click 'Submit'
7. On the 'We were able ... DNS records' popup, click 'Ok'
8. Check under 'Current Records' - there are now 2 'CNAME' and 4 'A' records
9. Back in the GitHub repo, click 'Settings' -> click 'Pages' in the sidebar
10. Under 'Custom domain', enter '`mydomainname`.com' -> click 'Save'
11. Note that GitHub adds a file called 'CNAME' to your repo's top level
12. It should now say 'DNS check successful' under that input field
13. Under that should say 'TLS certificate is ... 15 minutes to complete.'
14. 'Enforce HTTPS' should not be ticked, if you want to support old browsers
15. After a few minutes, these 4 URLs should all work:
    - https://`mydomainname`.com
    - https://www.`mydomainname`.com [301 to https://`mydomainname`.com]
    - http://`mydomainname`.com [redirects, unless curl or old browser]
    - http://www.`mydomainname`.com [combination of the above two behaviors]

> __IMPORTANT NOTE:__ Now back up your `dn`-`mydomainname`-2023.bcup file,
> copied to several safe places. In January 2024, change all the passwords and
> save as a new file `dn`-`mydomainname`-2024.bcup. Rinse and repeat every year!
