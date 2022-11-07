---
layout: page
title: About
permalink: /about/
weight: 2
---

## **About Me**

Hello there! :wave:.

My name is **{{ site.author.name }}**. I am a Software Developer (:desktop_computer: and :iphone:) and a Data Science Generalist living in New Zealand. I am currently working as a **Product Owner & Analytics Specialist** at **Spark New Zealand** (Christchurch) :new_zealand: in the **AI & Engineering Tribe**. My current work is focused in the Telecom industry, helping to build cutting edge analytical and data science web applications in React, Python, and R Shiny.

I have a strong passion for technology. I blog mostly about Web development and Data Science in general. Python and R are my go to tools for exploratory data analysis (EDA), statistics and machine learning. I blog and pin them in chronological order in "Blog" tab. 

The toolset I use for most of my work is in - Python, FastAPI, R + R Shiny, Jupyter notebooks, SQL, Snowflake, NoSQL (MongoDB), React & NextJS, Git, Docker, Kubernetes, Azure, Azure DevOps, and PowerBI.

A list of my projects are under the Projects tab. You may also check out my GitHub profile.

To get a better insight on my career so far, check out my curriculum vitae (CV tab).

Feel free to read a bit more about me down below.

<div class="row">
<img src="../images/portfolio_banner.png" alt="portfolio_banner" />
</div>

<div class="row">
{% include about/skills.html title="Programming" source=site.data.programming-skills %}
{% include about/skills.html title="Data Science" source=site.data.ml-skills %}
{% include about/skills.html title="Other Skills" source=site.data.other-skills %}
</div>

<style>
hr.dotted {
    border-top: 2px dotted #999;
}
</style>

<div class="row">
    <div class="col-lg-12 mx-auto">
        <div class="mb-12">
            <h6 class=" text-uppercase"></h6>
            <hr class="dotted">
        </div>
    </div>
</div>

<div class="col-xs-12 center-block text-center">
    <h3>💼 Work Experience 💼</h3>
</div>

<div class="row">
    {% include about/timeline.html %}
</div>
