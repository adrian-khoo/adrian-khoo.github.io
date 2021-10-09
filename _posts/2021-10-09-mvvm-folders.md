---
title: Xamarin Forms (MVVM) Folders
category: Xamarin
tags: [xamarin, mvvm]
---

The Model-View-ViewModel (MVVM) pattern helps to cleanly separate the business and presentation logic of an application from its user interface (UI). Maintaining a clean separation between application logic and the UI helps to address numerous development issues and can make an application easier to test, maintain, and evolve. It can also greatly improve code re-use opportunities and allows developers and UI designers to more easily collaborate when developing their respective parts of an app.

Quote from [Microsoft MVVM](<https://docs.microsoft.com/en-us/xamarin/xamarin-forms/enterprise-application-patterns/mvvm>)

We will organise our source code based on the following folders for easy management.

Fonts
------
Customised forts

Model
------
Data structure classes. Mainly structure classes for holding JSON objects from APIs.

Data
------
Data structure classes. Static singleton data objects. Such as user_data.

Services
------
Interfaces and implementation for dependency injection of services functions to view models. Such as navigation services which allows view models to navigate to other pages. Static class tools such as random string generator can be in this folder. 

Views
------
Consist of all the UI Pages (View - Xaml and CS) and its MVVM binding view model (CS).

