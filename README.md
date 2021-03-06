# Inliner

> Avoid inline/embedded code !!!
 
Using external files is a classical Web Performance Optimization ([references](https://developer.yahoo.com/blogs/ydn/high-performance-sites-rule-8-javascript-css-external-7205.html)), but *sometimes* it's better to include your styles/scripts in the web page.
- you have small assets (a few KBs)
- the cost of making a request is greater (new DNS queries, mobile network, ..)
- you never expect return visitors (landing page, temporary campaign, ...)

Inliner is a small library on the top of Microsoft.Web.Optimization (aka asp.net Bundling & Minification), that allow you to embed your resources/bundles in a web page.

# Install

`Install-Package Inliner`

# Getting Started

## Embed a Bundle
```
// BundleConfig
public static void RegisterBundles(BundleCollection bundles)
{
   bundles.Add(new StyleBundle("~/Content/css").Include(
   "~/Content/bootstrap.css",
   "~/Content/site.css"));
}

// _layout.cshtml
@Inliner.Styles.Render("~/Content/css")

```
## Embed a file
```
// _layout.cshtml
@Inliner.Scripts.Render("~/Scripts/main.js")
```
## Embed a directory
```
// _layout.cshtml
@Inliner.Scripts.Render("~/Scripts")
``` 