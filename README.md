# Table of Contents

- [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Prerequisites](#prerequisites)
    - [.NET 6.0](#net-60)
    - [.NET 5.0](#net-50)
    - [Visual Studio 2022 Preview](#visual-studio-2022-preview)
    - [Mobile Development with .NET Workload](#mobile-development-with-net-workload)
  - [Demo](#demo)
    - [Create a Blazor Server Application](#create-a-blazor-server-application)
    - [.NET 6.0 HeadContent and PageTile](#net-60-headcontent-and-pagetile)
      - [*Index.razor* PageTitle](#indexrazor-pagetitle)
      - [*Counter.razor* PageTitle](#counterrazor-pagetitle)
      - [*FetchData.razor* PageTitle](#fetchdatarazor-pagetitle)
      - [*Index.razor* HeadContent](#indexrazor-headcontent)
      - [*Counter.razor* HeadContent](#counterrazor-headcontent)
      - [*FetchData.razor* HeadContent](#fetchdatarazor-headcontent)
    - [SEO in a Blazor Server Application Converted from .NET 5.0 to .NET 6.0](#seo-in-a-blazor-server-application-converted-from-net-50-to-net-60)
      - [*Index.razor* HeadContent](#indexrazor-headcontent-1)
      - [*Counter.razor* HeadContent](#counterrazor-headcontent-1)
      - [*FetchData.razor* HeadContent](#fetchdatarazor-headcontent-1)
  - [Summary](#summary)
  - [Complete Code](#complete-code)
  - [Resources](#resources)

## Introduction

In this episode, we are going to build a Blazor Server App and show you some tips and tricks to make it SEO friendly. We are going to see how `ServerPrerendered` helps with SEO.

End results will look like this:

![Logs](images/image.png)

Let's get to it.

## Prerequisites

The following prerequisites are needed for this demo.

### .NET 6.0

Download the latest version of the .NET 6.0 SDK [here](https://dotnet.microsoft.com/en-us/download).

### .NET 5.0

Download the latest version of the .NET 5.0 SDK [here](https://dotnet.microsoft.com/en-us/download/dotnet/5.0).

>:blue_book: The .NET 5.0 is needed only to demonstrate how to implement SEO in a Blazor Server app converted from .NET 5.0 to .NET 6.0.

### Visual Studio 2022 Preview

For this demo, we are going to use the latest version of [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/community/).

### Mobile Development with .NET Workload

In order to build Blazor apps, the ASP.NET and web development workload needs to be installed, so if you do not have that installed let's do that now.

![ASP.NET and web development](images/34640f10f2d813f245973ddb81ffa401c7366e96e625b3e59c7c51a78bbb2056.png)  

## Demo

In the following demo we will create a Blazor application and I will show you how to make it SEO (Search Engine Optimization) friendly, by leveraging the new `<PageTitle>`, and `<HeadContent>` tags introduced in .NET 6.0.

We are going to talk about the how `ServerPrerendered` aids with that, and how you can take a .NET 5.0 Blazor Server application, and make changes to take advantage of the new `<PageTitle>`, and `<HeadContent>` features by converting it to .NET 6.0.

Finally, we will also talk about `ServerPrerendered` in Blazor WebAssembly applications, to also create a SEO-friendly application.

Let's get started by creating a Blazor Server Application.

### Create a Blazor Server Application

![Blazor Server Application](images/a2daeedfde2b49ee5be16cf5c6ac1e7722fb0fa55b557955eaeb78f39bf51c18.png)

![Additional Information](images/7755ea2021df87ef11df82a5d0fc7bd29e8009a7b509ed0bbdedc3f82870e913.png)  

As you may know, in order to build a SEO friendly application, we need to provide at a very minimum, a useful title and description for every page. We do this inside the `<head>` section, with the HTML `<title>`, and `<meta>` tags, respectively.

Search engines will use these pieces of information when crawling your pages, and to display their search results.

>:blue_book: As I mentioned, title and description, are the minimum items you want to include for SEO, but for a deeper understanding refer to the official guidelines for each search engine.  [Search Engine Optimization (SEO) Starter Guide](https://developers.google.com/search/docs/beginner/seo-starter-guide?hl=en&visit_id=637639370449073519-226133402&rd=1), and [Bing Webmaster Guidelines](https://www.bing.com/webmasters/help/webmasters-guidelines-30fba23a).

### .NET 6.0 HeadContent and PageTile

The ability to modify the `<head>` content in Blazor applications was introduced in .NET 6.0 with the addition of `<PageTitle>` and `<HeadContent>`. No longer you have to rely on third party tools or `JSInterop` to modify the `<head>` content.

By default, in a Blazor Server app, a title will be specified for you for the three pages provided by the template `Home` (*Index.razor*), `Counter` (*Counter.razor*), and `Weather forecast` (*FetchData.razor*).

The template does this, by defining a `<PageTitle>` section for each page, as you can see in code from the files below:

#### *Index.razor* PageTitle

```razor
<PageTitle>Index</PageTitle>
```

#### *Counter.razor* PageTitle

```razor
<PageTitle>Counter</PageTitle>
```

#### *FetchData.razor* PageTitle

```razor
<PageTitle>Weather forecast</PageTitle>
```

Let's add now a `meta` description to hour pages, we do that with the `<HeadContent>` razor tag.

Inside of `<HeadContent>` add an `HTML` `<meta>` tag, and when you type `name="` IntelliSense will provide you with a long list of available meta tags you can choose from, as you can see in the following image:

![Meta Tags](images/7e9e9c987ec9666cf4f262cf5bb7310309ac834a059f09dd51bc5d0be0407cb3.png)  

For this example, we need to select or type `description`.

>:blue_book: As you can see there are specific tags for different platforms, such as Apple, Microsoft, Twitter, and Open Graph (og:) used by Facebook. For more information on each platform, check out the resources at the end of this document.

Place a `<HeadContent>` section, with a description meta tag, below `<PageTitle>` in all three files.

#### *Index.razor* HeadContent

```razor
<HeadContent>
    <meta name="description" content="Blazor SEO index page contains the Home main menu of the Blazor SEO demo application." />
</HeadContent>
```

#### *Counter.razor* HeadContent

```razor
<HeadContent>
    <meta name="description" content="Blazor SEO counter page contains a sample counter page in the Blazor SEO demo application." />
</HeadContent>
```

#### *FetchData.razor* HeadContent

```razor
<HeadContent>
    <meta name="description" content="Blazor SEO fetchdata page contains sample Weather Forecast data in the Blazor SEO demo application." />
</HeadContent>
```

Now, let's run the application and see the titles and meta tags in action.

![Title and Meta Tags](images/6bf044c1089ba36c633d7bfde0eb39da664fdc9b76da0155119c7721d2b38634.png)

Now, one important thing is to notice the title and meta tags, not only under the Elements tab in your browser's Dev Tools, as they will show up differently under the HTML source. So, to make sure, let's view the HTML source code instead.

Rick-click anywhere on the application, and click on `View page source`.

![View page source](images/e81ac1c08c56ec15778bea67baa25324e4a2acf1d5b1479d642dda1175c3eb59.png)  

You may notice that title and description do not show up:

![Missing Title and Description](images/d0bf8f0ab3bee090fbc09c7f8068153e41428aedb9359ed0bb5379902822aec9.png)  

That's because they are "buried" under the `<!--Blazor:...>` comment line below:

![<!--Blazor:...](images/efc92ee3bde84b3099d9e9799a6dcda84318d005c93cd4c364aad021e82f78ff.png)  

Scroll all the way to the right, and you will find the tags, in an uncommented section:

![Scroll to the right](images/8f702dd096bcc2203d76b58547d9f2a39f702fca76f564c7fbac5d517f9573e9.png)  

The formatting may change in the future, the current format is not a problem from web crawlers to find the tags.

>:blue_book: For more information about controlling the head content with `HeadContent` and how this works behind the scenes, refer to this document: [Control \<head> content in ASP.NET Core Blazor apps](https://docs.microsoft.com/en-us/aspnet/core/blazor/components/control-head-content?view=aspnetcore-6.0)

The "magic" that make this possible, is because a Blazor Server app with .NET 6.0 supports prerendering, and to do that, the `App` root component needs to be rendered before the `HeadOutlet`.

If you have a Blazor Server application that was upgraded from .NET 5.0 to .NET 6.0, you need to make a few tweaks to be able to render the `App` root component before the `HeadOutlet`. Let's do that next.

### SEO in a Blazor Server Application Converted from .NET 5.0 to .NET 6.0

Add a new Blazor Server application, but this time select .NET 5.0 as the target framework.

![Configure your new project](images/68ff7ad68d299df91e9eaf8a4969f7a7cc31f1d48a6f469dae5920b895b0d309.png)  

![Additional information](images/3e82a8cdececb5582193b4848c61e7d0a7a2ac8b80795b32b20a73846e276959.png)  

Double-click the project name `BlazorServerAppSEOWithNET5.0`, and change the TargetFramework from net5.0 to net6.0.

Build the application to restore NuGet packages.

An effective way to render the `App` root component before the `HeadOutlet` is to add a *_Layout.cshtml* file, and move some of the content of the *_host.cshtml* there.

Add a new *_Layout.cshtml* file under the *Pages* folder, and add the following code:

```html
@using Microsoft.AspNetCore.Components.Web
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Blazor Server App SEO with NET5.0</title>
    <base href="~/" />
    <link rel="stylesheet" href="css/bootstrap/bootstrap.min.css" />
    <link href="css/site.css" rel="stylesheet" />
    <link href="BlazorServerAppSEOWithNET5.0.styles.css" rel="stylesheet" />
    <component type="typeof(HeadOutlet)" render-mode="ServerPrerendered" />
</head>
<body>
    @RenderBody()

    <script src="_framework/blazor.server.js"></script>
</body>
</html>
```

Remove the code we moved to the *_Layout.cshtml* file from the *_host.cshtml* and make it look like this:

```html
@page "/"
@namespace BlazorServerAppSEOWithNET5._0.Pages
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers
@{
    Layout = "_Layout";
}

<component type="typeof(App)" render-mode="ServerPrerendered" />
```

That's all the pre-work needed, now we can use `<PageTitle>` and `<HeadContent>` as we did before.

Add a `<PageTitle>` with a title, and a `<HeadContent>` sections, with the title and a description meta tag in all three files.

#### *Index.razor* HeadContent

```razor
<PageTitle>Index</PageTitle>

<HeadContent>
    <meta name="description" content="Blazor SEO index page contains the Home main menu of the Blazor SEO demo application." />
</HeadContent>
```

#### *Counter.razor* HeadContent

```razor
<PageTitle>Counter</PageTitle>

<HeadContent>
    <meta name="description" content="Blazor SEO counter page contains a sample counter page in the Blazor SEO demo application." />
</HeadContent>
```

#### *FetchData.razor* HeadContent

```razor
<PageTitle>Weather forecast</PageTitle>

<HeadContent>
    <meta name="description" content="Blazor SEO fetchdata page contains sample Weather Forecast data in the Blazor SEO demo application." />
</HeadContent>
```

Set the `BlazorServerAppSEOWithNET5.0` project as the start-up project, and run the application.

As you can see, title and description tags show up correctly under the Elements tab:

![SEO in Blazor Server App](images/7cb7f78b914ae0bdbbe07543fb489170382cd46a3f9c8d326307837ed926ce5a.png)  

As well as under the page source:

![Tags under page source](images/cdc0bed7a25cbb43fe7b3adabde67533ebda6a56751f264d40620094f5f1c95c.png)  


## Summary

For more information about Blazor, check the links in the resources section below.

## Complete Code

The complete code for this demo can be found in the link below.

- <https://github.com/payini/BlazorSEO>

## Resources

| Resource Title                                      | Url                                                                                                                        |
| --------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| The .NET Show with Carl Franklin                    | <https://www.youtube.com/playlist?list=PL8h4jt35t1wgW_PqzZ9USrHvvnk8JMQy_>                                                 |
| Download .NET                                       | <https://dotnet.microsoft.com/en-us/download>                                                                              |
| Search Engine Optimization (SEO) Starter Guide      | <https://developers.google.com/search/docs/beginner/seo-starter-guide?hl=en&visit_id=637639370449073519-226133402&rd=1>    |
| Bing Webmaster Guidelines                           | <https://www.bing.com/webmasters/help/webmasters-guidelines-30fba23a>                                                      |
| Control \<head> content in ASP.NET Core Blazor apps | <https://docs.microsoft.com/en-us/aspnet/core/blazor/components/control-head-content?view=aspnetcore-6.0>                  |
| Apple Supported Meta Tags                           | https://developer.apple.com/library/archive/documentation/AppleApplications/Reference/SafariHTMLRef/Articles/MetaTags.html |

|Twitter Cards|<https://developer.twitter.com/en/docs/twitter-for-websites/cards/guides/getting-started>|
|https://developer.twitter.com/en/docs/twitter-for-websites/cards/guides/getting-started|https://ogp.me/|
