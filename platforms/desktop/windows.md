# Langley Foxall Windows Apps

Whilst our windows application development is slightly more rare than the other platforms, we still have a set standard 
of development, built by our in-house specialists.

As a preference, our Windows applications are developed using C#.

### Universal Windows Platform (UWP)

The Universal Windows Platform is our windows platform of choice, allowing you to develop and build once for Desktop, 
Mobile, Xbox, Hololens and more.

We work mainly with C# for our logic layer, and build our views using XAML.

#### Things you should know

- The UWP Platform is only compatible on Windows 10, with Windows 8 having a similar framework called Windows RT.
- The UWP & WinRT platforms use .NET Core - as opposed to the full .NET Framework. For Windows 10 this has recently
extended to .NET Core 2.0, which added a lot of extra API's.

#### Design Patterns / Architecture

UWP favours the MVVM design pattern (Model, View, View-Model), for separation of the views, business logic and models.

To incorporate this, there are a number of MVVM Frameworks that are compatible with NuGet, but our framework of choice is
[MVVM Light (Libraries only)](https://www.nuget.org/packages/MvvmLightLibs/). We have chosen this framework because it 
isn't opinionated, whilst employing useful helpers and tools to build enterprise applications, such as dependency 
injection, dialog services and more.

This enables you to have more control over the structure and development of the projects, whilst speeding up the process
tenfold.

You can opt to use the full [MvvmLight Framework](https://www.nuget.org/packages/MvvmLight/) which offers more, but does
inflict stronger opinions on your code, and less flexibility.

#### Offline Databases

When building on the UWP, we choose to use SQLite as our mobile database - this is because it closely matches the syntax
 and structure of MSSQL databases - which is typically what you will be dealing with on the Microsoft stack.
 
#### Deployment

##### Continuous deployment

Whilst in development, you will want to easily and consistently push new versions out to the customer for review.
The easiest way of doing this is via an AdHoc service such as [HockeyApp](https://www.hockeyapp.net/). HockeyApp allows 
unregulated distribution of applications with minimal effort.

##### Final Deployment

When an application has been completed, Microsoft have a [way of distributing Line of Business (LOB)/B2B applications via 
the store](https://docs.microsoft.com/en-us/windows/uwp/publish/distribute-lob-apps-to-enterprises). This should be used 
once an application is in production, just as [VPP](https://developer.apple.com/programs/volume/b2b/) is for iOS 
applications.