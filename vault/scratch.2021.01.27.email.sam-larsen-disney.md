---
id: ca3f878e-1b2d-4ca7-96f5-2af9f63126e6
title: Pair with Sam Larsen Disney for email creation and distribution
desc: ''
updated: 1612124436921
created: 1611756544773
---

## The format of the email

Sam uses [Maizzle] to make the HTML email look pretty then has
SendGrid to send the emails.

There's a lot to go over here

SenGrid there was a fail bot to go over and Sam was kind enough to
walk me through a lot of it

## Sending the emails

[SendGrid] for emails, use automations for a thank you after a new
sign-up, Sam has this in a node server.

Single send is for the newsletter, blank template in send grid then
paste in the raw HTML from Maizzle.

## What Sam uses for his slides navigation

https://github.com/slarsendisney/sld-clicker

He's looking at moving some of it to firebase serverless functions as
he has a few Heroku servers to manage these things currently.

## There was two approaches

There was two approaches to getting the data to SendGrid, the first
one was with a SendGrid form and pulling the API key from the POST.

The second approach was to put directly from the sign-up form to the
SendGrid API with a PUT request.

This was all Sam so massive thanks to him for walking me through this!

Here's an example of the request:

```js
export default async function putToSendGrid(email, name) {
  await fetch('https://api.sendgrid.com/v3/marketing/contacts', {
    method: 'PUT',
    headers: {
      'Content-Type': 'application/json',
      Authorization: `Bearer ${process.env.GATSBY_SENDGRID_API_KEY}`,
    },
    body: JSON.stringify({
      list_ids: ['785c6867-cc31-46e9-84af-c5bf6935acd7'],
      contacts: [
        {
          email,
          first_name: name,
        },
      ],
    }),
  })
}
```

The `list_ids` here is the contacts list from my SendGrid Contacts
section, under Marketing/Contacts in SendGrid.

<!-- Links -->

[maizzle]: https://maizzle.com/
[sendgrid]: https://app.sendgrid.com
