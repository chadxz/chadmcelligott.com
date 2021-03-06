---
layout: post
title: "Taming ASP.NET MVC 4's bundled scripts and styles"
date: 2013-08-12 16:09:00
tags:
 - asp.net
 - c#
---

I have been working on a responsive design project in ASP.NET MVC 4 using the "Microsoft ASP.NET Web Optimization Framework" (nuget id: [Microsoft.AspNet.Web.Optimization][1]), which introduces the ability to create bundles of scripts and styles.  These bundles can then be included in my view using syntax like `@Scripts.Render("~/bundles/header-scripts")`.  This can be nice if you have many scripts to include, but the best benefit is its ability to concatenate, minify, and name your scripts/styles.  Concatenation and minification are nice to improve the performance of the site, and automatic name management is nice because it will force an updated script to be re-downloaded instead of served from the browser cache.

By default, the bundling framework has some built-in magic that decides how best to order the scripts and styles included.  Imran Baloch has a [blog post][2] providing details of the script/stylesheet names that take precedence over others by default.

To take complete control over the ordering of the scripts or styles in the bundles that you create, simply put `bundles.FileSetOrderList.Clear();` at the top of your RegisterBundles function, i.e.

```c#
public class BundleConfig
{
    public static void RegisterBundles(BundleCollection bundles)
    {
        // remove built-in preferential ordering
        bundles.FileSetOrderList.Clear();

        // javascript to be included in the header
        bundles.Add(new ScriptBundle("~/bundles/header-scripts")
            .Include("~/Content/Scripts/mysite.js")
            .Include("~/Content/Scripts/Vendor/modernizr-{version}.js"));

        // javascript to be included before the </body> tag
        bundles.Add(new ScriptBundle("~/bundles/footer-scripts")
            .Include("~/Content/Scripts/Vendor/jquery-{version}.js")
            .Include("~/Content/Scripts/Vendor/bootstrap-{version}.js"));

        // css
        bundles.Add(new StyleBundle("~/bundles/css")
            .Include("~/Content/Styles/Vendor/bootstrap-{version}.css")
            .Include("~/Content/Styles/mysite.css"));
    }
}
```
Once you have cleared the `bundles.FileSetOrderList` property, the order that you add the files to your bundle will be the order they are included in your page (when `<compilation debug="true">` in your web.config) or the order they are included in the minified and concatenated file (in the case of `debug="false"`)

Thanks to [Steve Fenton][3] on stackoverflow for his insightful explanation of this process.
[1]: http://www.nuget.org/packages/microsoft.aspnet.web.optimization/
[2]: http://weblogs.asp.net/imranbaloch/archive/2012/09/30/hidden-options-of-asp-net-bundling-and-minification.aspx
[3]: http://stackoverflow.com/questions/13130833/how-do-i-configure-mvcs-style-bundling-order
