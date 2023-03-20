# API .NET 6.0

## 1. Create new project
<ol type="a">
  <li>Open Visual Studio</li>
  <li>Create a new project</li>
  <li>Select ASP.NET Core Web API. A project template for creating an ASP.NET Core application with an example Controller for a RESTfull HTTP service. This template can also be used for ASP.NET Core MVC Views and Controller</li>
  <li>Input Project name "Main" and solution name "WebAPI"</li>
  <li>Delete WeatherForecast.cs and Controllers/WeatherForecastController.cs</li>
  <li>Add Models folder in solution folder</li>
  <li>Add new class in Models folder, name SuperHero</li>
  <li>Add new controller name SuperHeroController in Controllers folder</li>
</ol>

## 2. Models
```
// File: SuperHero.cs
namespace Main.Models
{
    public class SuperHero
    {
        public int Id { get; set; }
        public string Name { get; set; } = string.Empty;
        public string FirstName { get; set; } = string.Empty;
        public string LastName { get; set; } = string.Empty;
        public string Place { get; set; } = string.Empty;
    }
}
```
## 3. Controller


