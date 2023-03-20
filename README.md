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
In Get by id method, use NoCopntent() if not found<br>
In Put method, use NotFound("string") as an example<br>
In Delete method, use BadRequest("string") as an example

```
// File: Controllers/SuperHeroController.cs
using Main.Models;
using Microsoft.AspNetCore.Components.Web.Virtualization;
using Microsoft.AspNetCore.Http;
using Microsoft.AspNetCore.Mvc;

namespace Main.Controllers
{
    [Route("api/[controller]")]
    [ApiController]
    public class SuperHeroController : ControllerBase
    {
        private static List<SuperHero> heroes = new List<SuperHero>
            {
                new SuperHero
                {
                    Id = 1,
                    Name = "Spider Man",
                    FirstName = "Peter",
                    LastName = "Parker",
                    Place = "New York City"
                },
                new SuperHero
                {
                    Id = 2,
                    Name = "Ironman",
                    FirstName = "Tony",
                    LastName = "Stark",
                    Place = "Long Island"
                }
            };
        //====================================================================
        // Get whole list of SuperHero
        [HttpGet]
        public async Task<ActionResult<List<SuperHero>>> Get()
        {
            return Ok(heroes); // Ok: 200, BadRequest: 400, NotFound: 404
        }


        //====================================================================
        // Get superhero by Id
        // [HttpGet]
        // [Route("{id}")]
        [HttpGet("{id}")]
        public async Task<ActionResult<SuperHero>> Get(int id)
        {
            // var hero = heroes[id];
            var hero = heroes.Find(h => h.Id == id);
            if (hero == null)
            {
                return NoContent();
            }
            return Ok(hero); // Ok: 200, BadRequest: 400, NotFound: 404
        }


        //====================================================================
        [HttpPost]
        public async Task<ActionResult<List<SuperHero>>> AddHero(SuperHero hero)
        {
            heroes.Add(hero);
            return Ok(heroes); // Ok: 200, BadRequest: 400, NotFound: 404
        }


        //====================================================================
        [HttpPut]
        public async Task<ActionResult<SuperHero>> UpdateHero( SuperHero request)
        {
            var hero = heroes.Find(h => h.Id == request.Id);
            if (hero == null)
            {
                return NotFound("Hero is not found.");
            }

            hero.Name = request.Name;
            hero.FirstName = request.FirstName ;
            hero.LastName = request.LastName ;
            hero.Place = request.Place;
            return Ok(hero); // Ok: 200, BadRequest: 400, NotFound: 404
        }


        //====================================================================
        [HttpDelete("{id}")]
        public async Task<ActionResult<SuperHero>> Delete(int id)
        {
            var hero = heroes.Find(h => h.Id == id);
            if (hero == null)
            {
                return BadRequest("Hero is not found.");
            }
            heroes.Remove(hero);
            return Ok(heroes); // Ok: 200, BadRequest: 400, NotFound: 404
        }
    }
}

```


