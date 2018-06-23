---

title: useCORSOnly for ID Service
description: An optional Boolean flag that controls how the browser requests resources from the Experience Cloud ID service
seo-title: useCORSOnly for Adobe Experience Cloud ID Service
seo-description: useCORSOnly is an optional Boolean flag that controls how the browser requests resources from the Experience Cloud ID service
short-title: useCORSOnly
doc-type: reference
audience: admin
index: true
translate: true
version: false
private-feature-pack: false
beta: false
redirect: false

---

<!--Meta Data Values

**Required Meta for search optimization and page data**

title: free text string

description: free text string

seo-title: free text string

seo-description: free text string

**Optional Meta for extended capabilities**

audience:
all (default), admin, developer, end-user
 
index: true (default), false
 
translate:
true (default), false
 
doc-type:
reference (default), tutorials

version:
false (default), Classic, Standard, 6.5, 6.4, 6.3, 6.2
 
private-feature-pack:
false (default), true
 
beta:
false (default), true
 
redirect:
false (default), pathname
-->

# useCORSOnly

An optional, Boolean flag that controls how the browser requests resources from the Experience Cloud ID service.

## Syntax: 

`useCORSOnly: true|false` (default is *false*.)

## Overview

When set to false, the browser performs resource checks with CORS or JSONP. However, the ID service always tries to request resources with CORS first. It reverts to JSONP on older browsers that do not support CORS. If you need to force the browser to use CORS only, set useCORSOnly:true in the Visitor.getInstance function call.

>[!IMPORTANT]
>Set `useCORSOnly: true` if you have strict security requirements. You should only enable this mode if you’re confident all of your visitors use browsers that support CORS. The user experience is unaffected by browsers that do not support CORS. However, browsers without CORS support cannot request resources or exchange data with the Adobe Experience Cloud.

## Code Sample

```javascript
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure

   //For CNAME support only. Exclude these variables if you're not using CNAME
   marketingCloudServer: "Insert tracking server here",
   marketingCloudServerSecure: "Insert secure tracking server here",

   //Function variable
   useCORSOnly: true
});
```