---
title: Xamarin Forms (MVVM) ViewModel Binding
---

This example shows the process to bind a view to an external view model.

Binding the view to an view model.

Code
----

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ c#
public MainPage()
{
    InitializeComponent();
    BindingContext = new MainViewModel();
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

How do i pass the call to the view model when the page is visible?

Code
----

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ c#
protected override void OnAppearing()
{
    var bindingContext = BindingContext as FulfilmentViewModel;

    if (bindingContext != null)
        bindingContext.OnAppearing();

}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Implementing the View Model based on BaseViewModel

Code
----

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ c#
class FulfilmentViewModel: BaseViewModel
{
    public FulfilmentViewModel()
    {
        Title = "Welcome";
    }

    public void OnAppearing()
    {
        
    }
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~