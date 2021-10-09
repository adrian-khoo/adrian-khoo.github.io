---
title: Xamarin Forms (MVVM) Message Service
category: Xamarin
tags: [xamarin, mvvm, code]
---

This code display alert and actionsheet for Message Service.

Interface

Code
----

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ c#
public interface IMessageService
{
   Task ShowAsync(string message);
    Task<string> ShowActionSheet(string title, string cancel, string destruction = null, string[] buttons = null);
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Implementation

Code
----

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ c#
public class MessageService : IMessageService
{
    async Task IMessageService.ShowAsync(string message)
    {
        await App.Current.MainPage.DisplayAlert("Message", message, "Ok");
    }

    async Task<string> IMessageService.ShowActionSheet(string title, string cancel, string destruction, string[] buttons)
    {
        var displayButtons = buttons ?? new string[] { };
        var action = await App.Current.MainPage.DisplayActionSheet(title, cancel, destruction, displayButtons);
        return action;
    }
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
