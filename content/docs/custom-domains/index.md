---
title: Custom Domains
description: How to add custom domains to Statusflare!
lead: ''
date: 2021-04-22T04:00:00.000+00:00
lastmod: 2021-04-22T04:00:00.000+00:00
images: []
menu:
  docs:
    parent: "Docs"
weight: "130"
toc: true

---
***

Currently, there are two ways to use a custom domain with your Statusflare account. SSL for SaaS is the easiest but does cost money. Another way is for each user to create a workers proxy to bind to their status page.

***

## SSL for SaaS

**Warning: Before you begin, please note that** [**SSL for SaaS**](https://developers.cloudflare.com/ssl/ssl-for-saas) **is currently in beta and requires the "Pro" Statusflare plan.**

SSL for SaaS is the easiest way to get your domain linked to your status page on Statusflare. This method requires the "Pro" Statusflare plan.

**Get Started**

Go to the "custom domains" tab of the settings page. (https://dash.statusflare.com/settings/custom-domains/)

Enter a domain in the box and press the "+ Add Domain" button.

{{< img src="sslsaas-1.png" alt="Rectangle" caption="<em> </em>" class="border-0" >}}

After this, you must go to your DNS provider and add a CNAME, **_status-page-origin.statusflare.com _**for your domain.

The DNS propagation might take a few minutes, and then your custom domain will work with your status page.

***

## Worker method

Another method that has been tested to work is to create a custom proxy with a Cloudflare Worker on your account.

1. **Prerequisites**

* In order to use this method of adding a custom domain, you must have a Cloudflare account. **Please note that Cloudflare is free.**
* The domain that you want to use also has to be hosted on Cloudflare.
* You must also have a Statusflare status page already set up.

2. **Add a worker**

The first thing to do is to go to your [Cloudflare Workers dashboard](https://dash.cloudflare.com/login?redirect_uri=https%3A%2F%2Fdash.cloudflare.com%2F%3Faccount%3Dworkers) and press the blue "Create a Worker" button at the top of the page.

{{< img src="custom-domains-1.png" alt="Rectangle" caption="<em> </em>" class="border-0" >}}

A new window will come up after you press the button. You might see text in the script box, you can go ahead and remove this text.

{{< img src="custom-domains-2.png" alt="Rectangle" caption="<em> </em>" class="border-0" >}}

Next, you will paste this script in the box:

**Note: You must replace \[uuid\] with the UUID of your Statusflare page.**

    worker proxy template// Website you intended to retrieve for users.// Make sure its prefixed with protocol (e.g. https://)const upstream = 'https://[uuid].s.statusflare.com'
    addEventListener('fetch', event => {  event.respondWith(handleRequest(event.request))})
    async function handleRequest(request) {  const url = new URL(request.url)  return fetch(upstream + url.pathname + url.search, request);}

Next press "Save and Deploy"

{{< img src="custom-domains-3.png" alt="Rectangle" caption="<em> </em>" class="border-0" >}}

3. **DNS settings**

After that, you will need to configure your Cloudflare DNS settings to point to your new worker.

Go to your DNS zone on your Cloudflare account and create an "A" record for the subdomain you wish to use. Have the record point towards 1.1.1.1 with the orange cloud on.

{{< img src="custom-domains-4.png" alt="Rectangle" caption="<em> </em>" class="border-0" >}}

Save the record. Next, go to the Workers route assignment page on the regular dashboard.

{{< img src="custom-domains-5.png" alt="Rectangle" caption="<em> </em>" class="border-0" >}}

Press the gray button "Add Route," insert the domain name you set earlier, and select your worker from the dropdown.

{{< img src="custom-domains-6.png" alt="Rectangle" caption="<em> </em>" class="border-0" >}}

Press "Save" and your status page should be published on the domain that you set!