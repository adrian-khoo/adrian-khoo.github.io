---
title: Xamarin Forms (MVVM) Dependency Services
---

In this example, we will use dependency injection to implement a service object for UI navigation from the view model. This allows view models to invoke shared functionality.

The interface. The interface provides the registration to reference the NavigationService object.

Code
----

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ c#
public interface INavigationService
{
    Task routeToBack();
    Task routeToForgetPassword(string userid);
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Implement the interface.

Code
----

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ c#
class NavigationService : INavigationService
{
    async public Task routeToBack()
    {
        await App.Current.MainPage.Navigation.PopAsync();
    }

    async public Task routeToForgetPassword(string userid)
    {
        await App.Current.MainPage.Navigation.PushAsync(new ForgetPasswordPage(userid));
    }
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

First of all, register the dependency service from the main App().

Code
----

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ c#
public App()
{
    InitializeComponent();

    DependencyService.Register<IMessageService, MessageService>();
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

4. From the view model, resolve the dependency service, and invoke them.

Code
----

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ c#
class FulfilmentViewModel: BaseViewModel
{
    private readonly Services.INavigationService _navigationService;

    public FulfilmentViewModel()
    {
        this._navigationService = DependencyService.Get<Services.INavigationService>();

        Title = "Welcome";
    }

    public void OnAppearing()
    {
        
    }

    private async void OnBackButtonClicked(object obj)
    {
        await _navigationService.routeToBack();
    } 
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
