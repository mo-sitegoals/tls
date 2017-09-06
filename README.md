# Texas Linguistics Society (TLS)

This repository contains the source code (HTML/JavaScript/CSS) to generate the TLS website,
as well as any published proceedings documents (PDF).

If you simply want to visit the live site, please go to **<http://tls.ling.utexas.edu>**


## Websites, Servers, and GitHub Pages

#### How websites work

To host a webpage on the internet, a server (computer) must be online and available to respond to incoming requests, at any time, as long as you want the webpage to exist.

For example, when you go to the URL <http://tls.ling.utexas.edu/2016tls/>, your browser first looks up the address of the server that is responsible for the domain `tls.ling.utexas.edu`, then it connects to that server, and requests the server to send it the page content corresponding to `/2016tls/`.
The server, which has been configured to listen for just such a request, finds the data that it has been programmed to associate with that particular request, and sends that data back to your browser.
Depending on the content of that data, your browser may send out additional requests, potentially to other servers,
to retrieve other components of your webpage, such as images.

#### How servers work

Servers and internet connections are not free.
If you want to host an arbitrary webpage on the internet, you will pay for it in some fashion.
If you search the web for "free webpage" you will find lots of services for which you pay by being obligated to show ads to your visitors (or in some cases, by being obligated to pay in money after a short introductory/trial period).

If you happen to own a desktop computer at home, and are already paying for an internet connection, you could technically use that computer to serve your webpage.
However, nobody does this, not even for small/niche websites, due to a number of factors that make this method impractical:

* If your power goes out or your internet goes down, your website will cease to exist until the power/service returns.
* If your internet provider arbitrarily changes your connection's IP address (or you move), you will need to ensure that your visitors are aware of the change (by updating your website address's DNS configuration)
* Your computer will be slower proportionally to how much work it's doing to respond to requests for your webpage, potentially making it unusable for your personal use.
  Similarly, if a lot of visitors visit your webpage simultaneously, some of them will get slow responses, or no response at all, if your computer is working beyond its capacity.
* Your computer will be vulnerable to attacks from the outside world.
  Even if you use secure software to protect against someone gaining access to your computer and using it to do more nefarious things besides viewing your webpage, you cannot protect against a "denial-of-service" attack, which is when someone maliciously pushes your computer beyond capacity, as in the preceding point.
* Your internet provider may decide to limit your bandwidth, or require you to pay them more for additional bandwidth.

Dealing with these issues and liabilities requires considerable labor and attention,
which quickly exceeds the relative inexpensiveness of other options.
It is far more common and cost-efficient to pay someone else to worry about all those problems,
in exchange for access to one of their servers, which generally comes with some guarantee of uptime and bandwidth.

How much you pay for the server depends on the complexity needs of your webpage.
If you are responding with dynamic content that requires the server to do considerable work for each request,
you'll be hard-pressed to find a service cheaper than $5/month,
such as [Digital Ocean](https://www.digitalocean.com/pricing/#droplet) or [Linode](https://www.linode.com/pricing).
With such services, when you stop paying, the server you were paying for will stop responding to requests.

It is much cheaper to serve static content.
"Static" means that for every URL the server is programmed to respond to, it always gives the same response.
This requires very little work from the server; it needs only look for a file matching the specified URL, and send that file to your webpage's visitor.
A static webpage is non-interactive, i.e., your visitors cannot login and receive personalized content, or upload anything, or otherwise manipulate the state of the server.
But for many purposes, and for TLS's purpose in particular, a static webpage is entirely sufficient.

#### Why the TLS website is here on GitHub

GitHub offers to serve static content, ostensibly for free,
as a product they call ["GitHub Pages"](https://pages.github.com/).
This costs GitHub money to do, but not very much, relatively, and their business model in this regard consists of advertising paid plans with more functionality to you, the website developer, rather than your visitors.

This service comes with the intangible cost of having no guarantee,
in that they may cancel or insist on charging for this service at any time.
However, due to the traction and wide adoption / expectation of this service, canceling it would alienate and/or infuriate a large portion of their paying clientele, which makes a strong case for its persistence.

There are also some [usage limits and restrictions](https://help.github.com/articles/what-is-github-pages/#usage-limits) imposed by GitHub, but these are generous and beyond sufficient for the needs of TLS (and even much bigger sites).

In short, despite the advertisement aspect and indeterminate continuation of the GitHub Pages service,
I've concluded that it's the best option for hosting the TLS website for as long as possible with minimal ongoing costs.


## History

The site was originally hosted on a UT server at `http://uts.cc.utexas.edu/~tls`,
but that server was retired (without announcement) in Summer 2016,
so `tls.ling.utexas.edu` is now both the canonical and only URL.


## Archival remarks on legacy directories

`97tls`, `98tls`, and `99tls` weren't exactly named with an optimist outlook for the conference, but that's okay, it was a common mistake back then.

But `tls2009`? There's no excuse. Still, we'll retain a link for backward compatibility.

To be clear, the pattern you should follow for new conferences is <code><b>YEAR</b>tls/</code>.
Honestly, yes, I agree that the trailing "tls" is redundant — that only the year would be cleaner and just as clear.
But see [xkcd #927](https://xkcd.com/927/).


## Administrative notes

`tls.ling.utexas.edu` is a CNAME record (a DNS entry that aliases one domain name to another, rather than from one domain to an IP address, like A records do) that points to `linguistics.github.io`.
Thanks to the [`CNAME`](CNAME) file in this repository, GitHub knows that incoming requests with the header `Host: tls.ling.utexas.edu` should be served static files from this directory. GitHub uses Fastly to serve GitHub pages, so we get the benefit of an incredibly fast CDN (content delivery network), for free. The disadvantage is that GitHub pages only serves static files — no PHP, ASP.net, etc. But static files have much greater longevity, so in the long run, it's a healthy constraint to have.

UT ITS controls allocation of all `*.utexas.edu` domains, so if any issues arise with that DNS entry, your best bet is to search for "UTnic" on the [utexas.edu](https://www.utexas.edu/) website or file a ticket with the IT folks.


## Files

* [`.nojekyll`](.nojekyll): this is just a configuration file that tells GitHub pages not to run [Jekyll](https://jekyllrb.com/) on these files.
  Jekyll is handy in some cases, but didn't fit with the archival needs of this repository.
  This is optional; since none of the files contain Jekyll directives, nothing would be changed in the Jekyll-rendered result, but by skipping Jekyll, you'll see changes on the live site more quickly after you do a `git push`.
* [`archive.html`](archive.html): is a static listing of all conferences with direct links. This should probably be moved into `index.html`, after getting rid of the current `index.html` redirect.
* [`CNAME`](CNAME): another GitHub Pages configuration file that tells to GitHub to serve requests it receives for `tls.ling.utexas.edu` with files from this directory.
* [`index.html`](index.html): this is the file people get when they go to <http://tls.ling.utexas.edu/>.
  It is currently configured to serve a redirect to the most recent (TLS 2016) year-specific site.
  This is probably not the best solution. When linking to your conference you should use the full URL, but in some cases `tls.ling.utexas.edu` looks nicer, so in practice, you'll likely want to change the links in this page to the current year's site.


## Documents

* [`CONTRIBUTING.md`](CONTRIBUTING.md): Describes how to make changes to this repository; and as a result, how to add pages to the <http://tls.ling.utexas.edu/> website.
* [`2014tls/README.md`](2014tls/README.md): Records some notes and reflections on running TLS 2014, including general advice, overly optimistic thinking, and potentially out-of-date or overly specific suggestions.
