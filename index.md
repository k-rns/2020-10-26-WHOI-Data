---
layout: workshop      # DON'T CHANGE THIS.
# More detailed instructions (including how to fill these variables for an
# online workshop) are available at
# https://carpentries.github.io/workshop-template/customization/index.html
venue: "Woods Hole Oceanographic Institution"        # brief name of the institution that hosts the workshop without address (e.g., "Euphoric State University")
address: "online"      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria"), videoconferencing URL, or 'online'
country: "us"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) for the institution that hosts the workshop
language: "en"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) for the
latitude: "41"        # decimal latitude of workshop venue (use https://www.latlong.net/)
longitude: "-70"       # decimal longitude of the workshop venue (use https://www.latlong.net)
humandate: "Oct 26 & 27, Nov 2 & 3, 2020"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "8:30AM to 12:30PM EDT"    # human-readable times for the workshop (e.g., "9:00 am - 4:30 pm")
startdate: 2020-10-26      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2020-11-03        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Amber York", "Karen Soenen"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: ["Stace Beaulieu","Audrey Mickle","Joe Futrelle","Arianna Krinos","Brett Longworth","Harriet Alexander","Svenja Ryan","Ivan Lima","Katy Abbot","Ryan Govostes","Stewart Jamieson"]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["adyork@whoi.edu","ksoenen@whoi.edu"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes:  # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document (e.g., https://pad.carpentries.org/2015-01-01-euphoria)
eventbrite:           # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
---

{% comment %} See instructions in the comments below for how to edit specific sections of this workshop template. {% endcomment %}

{% comment %}
HEADER

Edit the values in the block above to be appropriate for your workshop.
If the value is not 'true', 'false', 'null', or a number, please use
double quotation marks around the value, unless specified otherwise.
And run 'make workshop-check' *before* committing to make sure that changes are good.
{% endcomment %}


{% comment %}
8< ============= For a workshop delete from here =============
For a workshop please delete the following block until the next dashed-line


<div class="alert alert-danger">
This is the workshop template. Delete these lines and use it to
<a href="https://carpentries.github.io/workshop-template/customization/index.html">customize</a>
your own website. If you are running a self-organized workshop or have not put
in a workshop request yet, please also fill in
<a href="{{site.amy_site}}/forms/self-organised/">this workshop request form</a>
to let us know about your workshop and our administrator may contact you if we
need any extra information.
</div>
{% endcomment %}

{% comment %}
8< ============================= until here ==================
{% endcomment %}


{% comment %}
Check DC curriculum
{% endcomment %}

{% if site.carpentry == "dc" %}
{% unless site.curriculum == "dc-ecology" or site.curriculum == "dc-genomics" or site.curriculum == "dc-socsci" or site.curriculum == "dc-geospatial" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Data Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>dc-ecology</code>, <code>dc-genomics</code>, <code>dc-socsci</code>, or <code>dc-geospatial</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% comment %}
Check SWC curriculum
{% endcomment %}

{% if site.carpentry == "swc" %}
{% unless site.curriculum == "swc-inflammation" or site.curriculum == "swc-gapminder" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Software Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>swc-inflammation</code>, or <code>swc-gapminder</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% comment %}
EVENTBRITE

This block includes the Eventbrite registration widget if
'eventbrite' has been set in the header.  You can delete it if you
are not using Eventbrite, or leave it in, since it will not be
displayed if the 'eventbrite' field in the header is not set.
{% endcomment %}
{% if page.eventbrite %}
<strong>Some adblockers block the registration window. If you do not see the
  registration box below, please check your adblocker settings.</strong>
<iframe
  src="https://www.eventbrite.com/tickets-external?eid={{page.eventbrite}}&ref=etckt"
  frameborder="0"
  width="100%"
  height="280px"
  scrolling="auto">
</iframe>
{% endif %}


<h2 id="general">General Information</h2>

{% comment %}
INTRODUCTION

Edit the general explanatory paragraph below if you want to change
the pitch.

{% endcomment %}

{% comment %}
LOCATION

This block displays the address and links to maps showing directions
if the latitude and longitude of the workshop have been set.  You
can use https://itouchmap.com/latlong.html to find the lat/long of an
address.
{% endcomment %}
{% assign begin_address = page.address | slice: 0, 4 | downcase  %}
{% if page.address == "online" %}
{% assign online = "true_private" %}
{% elsif begin_address contains "http" %}
{% assign online = "true_public" %}
{% else %}
{% assign online = "false" %}
{% endif %}
{% if page.latitude and page.longitude and online == "false" %}
<p id="where">
  <strong>Where:</strong>
  {{page.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latitude}}&mlon={{page.longitude}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latitude}},{{page.longitude}}">Google Maps</a>.
</p>
{% elsif online == "true_public" %}
<p id="where">
  <strong>Where:</strong>
  online at <a href="{{page.address}}">{{page.address}}</a>.
  If you need a password or other information to access the training,
  the instructor will pass it on to you before the workshop.
</p>
{% elsif online == "true_private" %}
<p id="where">
  <strong>Where:</strong> This training will take place online.
  The instructors will provide you with the information you will need to connect to this meeting.
</p>
{% endif %}

{% comment %}
DATE

This block displays the date and links to Google Calendar.

{% if page.humandate %}
<p id="when">
  <strong>When:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% endcomment %}
{% comment %}
AUDIENCE

Explain who your audience is.  (In particular, tell readers if the
workshop is only open to people from a particular institution.

{% endcomment %}


<p id="audience">
  <strong>Audience:</strong>
This workshop is targeted towards the technical WHOI staff in order to improve project efficiency and build technical skills. It will only be held for 20 people at a time through an online Zoom meeting. Registration is required. Please contact stace@whoi.edu for availability. 
</p>

<p id="prerequisites">
  <strong>Prerequisites:</strong>
To get the most out of this workshop we suggest that participants are already using python for data analysis at a novice or intermediate level.  A strong familiarity with Python syntax and basic constructs such as loops, lists and conditionals (i.e. if statements) is required. Python skills covered will progress from novice to intermediate over the course of the workshop.
</p>

<p id="when">
  <strong>When:</strong> Four half-day, morning workshops on Mondays and Tuesdays. October 26th and 27th, November 2nd and 3rd.  Each day will start at 8:30AM and finish at 12:30PM.  Breaks will be included in the schedule.
</p>

{% comment %}

SPECIAL REQUIREMENTS

Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>Requirements:</strong> Participants must bring a laptop with a
  Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on. They should have a few specific software packages installed (listed <a href="#setup">below</a>).
</p>

{% comment %}
ACCESSIBILITY

Modify the block below if there are any barriers to accessibility or
special instructions.
{% endcomment %}
<p id="accessibility">
  <strong>Accessibility:</strong>
{% if online == "false" %}
  We are committed to making this workshop
  accessible to everybody. The workshop organizers have checked that:
</p>
<ul>
  <li>The room is wheelchair / scooter accessible.</li>
  <li>Accessible restrooms are available.</li>
</ul>
<p>
  Materials will be provided in advance of the workshop and
  large-print handouts are available if needed by notifying the
  organizers in advance.  If we can help making learning easier for
  you (e.g. sign-language interpreters, lactation facilities) please
  get in touch (using contact details below) and we will
  attempt to provide them.
{% else %}
  We are dedicated to providing a positive and accessible learning environment for all. Please
  notify the instructors in advance of the workshop if you require any accommodations or if there is
  anything we can do to make this workshop more accessible to you.
</p>
{% endif %}

{% comment %}
CONTACT EMAIL ADDRESS

Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Contact:</strong>
  Please email
  {% if page.email %}
  {% for email in page.email %}
  {% if forloop.last and page.email.size > 1 %}
  or
  {% else %}
  {% unless forloop.first %}
  ,
  {% endunless %}
  {% endif %}
  <a href='mailto:{{email}}'>{{email}}</a>
  {% endfor %}
  {% else %}
  to-be-announced
  {% endif %}
  for more information.
</p>

{% comment %}
<p id="roles">
  <strong>Roles:</strong>
  To learn more about the roles at the workshop (who will be doing what),
  refer to <a href="https://carpentries.org/workshop_faq/#what-are-the-roles-of-everyone-participating-in-a-workshop">our Workshop FAQ</a>.
</p>
{% endcomment %}

{% comment %}
WHO CAN ATTEND?

If you would like to specify who can attend the workshop,
you can use the section below.

Move the 'endcomment' tag above the beginning of the following
<p> tag to make this section visible.

Edit the text to match who can attend the workshop. For instance:
- This workshop is open to affiliates to ABC university.
- This workshop is open to the public.
- If you are interested in attending this workshop, contact me@example.com
  for more information

<p id="who-can-attend">
    <strong>Who can attend?:</strong>
    This workshop is open to ....
</p>
{% endcomment %}


<p id="sponsorship">
<strong>Workshop sponsorship: </strong> DDVPR Technical Staff Training Award
</p>

<hr/>

<h2 id="why">Why take this course? </h2>

<strong>We\'ll cover:</strong>
<ul>
  <li>Managing tabular data for analysis and reproducibility</li>
  <li>Improving python skills for data analysis, and visualisation, both for tabular and grdided data</li>
  <li>Introducing collaboration and versioning using github and jupyter notebooks.</li>
</ul>

<p>
<strong>Managing tabular data for analysis and reproducibility.</strong>
</p>

<p>
Good data organization is the foundation of any research project. Most researchers have data in spreadsheets, so it’s the place that many research projects start. 
</p>

<p>
We organize data in spreadsheets in the ways that we as humans want to work with the data, but computers require that data be organized in particular ways. In order to use       tools that make computation more efficient, such as programming languages like R or Python, we need to structure our data the way that computers need the data. Since this is where most research projects start, this is where we want to start too!  The concepts learned here also apply more broadly to other tabular formats (e.g. csv and tsv).
</p>

<p>
In this lesson, you will learn:
<ul>
  <li>Good data entry practices - formatting data tables in spreadsheets</li>
  <li>How to avoid common formatting mistakes</li>
  <li>Approaches for handling dates in spreadsheets</li>
  <li>Basic quality control and data manipulation in spreadsheets</li>
  <li>Exporting data from spreadsheets</li>
</ul>  
</p>


<strong>Improving python skills for data analysis and visualization.</strong>

<p>
Python is rapidly emerging as the programming language of choice for data  analysis in the atmosphere and ocean sciences. By consulting online tutorials and help pages, most researchers in this community are able to pick up the basic syntax and programming constructs (e.g. loops, lists and conditionals). This self-taught knowledge is sufficient to get work done, but it often involves spending hours to do things that should take minutes, reinventing a lot of wheels, and a nagging uncertainty at the end of it all regarding the reliability and reproducibility of the results. To help address these issues, these Data Carpentry lessons cover a suite of programming and data management best practices that aren’t so easy to glean from a quick Google search.
</p>

<strong>Introducing collaboration and versioning using github and jupyter notebooks.</strong>

<p>
We will be taking this to a next level, introducing tools to increase collaboration, ensure code provenance and lower mistakes with documentation, and use versioning to not save a thousand copies of your code.
</p>


<hr/>

<h2 id="about-data-carpentries">About Data Carpentries</h2>
<p><a href="https://datacarpentry.org/">Data Carpentry</a> develops and teaches workshops on the fundamental data skills needed to conduct research. Its lessons are domain specific, building on learners' existing knowledge to enable them to quickly apply skills learned to their own research. Participants will be encouraged to help one another and to apply what they have learned to their own research problems.
</p>

<p>
For more information on what we teach and why, please see our paper "<a href="http://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005510">Good Enough Practices for Scientific Computing</a>".
</p>

<hr/>

{% comment%}
CODE OF CONDUCT
{% endcomment %}
<h2 id="code-of-conduct">Code of Conduct</h2>

<p>
Everyone who participates in Carpentries activities is required to conform to the <a href="https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html">Code of Conduct</a>. This document also outlines how to report an incident if needed.
</p>

<p class="text-center">
  <a href="https://goo.gl/forms/KoUfO53Za3apOuOK2">
    <button type="button" class="btn btn-info">Report a Code of Conduct Incident</button>
  </a>
</p>
<hr/>


{% comment %}
Collaborative Notes

If you want to use an Etherpad, go to

https://pad.carpentries.org/YYYY-MM-DD-site

where 'YYYY-MM-DD-site' is the identifier for your workshop,
e.g., '2015-06-10-esu'.

Note we also have a CodiMD (the open-source version of HackMD)
available at https://codimd.carpentries.org
{% endcomment %}
{% if page.collaborative_notes %}
<h2 id="collaborative_notes">Collaborative Notes</h2>

<p>
We will use this <a href="{{ page.collaborative_notes }}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
<hr/>
{% endif %}


{% comment %}
SURVEYS - DO NOT EDIT SURVEY LINKS
{% endcomment %}
<h2 id="surveys">Surveys</h2>
<p>Please be sure to complete these surveys before and after the workshop.</p>
<p><a href="{{ site.pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>

<hr/>


{% comment %}
SCHEDULE

Show the workshop's schedule.  Edit the items and times in the table
to match your plans.  You may also want to change 'Day 1' and 'Day
2' to be actual dates or days of the week.

<h2 id="schedule">Schedule</h2>

{% if site.carpentry == "swc" %}
{% include swc/schedule.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/schedule.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/schedule.html %}
{% endif %}

<hr/>
{% endcomment %}

<h2 id="schedule">Syllabus</h2>

This workshop is based on a few workshops developed by the Carpentries (See <a href="https://carpentries.org">https://carpentries.org</a>  for more information about the Carpentries organisation.) 
<ul>
  <li><a href=" https://datacarpentry.org/spreadsheet-ecology-lesson/">Data Organization in Spreadsheets for Ecologists</a></li>
  <li><a href="https://datacarpentry.org/python-ecology-lesson/">Data Analysis and Visualization for Ecologists</a></li>
  <li><a href="https://carpentrieslab.github.io/python-aos-lesson/">Python for atmosphere and ocean scientists</a></li>
</ul>

<br>


{% include dc/schedule_oswn.html %} 

{% comment %}    

Show what topics will be covered.

1. If your workshop is R rather than Python, remove the comment
around that section and put a comment around the Python section.
2. Some workshops will delete SQL.
3. Please make sure the list of topics is synchronized with what you
intend to teach.
4. You may need to move the div's with class="col-md-6" around inside
the div's with class="row" to balance the multi-column layout.

This is one of the places where people frequently make mistakes, so
please preview your site before committing, and make sure to run
'tools/check' as well.

<h2 id="syllabus">Syllabus</h2>

{% if site.carpentry == "swc" %}
{% include swc/syllabus.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/syllabus.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/syllabus.html %}
{% endif %}

<hr/>
{% endcomment %}


{% comment %}
SETUP

Delete irrelevant sections from the setup instructions.  Each
section is inside a 'div' without any classes to make the beginning
and end easier to find.

This is the other place where people frequently make mistakes, so
please preview your site before committing, and make sure to run
'tools/check' as well.
{% endcomment %}

<h2 id="setup">Setup for Week 1 (Days 1 and 2)</h2>

<p>
  To participate in a
  {% if site.carpentry == "swc" %}
  Software Carpentry
  {% elsif site.carpentry == "dc" %}
  Data Carpentry
  {% elsif site.carpentry == "lc" %}
  Library Carpentry
  {% endif %}
  workshop, you will need access to the software described below (Zoom, Python, Jupyter notebooks). In addition you will need an up-to-date web browser and access access to a spreadsheet program (Excel, LibreOffice,...),
</p>

<p>
  We maintain a list of common issues that occur during installation as a reference for instructors that may be useful on the <a href = "{{site.swc_github}}/workshop-template/wiki/Configuration-Problems-and-Solutions">Configuration Problems and Solutions wiki page</a>.
</p>

{% comment %}
For online workshops, the section below provides:
- installation instructions for the Zoom client
- recommendations for setting up Learners' workspace so they can follow along
  the instructions and the videoconferencing

If you do not use Zoom for your online workshop, edit the file
`_includes/install_instructions/videoconferencing.html`
to include the relevant installation instrucctions.
{% endcomment %}

{% if online != "false" %}
{% include install_instructions/videoconferencing.html %}
{% endif %}

{% comment %}
These are the installation instructions for the tools used
during the workshop.
{% endcomment %}

{% if site.carpentry == "swc" %}
{% include swc/setup.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/setup.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/setup.html %}
{% endif %}

{% include install_instructions/python.html %}

<h2>Setup for Week 2 (Days 3 and 4)</h2>

{% include install_instructions/shell.html %}
{% include install_instructions/git.html %}

<h3>Installing required packages</h3>

<p>For the workshop we recommend installing the required packages using the Anaconda Prompt in windows (or Terminal in Mac/Linux) as described in method 1 (below). If you try method 2 and that does not work for you, you can try method 1 at any time since it uses a separate environment we create just for this lesson.</p>
<div id="install-method-1">
  <strong>Install method 1: Make a new environment and launch jupyter notebooks using the new environment.</strong>
  <p>This method is more fail-safe than method 2.   As shown in the steps below you have to use a command line (Anaconda Prompt(win) Terminal(Mac/Linux) to launch jupyter notebook, not the graphical Anaconda Navigator.</p>
  <strong>Steps</strong>
  <ol>
    <li>Open Anaconda Prompt (Windows) or Terminal(Mac/Linux)</li>
    <li><p>Enter the following command to create a new environment called "pyaos-lesson"</p>
       <pre><code>conda create -n pyaos-lesson -c conda-forge jupyter xarray netCDF4 cartopy cmocean cmdline_provenance plotnine</code></pre>
    <li>
        <p>You will be asked if you would like to install the packages after they are found.  Press Yes (y).</p>
        <p>You should see messages for Preparing, Verifying, and Executing the "transaction" and end with a line that says "done"</p>
    </li>
    <li>
        <p>Enter the new environment you created.  After this command you should see "(pyaos-lesson)" at the start of your line.</p>
        <pre><code>conda activate pyaos-lesson</code></pre>
    </li>
    <li>
        <p>Launch the jupyter notebook with the following command. A new browser window should pop up with jupyter notebook in it.</p>
        <pre><code>jupyter notebook</code></pre></li>
    <li>Test your installs worked. See "Testing Your Installs" section Below.</li>
  </ol>
</div>

<div id="install-method-2">
    <strong>Install Method 2: Using the base environment</strong>
    <p>This method may be quite slow for some people and you may encounter more issues than method 1. But if you have completed your installs with this method and your test works then you are all set for the worksohp (See "Testing Your Installs" section Below).</p>

    <strong>Steps</strong>
    <ol>
      <li>Enter <code>conda activate base</code> and press enter to execute. This makes sure you are in your base environment. It won't hurt anything if you already are in base and run it anyway.  You should see "(base)" at the beginning of your line.</li>
      <li>
      Run the following commands one at a time.  It may take a few minutes to respond during this process.  You will be asked if you would like to install the packages after they are found.  Press Yes (y)
    <p><code>conda install jupyter xarray netCDF4 cartopy</code></p>
    <p><code>conda install -c conda-forge cmocean cmdline_provenance plotnine</code></p>
    <p>You should see messages for Preparing, Verifying, and Executing the "transaction" and end with a line that says "done"</p>
      </li>
      <li>Launch the jupyter nootebook using either Anaconda Navigator or command line using Anaconda Prompt(Windows) or Terminal(Mac/Linux).</li>
      <li>Test your installs worked. See "Testing Your Installs" section Below.</li>
    </ol>
</div>
  
<h3>Testing your installs</h3>
<p>To check your install was successful and you can use the packages within a notebook, you can enter the following into a jupyter notebook cell and run it. You should be able to execute the cell without an error.  It may take a few seconds then will show you "Hello World!" after the cell.


<pre><code>import xarray as xr
import cartopy.crs as ccrs
import matplotlib.pyplot as plt
import numpy as np
import cmocean
import cmdline_provenance as cmdprov
import plotnine as p9
import pandas as pd
print("Hello World!")
</code></pre>
 
<a href="fig/test_installs.png"><img src="fig/test_installs.png" alt="testing-installs" width="800"></a>


  <h3>Launching Jupyter Notebook</h3>
  <p>*if you have just followed the instructions to install packages and test them, you already have launched jupyter notebook and can use that.  You can follow these instructions if you don't already have a notebook running.</p>
  <strong>Steps</strong>
  <ol>
    <li> Open an Anaconda Prompt(Win) or Terminal(Mac/Linux) and type the command "jupyter notebook". </li>
    <li><p>Enter the environment wish to use.  After this command you should see the environment name "(pyaos-lesson)"  or "base" at the start of your line.</p>
      <div><p>If you installed your packages using method 1:</p>
            <pre><code>conda activate pyaos-lesson</code></pre>
     </div>
      <div><p>If you installed your packages using method 2:</p>
        <pre><code>conda activate base</code></pre> 
        
     </div>
    </li>
    <li><p>Launch the jupyter notebook with the following command. A new browser window should pop up right into your notebook.</p>
     <pre><code>jupyter notebook</code></pre>
     <p>A browser window will open with your notebook in it. If you close the page and need to get back to it, you can copy and paste the link shown in your Anaconda Prompt/Terminal.  Or you can try the default address <a href="http://localhost:8888/">http://localhost:8888/</a>.
     </li>
  
  </ol>
  
<p>For a brief introduction to Jupyter Notebooks, please consult our <a href="https://datacarpentry.org/python-ecology-lesson/jupyter_notebooks/">Introduction to Jupyter Notebooks</a> page. If you installed your required packages using method 2, you can also launch jupyter notebook using the Anaconda Navigator (instead of command line) as shown in that lesson.</p>


<h3>Data</h3>

<p>In preparation for these lessons,you will need to download the following two Python scripts and four netCDF files
and place them in a new folder/directory:</p>

<ol>
  <li>Make a new folder in your Desktop called `data-carpentry` if you haven't already.</li>
  <li>Download <a href="https://carpentrieslab.github.io/python-aos-lesson/code/script_template.py">script_template.py</a> and <a href="https://carpentrieslab.github.io/python-aos-lesson/code/plot_precipitation_climatology.py">plot_precipitation_climatology.py</a> and move them into that folder.</li>
  <li>Make a new folder in your `data-carpentry` folder called `data` if you haven't already.</li>
  <li>Download the following files and place them in that folder:</li>
   <ul>
     <li><a href="https://carpentrieslab.github.io/python-aos-lesson/data/pr_Amon_ACCESS1-3_historical_r1i1p1_200101-200512.nc">pr_access_file</a></li>
     <li><a href="https://carpentrieslab.github.io/python-aos-lesson/data/pr_Amon_CSIRO-Mk3-6-0_historical_r1i1p1_200101-200512.nc">pr_csiro_file</a></li>
     <li><a href="https://carpentrieslab.github.io/python-aos-lesson/data/sftlf_fx_ACCESS1-3_historical_r0i0p0.nc">sftlf_access_file</a></li>
     <li><a href="https://carpentrieslab.github.io/python-aos-lesson/data/sftlf_fx_CSIRO-Mk3-6-0_historical_r0i0p0.nc">sftlf_csiro_file</a></li>
  </ul>
</ol>



