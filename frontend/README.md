# Frontend Technical Specifications
- Create a static website that serves an HTML resume

## Resume Info
- Will need to update current resume with my new acquired skills from recent role + skils learned via this project. (Rolling adjustment throughout this project)

## Resume Format

- Resume should resemble a Modern resume template [Resume Template](https://docs.google.com/document/d/19JWIczqAohw7HQeR5TCEPCxdrukdWyvhovV-rLIP9ls/edit?tab=t.0)
- This is the top recommended for Tech industry per Gemini AI

- 2/26/26 Thought doing a interactive portfolio might work better! wondering if that is doable with HTML (we will find out) https://www.rolind.me/#about


## Resume Format Generation

Will need to figure out a way to format resmume to follow Resume Template via HTML. 
Can use AI to generate HTML , will edit to meet our preference

Prompt: 
Convert this resume format (zappywappy/cloud-resume-challenge/frontend/assets/resumetemplate.png) into HTML.
Do not use a CCS framework (decoration of the webpage)
Use least amount of css tags.

This is the generated HTML for the resume template [frontend/assets/02-24-26resume_template.html]

## HTML Adjustments
- grabbing pieces from generated HTML and placing them in a [new file](public/index.html)
- 2/26/26 : completed foundation adjustments and also updated resume info. Will need to include project exp, certification completion, course completion

## Setting up HTTP to localize website

- first install Vim through extensions on the left menu. this will be used to use Visual Studio Code to visualize the website and begin styling to my prefrence.
- open a terminal by choosing the layouts in the top right
- enter the following command in the terminal:

    ```sh
        npm i http-server -g     <!-- this will install http-server using npm/node.js-->
    ```
Reference Documentation: https://www.npmjs.com/package/http-server

'''sh
    cd frontend <!-- this will open the frontend folder-->
    http-server <!-- since i am in the frontend folder, this will have the http-server run and serve as a public folder>
'''

- can access the http-server via browser by clicking on the Avaiable links via IP address. this currently shows whats in the public/index.html file

## Praciting styling the webpage and see how changes impact the visuals
- now i can begin styling the webpage, create a new folder in assets directory: "stylesheets"
- create file "style.css" in the stylesheets folder
- open the index.html and add <link> to reference the style.css file 

'''
    <link rel="stylesheet" href="frontend/assets/stylesheets/style.css">
'''    

- run a test to see if link worked, open style.css and type the following to change the background color

<!-- background color-->
'''
    html, body {
        background: rgb(0,255,255) <!-- this will change the color of the background to tourqouise/light blue-->
    }    
'''

- commit and push for changes to take effect
- received error

[2026-02-26T09:34:15.076Z]  "GET /frontend/assets/stylesheets/style.css" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/145.0.0.0 Safari/537.36"
[2026-02-26T09:34:15.076Z]  "GET /frontend/assets/stylesheets/style.css" Error (404): "Not found"

- removed "frontend/" to see if that made any change. prcoessed commit. 
- failed again. turns out "assets" folder needs to be in the "public" folder. moved folder, folder turned green sooo looks good? committed to verify if this worked
- refresh the local website and see if changes are made

- to view changes of css without committing, right-click > inspect > Network > check Disable Cache. Now i can make changes, refresh the webpage and changes will be in effect

<!-- enable border for webpage to keep consistent sizing throught the webpage-->
https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/box-sizing

'''
    {
    box-sizing: border-box;
    }


<!-- set margins for the header & headings to 0px. This aligns the headers & headings to the top left corner of the webpage. I also include color for the header and headings to see outcome for fun-->
[Outcome](public/assets/webpage_style1.png)

'''
header {
    width:200px;
    margin: 0px;
    padding: 0px;
    background: rgb(0,255,0);
}

h1,h2,h3,h4,h5 {
    width:100px;
    margin: 0px;
    padding: 0px;
    background: rgb(255,0,255);
}
'''

<!-- move the webpage to the center-->
[Outcome](public/assets/webpage_style1 copy.png)
https://css-tricks.com/snippets/css/a-guide-to-flexbox/


'''
    main {
        height: 100%;
        wedith: 100%;
        display: flex;
        flex-direction: column;
        align-items: center
    }
'''

<!-- creating border around the article to force the text to wrap. also adding color white-->
[Outcome](public/assets/webpage_articlecenter1.png)
'''
    article {
        width: 1200px;
        background: rgb(255,255,255)
    }


- need to format the webpage a bit better and change some of the data:
    - make name right in the center, with the job position below
    - remove street and zipcode, leave city and state on the next row
    - then move the email, linkedin, phone number onto another row. (maybe include github link aswell)


## Styling webpage to the template 

<!-- reminded myself i should follow the template as i am treating this as a request/initiative task-->
- reviewing the template html to see how to reach the same format

'''css
    main: 
    |remove| ALL (deleted)

    article:
    |remove| ALL (deleted)

    root: 
    |add| --ink:#1f2937; --muted:#6b7280; --accent:#2f66c6; --rule:#e5e7eb;
    |update| --accent: #013897 (previous color was too bright)

    body:
    |remove| background color
    |remove| padding
    |add| color:var(--ink); font:14px/1.45 Arial, Helvetica, sans-serif; (set font color to var from root, set font type)

    .page(class = page):
    |add| max-width:860px; margin:28px auto; padding:0 28px 28px; 
    |update| max-width: 1000px (previous value made the webpage a bit small)

    header:
    |remove| background color

    headings:
    |update| separate the headings as the name & position need differnet formats
    |remove| background color
    |add| [h1] font-size: 44px; letter-spacing: .2px; color: var(--accent);
    |add| [h2] font-size:18px; font-weight:600; color:#374151;

    .meta(class = meta):
    |add| margin:6px 0 14px; color:var(--muted);

    .meta a(<a href=xxx>)
    |add| color:inherit; text-decoration:none;

    .summary(class = summary):
    |add| margin:0 0 18px; color:#4b5563; max-width:760px;
    |update| max-width: 960px (previous value made the summary cut mid-screen)

    .section-title(class = section-title):
    |add|  margin:22px 0 10px; font-size:13px; color:var(--accent); letter-spacing:1px; text-transform:uppercase;

    .hr (line divider, right below the section-titles)
    |add| border:0; border-top:1px solid var(--rule); margin:8px 0 14px; 
    
    .job 
    margin:0 0 18px; 

    .row 
    |add| display:flex; justify-content:space-between; gap:18px; 

    .role  
    |add|font-weight:700; font-size:16px; color:#374151; 

    .date 
    |add|white-space:nowrap; color:#111827; 

    .company 
    |add| color:var(--muted); margin:2px 0 8px; 

    ul
    |add| margin:8px 0 0 18px; padding:0; 
    
    li 
    |add| margin:6px 0; color:#4b5563; 
    
    .edu 
    |add| margin:0; 
    
    .school
    |add| font-weight:700; font-size:16px; color:#374151; 
    
    .degree 
    |add| color:var(--muted); margin:2px 0 0; 
    
    .skills
    |add|margin:0; color:#4b5563; 
    
 .skills b
    |add| color:#374151; 
'''

'''html
    |remove| &nbsp;
    |add| &#x2022; (used as the dot between the address and contact info)
    |move| phone number before email address
    |update| added real phone number and location
'''
[Outcome](public/assets/webpage_reformatted_to_template.png)