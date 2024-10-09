# Website

I'd considered a while ago that having a website for blog posts and project pages is a good idea. It's a nice portfolio for people to be able to review what I've been working on.

I hate HTML, I find writing it it really awkward so my first requirement is to not use HTML at all. I don't need it to be super snazzy and I'm realistically not going to spend a load of time on CSS to make it look pretty, but I do want it to render well on both PC and mobile.

From my initial research it looked like Python and Flask were good choices. I'd researched using Rust but it didn't look like there was as good support for presenting websites using Rust. It's great for backend stuff and APIs but not for web presentation.

One big idea is that I wanted the page to be scalable, so designing it in a way that benefits from docker and kubernetes was a must. On that vein I decided to separate out the content from the framework and created 2 repos to achieve this:
* [techartdesign-content](https://github.com/richClubb/techartdesign-content/)
* [techartdesign-framework](https://github.com/richClubb/techartdesign-framework)

Initially it was deployed in Azure on a debian VM using Apache but I wanted it to be containerised for easy deployment. I spent about a day working on getting it running in a docker container and finally got it working so I can deploy it by just building and running docker commands.

It does require a fair number of secrets which are currently not very secure but with the current architecture I'm not sure how to make it better. I'd considered using Azure KeyVault but that might be a task for another day.

## Next Steps

* ~~Get it deployed into a docker container and working "out-of-the-box"~~ - Done
* Get it working with Kubernetes
* Use some kind of keyvault so that I don't have to deal with secrets for the cert etc.
* Look at contributing to the Flask markdown project as it's now been orphaned.
* Figure out a way to get the headings to appear in the sidebar as a navigable TOC
    * This is probably going to require contributions 