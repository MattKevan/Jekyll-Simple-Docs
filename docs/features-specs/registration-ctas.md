---
layout: docs
title: Registration calls to action 
description: A quick summary of Registration calls to action
group: features-specs
toc: true
---
​
**August 2018** 
Version 1
​
## Contents
* Unconfirmed user calls to action
* Competitions pages
* Pregnancy registration modal

## Unconfirmed user calls to action
### Features
* Logged in user with unconfirmed email address sees confirm email call to action banner at top of all site pages
* Logged in user with unconfirmed email address sees confirm email call to action block at bottom of talk threads, instead of post form.
​
JMW: Each feature should have it's own user story / acceptance criteria, so it can be implemented independently. 
In this istance I'd replace the two features above with 1 feature called 'Logged in users with unconfirmed email addresses sees confirm email call to actions'. 
Then we wrap it into 1 feature and the story and acceptance criteria apply. 

### User stories
User has completed registration process and is logged in, but has not yet confirmed their email address.
​
User sees banner below the header on every page reminding them to confirm their email. User also sees call to action on talk pages, instead of the post form.
​
User may: 
* Go to their inbox and click the confirmation link, where they are taken to the default 'thank you for confirming' page.
* Click the 'send another' link in the call to action. The site will send them a new email, where they click the link and are taken to the thank you page.

Once their email is confirmed they no longer see the messages and are able to post in Talk as usual.
​
### Acceptance criterea

* Logged in user with unconfirmed emails always see banner and talk CTA
* Logged in users with confirmed emails never see banner and talk CTA
* Non-logged in users never see banner and talk CTA 

JMW: I think this is now wrong - it's right for the banner but not the talk CTA - they will see the talk CTA but it will be different messaging? 
Might actually be better to treat this as a separate feature on second thoughts 'Users sees talk CTA' then detail the cases for not logged in / logged in no confirm / logged in & confirm. 

* Banner and talk CTAs always appear in the same place 
* Clicking link to ‘send another’ sends a ‘confirm email’ email to user and changes CTA message to tell user email has been sent 

### Tech spec

For Rails we use the KIT method (TBC) to wrap the banner so only logged in / unconfirmed see it. For Java we use the method (TBC) to do the same. 
​
‘Send another’ fires an ajax call to the user service and changes the message. User service sends the email via events. 
​
Banner needs to be part of header delivered through global UI service (TBC: Can we have conditionals in this code or do we need to bake this into every service??) 
​
## Competitions pages

### Features
* Editors can make competitors available to logged in users only 
* User must be logged in to view the competition entry form

JMW: Again I would have this as 1 feature - last bullet point is acceptance criteria. 

### User stories

Logged out user arrives on a competition page. 

If user has a Mumsnet account they click the login button and are taken to the login form. On successful login they are returned to the competition page, where they complete the entry form.

If a user does not have a Mumsnet account they click the register button and are taken to the registration form where they complete the registration journey. On clicking the confirmation link in their email, they are returned to the competition page where they may enter the competition as usual.

JMW: Are we changing the registration functionality here or does it work like this now - can't remember? 
I thought thank you page might take you to home?

### Acceptance criterea
* Editor can choose whether to make a competition available to logged-in users only
* If set to logged in only, logged out or unconfirmed users may not enter the competition. 
* If users are logged out they are shown a call to action to register or join
* If users have not confirmed their email address, they are shown a call to action to do so.

### Tech spec

## Pregnancy registration modal

### Features
* User can register to receive pregnancy emails
* User can calculate their due date
​
JMW: Again I would have 1 feature per story, AC 

### User stories
User arrives on pregnancy Talk or pregnancy content pages. User is logged out.
​
User enters their email address, chooses a password and a username. User enters their due date. If they are not sure what their due date is, they can use the included due date calculator to find it out.
​
User selects to sign up to the pregnancy emails and checks the GDPR consent option.
​
User clicks the submit button. User's account is created. They are shown the 'congrats' message and sent a confirmation email.
​
### Acceptance criterea
* Content can decide which pages/Talk topics to show the modal on (list to be provided)
* Modal or block is only shown to logged-out users
* User may dismiss the modal or block. If they dismiss it, they do not see it again
* User may not enter email address already associated with an account
JMW:  What happens if they do. 
* User may not use a taken username – live form validation ensures username is original (same as standard registration form)
JMW:  What happens if they do. 
* User must enter password of sufficient strength (same as standard registration form)
JMW:  What happens if they do. 
* Pregnancy emails option is not pre-selected. User may sign up without checking this option
* If user selects pregnancy emails they are subscribed to the pregnancy email list
* User must select 'Mumsnet can store this information about me' to submit the form
JMW:  What happens if they don't
* If user has an account they may click the 'Sign in' link to go to the standard login form.

### Tech spec
​


