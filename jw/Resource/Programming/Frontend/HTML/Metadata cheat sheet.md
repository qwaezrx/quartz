#Cheat-sheet 

## [[HTML]] `<meta>` tags

### Name
The name of the property can be anything, although browsers usually expect a value they understand and can take an action upon.
For example:
```html
<meta name="author" content="name">
```
### Content
The content field specifies the property's value.
For example:
```html
<meta name="language" content="english">
```
### Charset
The charset is a special field that lets you specify the character encoding used for the page.
```html
<meta charset="UTF-8">
```
### HTTP-equiv
This field stands for HTTP equivalent, and it's used to simulate HTTP response headers. This is rare to see, and it's recommended to use HTTP headers over HTML `http-equiv` meta tags. 
For example, the next tag would instruct the browser to refresh the page every 30 minutes:
```html
<meta http-equiv="refresh" content="30">
```
## Basic meta tags (meta tags For SEO)
```html
<meta name="description"/>
<!-- Provides a brief description of the page -->
<meta name="title"/>
<!-- Specifies the title of the web page -->
<meta name="author" content="jw">
<!-- Specifies the author of the web page -->
<meta name="language" content="english">
<!-- Specifies the language of the web page -->
<meta name="robots" content="index,follow" />
<!-- Tells search engines how to crawl or index a certain page -->
<meta name="google" />
<!-- Tells Google not to show the sitelinks search box for your page when showing search results -->
<meta name="googlebot" content="notranslate" />
<!-- Tells Google you don't want to provide an automatic translation for your page if the user uses a different language -->
<meta name="revised" content="Sunday, July 18th, 2010, 5:14 pm" />
<!-- Specifies the last modified data and time on which you have made certain changes -->
<meta name="rating" content="safe for kids">
<!-- Specifies the expected audience for your page -->
<meta name="copyright" content="Copyright 2022">
<!-- Specifies a Copyriht -->
```
## `<meta http-equiv="..."/>`  tags
```html
<meta http-equiv="content-type" content="text/html">
<!-- Specifies the format of the document returned by the server -->
<meta http-equiv="default-style" />
<!-- Specifies the format of the styling document -->
<meta http-equiv="refresh" />
<!-- Specifies the duration of the page before it's considered stale -->
<meat http-equiv="Content-language" />
<!-- Specifies the language of the page -->
<meta http-equiv="Cache-Control" content="no-cache">
<!-- Instructs the browser how to cache your page -->
```
## Responsive design/mobile meta tags
```html
<meta name="format-detection" content="telephone=yes"/>
<!-- Indicates that telephone numbers should appear as hypertext links that can be clicked to make a phone call -->
<meta name="HandheldFriendly" content="true" />
<!-- Specifies that the page can be properly visualized on mobile devices -->
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<!-- Specifies the area of the window in which web content can be seen -->
```

