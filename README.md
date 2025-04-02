# Cognition Motion & Neuroscience Lab Website

This repository contains the materials used for building the lab website for the Cognition, Motion & Neuroscience Lab led by Prof. Dr. Cristina Becchio at [Universitätsklinikum Hamburg-Eppendorf](https://uke.de)

The website is structured with a landing home page that consists of a banner image, an overview of the lab's research focus, active projects, and a link to the team profiles page. The main menu consists of the following:

- Research: A dedicated research page with more details on specific research lines and methodologies
- Team: Individual profiles of lab members
- Publications: A list of publications from the group
- Contact: A link to advertisements for active experiments, as well as contact details for the lab 

Most of this site should be fit for purpose without regular updating (although feedback is welcome and should be discussed in advance and assigned to a single individual). However, there are a number of features that will need to be updated more regularly, potentially by multiple users. These include: individual profiles, new publications, and experiment advertisements. 

## General procedure for updating the site

This site is generated using Hugo, which is a powerful tool for creating aesthetic and simple-to-navigate static websites without having to code a lot of complicated HTML, Javascript, or CSS. In theory, this is a very useful way of generating a website: you can do it in minutes by editing only a few files in this directory to add the content you want to display, and then uploading everything onto Github where Hugo and Netlify (the hosting service) will do the rest for you.

Of course, in practice this isn't always quite so neat. Because the building process is largely hidden behind the scenes, small errors in how you format your Markdown files can cause the entire site to crash with little evidence for what went wrong. 

Ideally, you should test the changes you want to make locally before committing them to Github so that you can be sure that the changes won't break everything and cause someone to have to send some very annoyed emails. To do this, you will need to be comfortable working with the command line and working with git. All you will need to do is clone the github repository to your local machine, [set up a local server](https://gohugo.io/commands/hugo_server/), and make your changes locally while checking how they affect the overall site (by navigating to the local server URL shown in the command line output, which is usually something like `localhost:1313` or similar). Then, once you've made your changes and checked that it hasn't ruined everything for ever, you can just commit the changes back to the main repository. It's so simple! Hey wait, why are you crying? No no, don't run away...

The good news is that there are only a few files or folders you should ever need to touch, and so long as you understand what needs to go in these places it should be very easy to keep on top of any changes. 

## Updating your individual profile

Each member of the lab has been given a personal profile on the site. These can be found in `./content/authors/` as separate folders. Cristina, as the PI, is the `admin/` folder, while everybody else's folder is named using their first initial and surname (e.g. NFoster, RVilla, OPansardi, etc.)

Within each folder you will find two files: an image file, which will be a headshot image used as your profile picture, and a Markdown file called `_index.md`. This file contains all of the information that will be displayed on your profile page, including your full name, links to social media and external sites like Google Scholar and ORCID, your experience and history, and a biography. Some important things to note:

- __Username:__ You will have to enter a username, and this must be the same name as the folder for your personal profile so that Hugo knows where to look for your information (the fact that it already has to be here in order to find this username is apparently immaterial; computers are stupid)
- __Socials:__ If you want to add any socials other than the ones other people already have, check out the available icons at [Font Awesome](https://fontawesome.com/v4/icons/) to see how you should call them (e.g. if you want to add a LinkedIn or a link to your podcast or whatever, see if they have a suitable icon there)
- __User group:__ You need to specify which user group you fall into so that the site knows how to sort you. Make sure to check the spelling and capitalisation so we don't end up with six different groups of 'Postdocs', 'Post-doc', 'postdoc', 'Post doc', 'POstdoctoral researcher', and who knows what else
- __Bio/description:__ This goes at the end of the document after the bullet-point list of specifications (known as the YAML header). This must go between two `---` identifiers to show the start and end points, and you should stick to writing this in Markdown unless you really know what you're doing. [Here's a cheat sheet for formatting Markdown](https://www.markdownguide.org/cheat-sheet/) if that helps 

## New publications

Fantastic news! This one's the one that is least likely to get messed up, which is fortunate. It's also the only type of content updating that won't require interfering with any Markdown! 

Adding a new publication should be relatively straightforward. The publication list is the menu leads to a page with an embedded bibliography hosted and generated by [BibBase](https://bibbase.org). This tool (which requires a free account - log in using the CMoN shared gmail) takes a `.bib` file and converts it into a flexible, sortable list of publications. Different parameters for displaying the bibliography can be set through BibBase by [adding customisation terms to the URL](https://bibbase.org/documentation) where the list is embedded.

As you might suspect, the publication list is embedded in the `./content/publications/` folder in the `_index.md` file using Javascript. You should only edit this file if you want to change the overall appearance of the publication list or direct it to a different bibliography (unwise)

The file that the publications page reads from is in the same folder and is called `bibliography.bib`. This is formatted in a standard BibTex format that you can easily export from any citation manager or from Google Scholar. **This is the file you will need to update when you add a new citation**. Simply add the citation in BibTex format to the bibliography file and BibBase should do the rest for you. 

So when you have a new paper coming out (congratulations), just add it directly to this file and relax. Nothing else to worry about. Sorry I couldn't figure out a way to automate this but honestly websites these days are so untrusting about you piping their content away to display on a different domain with unknown security certificates... :eyeroll: 

## Advertising experiments

Now this is where everything is going to go horribly wrong, I just know it. I'm sure it's a nice idea to be able to advertise our experiments so that people can sign up but I can already feel this feature watching me with all the ominous gravity of an iceberg sizing up a particularly tasty-looking 1912 ocean liner... 

Ah well, might as well give it a go.

On the contact page I've added a button that links to a page displaying our currently active experiments. When you are looking to recruit people, you can add an advertisement on the website to help direct traffic, provide information about the task, and provide details of how people can sign up. It's not as useful as having an actual Sona system for participant recruitment, but that would just make everything too easy, wouldn't it??

Experiments are listed in the folder `./content/experiments`, and each advert is assigned a different folder with a unique name (e.g. `riccardos-super-awesome-funtime-experiment/`). Within this folder, you need to have a Markdown file called `index.md`. As with all index files in this repository, this consists of YAML front matter, described below, and a Markdown-formatted text body that contains the description of the actual experiment.

Within the YAML content, you need:

- __Title:__ Give your experiment a short, descriptive title, preferably with some indication about the monetary rewards and time commitment they can expect
- __Authors:__ List the experimenters who are involved in the study. These names will appear at the top of the page under the title, and links to the individual profile pages will appear at the bottom so that participants can email you directly 
- __Draft status:__ If you don't want your experiment to appear in the list of ongoing experiments, set this to `draft: true` to hide it from the page. This will still allow people to navigate directly to the URL (e.g. by going to 'https://whatever-we-call-this-website.com/experiments/riccardos-super-awesome-funtime-experiment') but they won't be able to navigate to it from elsewhere

In the Markdown body, you should include:

- __Study description:__ A short description of the study and what the experimental task will be
- __Recruitment details:__ Inclusion and exclusion criteria 
- __Experiment details:__ Information about the timeslots and how participants should sign up. You can maybe link to a Doodle or Calendly here, or some other scheduling service that allows participants to pick a time

An example experiment (currently hidden with draft status) is available in `./content/experiments/example/`, including a cover photo. Feel free to duplicate the folder and edit it with your experiment's details, but please leave the example as it is so that we all have a template to refer back to.

# Theme information 

This website uses the [Hugo Research Group Theme](https://github.com/wowchemy/starter-hugo-research-group). Check out the website for this theme to learn more about the site structure as well as access tutorials, walkthroughs, and examples