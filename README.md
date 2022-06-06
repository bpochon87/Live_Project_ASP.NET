# Live_Project

<h2 align="center">Vertigo Theatre website</h2>

![homepage.png](images/homepageVertigo.png)

<h2>Index</h2>
<ul>
  <li><a href="#intro">Description</a></li>
  <li><a href="#bs">Building Entities</a></li>
  <li><a href="#api">Converting a Picture for Storage</a></li>
  <li><a href="#ux"></a></li>
  <li><a href="#skills">In Finality: Skills</li>
</ul>



<h2 id="intro">Description</h2>
<p>As part of our curriculum, we were tasked with a two-week sprint where we had to implement certain functionality within the Vertigo Theatre . This was done with other students as my teammates and instructors as project managers. Working according to the Agile methodology and within the scrum framework, I completed several stories where I implemented the ability to CRUD a cast member.</p>

<p><strong>Technologies used by me were:</strong></p>
<ul>
  <li>Visual Studio</li>
  <li>Azure DevOps</li>
  <li>ASP.NET</li>
  <li>C#</li>
  <li>HTML</li>
  <li>CSS</li>
  <li>Razor syntax</li>
</ul>

<h2 id="bs">Building Entities</h2>
<p>Successful websites require simple CRUD functionality. One story had me creating and styling the 'Create' portion. Check out the code and screenshot.</p>

```
namespace TheatreCMS3.Areas.Prod.Models
{
    public class CastMember
    {
        // This will create PK using VS convention [className]Id
        public int CastMemberId { get; set; }
        public string Name { get; set; }
        public int? YearJoined { get; set; }
        public Placement MainRole { get; set; }
        public string Bio { get; set; }
        public Byte[] Photo { get; set; }
        public bool CurrentMember { get; set; }
        public string Character { get; set; }
        public Production CurrentProduction { get; set; }
        public int? CastYearLeft { get; set; }
        public int? DebutYear { get; set; }
    }

    // An enum is a user-defined value type used to represent a list of named integer constants.
    // Here, we're using it to give our 'Placement' property a list of roles.
    public enum Placement
    {
        Actor,
        Director,
        Technician,
        [Display(Name = "Stage Manager")]
        StageManager,
        Other
    }

    public enum Production
    {
        Wicked,
        Hamilton,
        // Using System.ComponentModel.DataAnnotations, we're able to output a UI-friendly display name.
        [Display(Name = "The Lion King")]
        TheLionKing,
        [Display(Name = "Les Miserables")]
        LesMiserables,
    }
}
```

![scrapedData.png](images/scrapedData.png)


<h2 id="api">Sourcing Data via an API</h2>
<p>Another story had me locating an API that would be suitable for my particular use and implementing it as a source of data. I brought in all data provided and then selected only certain parameters (name of trail, description, difficulty [if specified]) that I wanted to pass to my webpage. Check out the code and video.</p>

```
def trail_api(request):
    # API code from https://rapidapi.com/trailapi/api/trailapi/
    url = "https://trailapi-trailapi.p.rapidapi.com/trails/explore/"

    # Latitude and longitude required. 'per_page' and 'radius' optional.
    parameters = {"lat": "39", "lon": "-106", "per_page": "300", "radius": "100"}
    headers = {
        "X-RapidAPI-Host": "trailapi-trailapi.p.rapidapi.com",
        "X-RapidAPI-Key": "e3b28ce81fmshbcd98af11e9812dp1487c5jsnaf6f45c8d994"
    }
    response = requests.request("GET", url, headers=headers, params=parameters)
    json_response = response.json()

    # Empty lists to populate with data we want to pull from the API.
    trail_name_list = []
    trail_desc_list = []
    trail_city_list = []
    trail_difficulty_list = []

    # Populating all lists except 'trail_list'.
    for item in json_response['data']:
        trail_name_list.append(item['name'])
        trail_desc_list.append(item['description'])
        trail_city_list.append(item['city'])
        trail_difficulty_list.append(item['difficulty'])

    trail_list = zip(trail_name_list, trail_desc_list, trail_city_list, trail_difficulty_list)

    context = {'trail_list': trail_list}
    return render(request, 'MTB_Trails/trail_api.html', context)
```

https://user-images.githubusercontent.com/83652607/163685974-1b9bfa39-7bef-42be-8d77-abe1d7a1a5c4.mp4


<h2 id="ux">Video Showcasing UI and UX</h2>
<p>I was quite pleased to see how the website came together: the melded colors, the slick and straightforward interface. Please enjoy a quick video of the functionality and pages created within the Django framework.</p>

https://user-images.githubusercontent.com/83652607/163687482-6487c094-b23f-4123-ab4c-523008ec2681.mp4

<h2 id="skills">In Finality: Skills</h2>
<p>This project allowed me to further hone several skills. They include:</p>
<ul>
  <li>Coding <strong>C#</strong></li>
  <li>Coding <strong>CSS</strong></li>
  <li>Coding <strong>HTML</strong></li>
  <li>Coding Razor (.cshtml) syntax</li>
  <li>Working within the <strong>ASP.NET</strong> framework</li>
  <li>Working with an <strong>MVC</strong> architectural pattern</li>
  <li>Working with <strong>Azure DevOps</strong></li>
  <li>Working within the <strong>Scrum</strong> framework</li>
  <li>Working with the <strong>Agile</strong> methodology</li>
</ul>

<p>Overall, <strong>communication</strong> with project managers and co-workers was one of the master keys which led to a successful venture.</p>
<br>
<p>Thank you for your time.</p>




  
