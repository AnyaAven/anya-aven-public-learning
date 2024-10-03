# SEO

---

# Canonical tag
Shows the true source of a piece of content.
For example if I post an article on my blog, I will have it canonically tagged 
as the original. If someone takes that same content for their medium article, 
Google will (ideally) rank that lower than mine (or unranked).

 # 

technical seo vs on-page seo

pagespeed insights website (or lighthouse in dev console)

Can put any website in here to test it's metrics

Google ranks mobile scores higher and desktop doesn't matter as much.
Even if your clients come from desktop mainly, that won't care about the desktop.

Performance helps rank!

accessibility matters.

Only 1 h1 tag, then h2, etc. 


---

Google Search console. 

Set up Google Search Console to request deindexing if need be. 
Need access to google account though.

Can see what indexed and not indexed

Crawler
- Discovered ( the crawler has been here)
- Crawler budjet, only will crawl so many pages

The places where currently not indexed is good for like /image-1 because we don't wanna spend our crawl budget on that slug.
But if it's really bad google won't index in it.

Linking inside your own website helps the crawlers navigate.

moz.com is helpful to see the standards. It explains the authority that a site has
(DA, domain authority)
keysearch.co

If Google thinks you're keyword stuffing, it will penalize you and remove any ranking.
AKA "Acorn" keyword copy and pasted as white on a white background is penalized now.

Google loves lists, aka <ul> tags.
Step by step instructions on a recipe

Google loves questions!! Add them.
"People also ask" dropdown in google is often added and uses FAQs for each question.

searchenginejournal.com
What is Schema markup and why is it important for SEO?
It isn't a visual component but its eaiser to read a json thing for the crawler

Put it in a script tag. Likely a lower script tag where I as a dev can keep it in the same.

Script tags that are specific for that page (aka for an FAQs) should NOT BE IN THE HEAD TAG. 
Head scripts only inside should be general

Updating your content is a good thing so Google can index it again!

Vague bullet points aren't good.
- flavorful
- key friendly

Too generic ^

Fix all your broken links

Rare for performance scores to be at 90 unless there SSR (server side rendering)
React is terrible for SEO.
NextJS and gatsy is nice.

Squarespace doesn't care about performance as much. It uses a lot of unused CSS and JavaScript

"Everygreen content"

6 months to see results and 1 year to really be there.
Authority isn't gained overnight.

## Website Recourses
[Google Lighthouse](https://googlechrome.github.io/lighthouse/treemap/?gzip=1#)
[Page Speed Insights](https://pagespeed.web.dev/)
[Key Search](keysearch.co)
[Search Engine Journal](searchenginejournal.com)


