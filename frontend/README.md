# Frontend Technical Specifications
- Create a static website that serves an HTML resume

## Resume Info
- Will need to update current resume with my new acquired skills from recent role + skils learned via this project. (Rolling adjustment throughout this project)

## Resume Format

- Resume should resemble a Modern resume template [Resume Template](https://docs.google.com/document/d/19JWIczqAohw7HQeR5TCEPCxdrukdWyvhovV-rLIP9ls/edit?tab=t.0)
- This is the top recommended for Tech industry per Gemini AI

- 2/26/26 Thought doing a interactive portfolio might work better! wondering if that is doable with HTML (we will find out)

## Resume Format Generation

Will need to figure out a way to format resmume to follow Resume Template via HTML. 
Can use AI to generate HTML , will edit to meet our preference

Prompt: 
Convert this resume format (zappywappy/cloud-resume-challenge/frontend/assets/resumetemplate.png) into HTML.
Do not use a CCS framework (decoration of the webpage)
Use least amount of css tags.

This is the generated HTML for the resume template [frontend/assets/02-24-26resume_template.html]

## HTML Adjustments
- grabbing pieces from generated HTML and placing them in a [new file](frontend/public/index.html)
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
- now i can begin styling the webpage, create a new folder in assets directory: "stylesheets"
- create file "style.css" in the stylesheets folder
- open the index.html and add <link> to reference the style.css file 

'''
    <link rel="stylesheet" href="frontend/assets/stylesheets/style.css">
'''    

- run a test to see if link worked, open style.css and type the following to change the background color

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
- refresh the local website and see if changes are made