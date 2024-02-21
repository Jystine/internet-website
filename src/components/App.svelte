<script>
    import { onMount } from "svelte";
    import * as d3 from "d3";
    import Internet from "./internet.svelte";

    let data = [];

 onMount(async () => {
            const res = await fetch('cleaned_internet.csv'); 
            const csv = await res.text();
            data = d3.csvParse(csv, d3.autoType)
            console.log(data);
        });

</script>

<main>
  <h1>Internet Usage Increases Dramatically Since the Start of the Century!</h1>
  <p>The Internet was first invented back in 1983 and has since then become a staple in today's world with a lot of people using
    it on a daily basis. <br> <a href = "https://data.un.org/">UNdata </a>has recorded how much of a region's population uses the Internet during certain years. Let's see how Internet usage has changed
    <br>since the start of the 21st century.</p>
  <Internet {data} />
  <div class = "write-up">
  <h1 style = "text-align:center"><u>Write-Up</u></h1>
  <p>Our visualization shows the internet usage trend every 5 years from 2000 to 2020, using data sourced from UNdata. </p>
  <p>We started our project by exploring the vitality and effectiveness of different possible visualization techniques. We thought Choropleth and line charts would be most fitting to plot our data because our interested variables involved geographical location (i.e. world countries) and time series data (i.e. year of interest). We thought line charts would be easier to make than a world Choropleth, but  it would not be as effective in visualizing our data. We chose a Choropleth map with a slider scale of years as our main visualization technique over line charts because we wanted to show the viewers the geographical patterns of internet usage data over time. A trend emerged over a geographical map is identified mainly via perceptive work, rather than a group of line charts for countries as that will involve more cognitive work for the viewers to make sense of more meaningful patterns in the data. For example, viewers can quickly tell from the Choropleth representation of world internet usage in 2020 that Australia and North America countries like Canada and the United States have much more internet access than the rest of the world comparatively (due to the color contrast), though internet access could still be considered a luxury good at this time and age with most of the countries were still in the 0-20% range.</p>
  <p>We also employed other interaction techniques in our project, such as legend filtering and hovering tooltip. The hovering tooltip is included if a viewer is interested in knowing the exact percentage of internet usage of a country in a year. The legend filtering is also included because we think it highlights the internet usage data in a 20% range since it helps facilitate pattern recognition of countries in a particular range of some year by perceptive work rather than cognitive work. For example, if viewers are interested in knowing about countries with 80-100% internet usage, they have to observe the entire map carefully to locate the occurrence of the color corresponding with the 80-100% range (i.e. dark blue). If there were no countries with 80-100% internet usage, it also involves more cognitive process from the viewers to derive that logical conclusion from the absence of the corresponding color while some other colors of other ranges already filled in those same countries.</p>
  <p>Other visualization aspects like color scheme and data inclusion are also taken into account to avoid having any unwanted deceptive components and ensure maximization of transparency in our visualization. Our visualization omits the data of the year 2019 and 2021 because we used a time slider with equal distance between the ticks to display internet usage data over time by year and 2019 or 2021 does not share the same localized distance to adjacent years as other years. As for the color, we included a sequential blue scheme of 5 different shades of blue because blue is colorblindness-friendly, and having less than 6 different shades of the same color scheme provides enough contrast for our visualization to be effective.</p>
  <p>In our development process, we had a lot of roadblocks initially when we set up the project, but we made much faster progress afterwards. Most of the debug and struggles were at the beginning when we tried to set up the static representation of our data using only 2020 subsetted data. The data was loaded incorrectly, causing the rendering of the map to be abysmally slow and the data mapping result to be empty or undefined. Besides the huge hiccup of loading in data, we could mostly follow examples and make minor modifications to the code to make them work for our project. About 22 hours has been spent on this project.</p>
  <p>We worked together on all components to make this project a success, but one of us might have a larger share in the ground work of one component while the other revised, improved, or made suggestion upon. Specifically, Raine figured out a lot of base code for interactivity, while Han made the draft for the write-up component. All in all, shared workload is fair. </p>
</div>
</main>

<style>
    main {
        text-align: center;
        font-family: 'Open Sans', sans-serif;
    }
    .write-up {
      text-align:left;
      padding: 10px;
    }
</style>