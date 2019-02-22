+++
categories = ["web"]
color_choice = ""
date = "2019-02-22T17:20:38+00:00"
draft = true
title = "Name Cheap and MailGun"

+++
I was having trouble getting MailGun  to work with my NameCheap domain, so I contacted their customer support and this was the solution.

I was pretty close to getting it correct but my problem was

> The only issue as it is not allowed to use full domain (like #_#mydomain.com#_#) in the host field in our system.
>
> So, please remove '#_#mydomain.com#_#' part from host fields for all your records, including MX records.

So for example

    smtp._domainkey.mg.mydomain.com

became...

    smtp._domainkey.mg

My Final Advanced DNS Records looked like this

CNAME Record  email.mg  mailgun.org

TXT Record  mg  v=spf1 include:mailgun.org \~all TXT Record  smtp._domainkey.mg  k=rsa; p=somelongstringhere

URL Redirect Record  @  http://www.mydomain.com/  unmasked

MX Record  mg mxa.mailgun.org  10  automatic
MX Record  mg mxb.mailgun.org  10  automatic