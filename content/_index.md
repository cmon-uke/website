---
# Leave the homepage title empty to use the site title
title: 
date: 2022-10-24
type: landing

sections:
  - block: hero
    content:
      title: "**Becchio Lab**<br />Cognition, Motion & Neuroscience"
      subtitle: Lab of Prof. Dr. Cristina Becchio, Department of Neurology UKE
    design:
      background:
        image:
          filename: welcome.png
        filters:
          brightness: 1
        parallax: false
        position: center
        size: cover
        #text_color_light: true
      spacing:
        position: fixed
        bottom: 100px
#        padding: ['0', '50px', '50px', '0']
      css_class: fullscreen
    advanced: 
      css_style: "width: 30vw; margin-left: 10vw !important; margin-top: 60vh !important;"
    
  - block: markdown
    content: 
      title: Our research
      subtitle: 
      text: 
        The Cognition, Motion and Neuroscience Laboratory at [University Medical Center Hamburg-Eppendorf](https://uke.de), investigates how movement encodes and transmits information about cognitive states, bridging the gap between behaviour, cognition, and neural activity. 



        Understanding other people’s mental states, such as their beliefs, intentions, or emotions, is a key skill for navigating our social environment; from anticipating what someone is going to do next, to interpreting communicative or social gestures, to deciding whether or not to collaborate with someone all rely on our ability to understand the inner mental states of other people. Research in our lab focuses on how information about mental states is conveyed through movement kinematics, and how observers read and parse this information to understand others’ minds. 



        The goal of our research programme is to develop new quantitative methods and use them for generating and testing new hypotheses about the mechanisms underlying the kinematic transmission of information, how these mechanisms develop, and how they can go awry in brain disorders. 



        [Read more about our research here](research)

  - block: collection
    content:
      title: Projects
      subtitle: A list of our current grants 
      text:
      count: 5
      filters:
        author: ''
        category: ''
        exclude_featured: false
        publication_type: ''
        tag: ''
      offset: 0
      order: desc
      page_type: project
    design:
      view: compact
      columns: '2'
  
  - block: markdown
    content:
      title: 
      subtitle:
      text: |
        {{% cta cta_link="./people/" cta_text="Meet the team →" %}}
    design:
      background:
        image:
          filename: uke.jpg
      columns: '1'
---
