---
layout: page
title: About
permalink: /about/
weight: 2
---

## **About Me**

Hello there! :wave:.

My name is **{{ site.author.name }}**. I am a Scientist (Data and Analytics) and a Software Developer (both :desktop_computer: and :iphone:) working at Institute of Environmental Science & Research (ESR) in Christchurch, New Zealand :new_zealand:. My work if focused around environment, public health and science.

I have a strong passion for technology. I blog mostly about Python, R, Django, Machine Learning, Computer Vision, Data Science, Software Development, Big Data and lot more. Python and R are my go to tools for exploratory data analysis (EDA), statistics and machine learning. I blog and pin them down here in chronological order. Feel free to read a bit more about me.

The toolset I use is quite an array of tech like Python, R, Jupyter notebooks, RShiny, SQL (SQL Server, Postgres, MySQL), NoSQL (MongoDB, LiteDB), Flask, Django, React JS, Git & GitHub, Docker, Kubernetes, Azure, Azure DevOps, PowerBI, Tableau for my day to day tasks and other workflows.

A list of my projects are under the Projects tab. You may also check out my GitHub profile.

To get a better insight on my career so far, check out my curriculum vitae.

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
