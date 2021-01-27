---
id: ca3f878e-1b2d-4ca7-96f5-2af9f63126e6
title: Sam Larsen Disney
desc: ''
updated: 1611757178218
created: 1611756544773
---

## The format of the email

Sam uses [Maizzle] to make the HTML email look pretty then has
sendgrid to send the emails

## Sending the emails

[SendGrid] for emails, use automations for a thank you after a new
sign-up, Sam has this in a node server.

Single send is for the newsletter, blank template in send grid then
paste in the raw HTML from Maizzle.

## What Sam uses for his slides navigation

https://github.com/slarsendisney/sld-clicker

He's looking at moving some of it to firebase serverless functions as
he has a few Heroku servers to manage these things currently.

<!-- Links -->

[maizzle]: https://maizzle.com/
[sendgrid]: https://app.sendgrid.com
