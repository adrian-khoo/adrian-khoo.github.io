---
title: Xamarin Forms (MVVM) ViewModel Binding
---

This example shows the process to bind a view to an external view model.

1. Binding the view to an view model.

Code
----

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ c#
public MainPage()
{
    InitializeComponent();
    BindingContext = new MainViewModel();
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

2. How do i pass the call to the view model when the page is visible?

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

3. Implementing the View Model based on BaseViewModel

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