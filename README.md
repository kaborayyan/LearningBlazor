# Blazor Web App
### Several files can be found
* `Program.cs` is the entry point for the app that starts the server and where you configure the app services and middleware.
* Inside the Components directory
    * `App.razor` is the root component for the app.
    * `Routes.razor` configures the Blazor router.
    * The `Pages` directory contains some example web pages for the app.
* `BlazorApp.csproj` defines the app project and its dependencies and can be viewed by double-clicking the BlazorApp project node in the Solution Explorer.
* The `launchSettings.json` file inside the `Properties` directory defines different profile settings for the local development environment. A port number is automatically assigned at project creation and saved on this file.

### Modifying a Component
* Component parameters are specified using attributes or child content, which allow you to set properties on the child component
* You can use the same component in two different pages in two different ways
* Any parametrized properties should be public
* To use any Compnent in another page all you have to do is write it like a tag `<Counter />`
* To use any parametrized property `<Counter IncrementAmount="7"/>`

### C# Expression Values
You can use the code like this.  
`<p role="status">Current count: @(currentCount)</p>`  
Or like this  
```C#
@if (currentCount > 3)
{
    <p>You win!</p>
}
// or
<ul>
    @foreach (var item in items)
    {
        <li>@item.Name</li>
    }
</ul>
```

### Event handlers
This can be done like this  
` @on{DOM EVENT}="{METHOD}`
```C#
<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>
// or as Lambda Expression
<button class="btn btn-primary" @onclick="() => currentCount++">Click me</button>
```
Event handler methods can take an event argument with information. You can access the value of an input element that changed, like this:
```C#
<input @onchange="InputChanged" />
<p>@message</p>

@code {
    string message = "";

    void InputChanged(ChangeEventArgs e)
    {
        message = (string)e.Value;
    }
}
```

### Data Binding
You can bind a UI element to a variable. It's a two way binding so when one changes, the other will change.  
It uses the `@bind` code like this
```C#
<input @bind="text" />
<button @onclick="() => text = string.Empty">Clear</button>
<p>@text</p>

@code {
    string text = "";
}
```

### Enable interactivity
To handle UI events from a component and to use data binding, the component must be interactive.  
This can be done through two methods
`@rendermode InteractiveServer` and `@rendermode InteractiveWebAssembly`
