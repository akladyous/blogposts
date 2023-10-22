---
title: Ruby on Rails Action Mailer Configuration
date: 2023-10-05
tags: ['action mailer', 'Ruby On Rails', 'ActionMailer', 'gmail']
---

# How does Action Mailer work?

![action mailer](/images/action-mailer-config.png)

### Action Mailer overview

Rails has a wonderful built-in mailing system called Action Mailer, which allows us to send email
from our application as long as we have a mailer model. Mailers are actually a lot like controllers:
they have their own app/mailers directory, and each mailer has its own associated view as well. Each
mailer also inherits from ActionMailer::Base, and just like controllers, can be generated really
easily.

This tutorial explains how to configure Ruby on Rails in the development environment toward sending
emails via Ruby on Rails Action Mailer integrated with the most popular email providers Gmail &
SendGrid.

Let’s take it step by step, first we need to do a bit of configuration, we are going to send emails
from the developement enviroment.

## ActionMailer Gmail Confiruation

In order to use Action Mail with Gmail, the best solution that does not violate your other security
such as 2-step certification is using
[app Password](https://support.google.com/accounts/answer/185833)

\*\* Open your [Account Security Settings](https://myaccount.google.com/security)

![Alt google-app-passwords](/images/action-mailer-config-1.png)

- Navigate to App Password

![Alt google-app-passwords](/images/action-mailer-config-2.png)

On the App Password page, select “Mail” app, and “Other” device, now we provide the name of ruby on
Rail application. Then click “Generate”.
