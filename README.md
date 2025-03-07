# Formatting and Hosting a Resume

## Statement of Purpose  
This guide walks you through the process of formatting a resume using Markdown and hosting it on Forge. It’s perfect for anyone who wants to share their resume online. You’ll also find helpful resources to dive deeper into creating Markdown documents.

## Prerequisites  
* Create an account on [GitHub](https://github.com/)  
* Install [Git](https://git-scm.com/)  
* Install [Python](https://www.python.org/)  
* Install Pelican with Markdown support:  
```sh
python -m pip install "pelican[markdown]"
```  
* Install GitHub Pages Import:  
```sh
python -m pip install ghp-import
```  

## Instructions  

* **Use Static Site Generators**: In the “Setting Up the Structure” section: Instead of using heavy tools like word processors or PDFs, static site generators make it easier and more efficient to build websites.
* **Version Control for Docs**: In the “Hosting” section: By using Git to store documentation alongside the project, updates are simple, and everyone can collaborate without hassle.
* **Minimalist and User-Centered Writing**: Throughout the documentation: The instructions are clear and to the point, focusing on what users actually need to do, with no unnecessary details to get in the way.
* **Automate Documentation Deployment**:In the “Hosting” section: Automation tools like CI/CD, ghp-import, and GitHub Pages handle deployment, keeping everything up to date without you having to do anything manually.
* **Keep Documentation Close to Code**  
  In the “Setting Up Pelican” sections: By storing the documentation in the same place as the project code, it’s much easier to keep everything in sync and make updates as needed.
* **Include Inline Examples**: In the “Project Setup” and “Customization” sections: Real-life examples are included to help clarify important concepts, making it easier to understand and follow the steps.


## Setting Up Pelican Structure  

1. Create a project directory:  
```sh
mkdir -p ~/projects/yoursite
```  

2. Open the project directory:  
```sh
cd ~/projects/yoursite
```  

3. Generate the Pelican structure:  
```sh
pelican-quickstart
```  

4. Answer the following prompts:  
__Note__: The following are placeholder values and can be changed.   
> **Where do you want to create your new website?** `[.]`  
> **What will be the title of this website?** `Panda Resume`  
> **Who will be the author of this website?** `Peter Panda`  
> **What will be the default language of this website?** `[en]`  
> **Do you want to specify a URL prefix?** (e.g., `https://example.com`) **(Y/n)** `n`  
> **Do you want to enable article pagination?** **(Y/n)**  
> **How many articles per page do you want?** `[10]`  
> **What is your time zone?** `[America/Winnipeg]`  
> **Do you want to generate a tasks.py/Makefile to automate generation and publishing?** **(Y/n)**  
> **Do you want to upload your website using FTP?** **(y/N)**  
> **Do you want to upload your website using SSH?** **(y/N)**  
> **Do you want to upload your website using Dropbox?** **(y/N)**  
> **Do you want to upload your website using S3?** **(y/N)**  
> **Do you want to upload your website using Rackspace Cloud Files?** **(y/N)**  
> **Do you want to upload your website using GitHub Pages?** **(y/N)**  


## Creating a Resume in Markdown  

5. Enter the content folder:  
```sh
cd content
```  

6. Create the resume Markdown file:  
```sh
touch resume.md
```  

7. Open the resume file and fill in the information:  
```
Title: My Resume
Date: 2025-03-05
Category: Work

# First Name Last Name
```

## Adding a Theme to the Pelican Site  
8. Go back to directory root:
``` sh
cd ~/projects/yoursite
```

9. Install pelican-themes:  
```sh
git clone https://github.com/MrSenko/pelican-octopress-theme.git
```  

10. Open `pelicanconf.py` and add these settings:  
```python
import os
THEME = os.path.abspath("pelican-octopress-theme")
```  

11. Build your site:
``` sh
pelican content
```

12. Preview your site:  
```sh
pelican --listen
```  


## Hosting on Forge  

13. Initialize Git in the project folder:  
```sh
git init
```  

14. Go to [GitHub](https://github.com/) and create a repository.  

15. Link repository to your local machine:  
```sh
git remote add origin https://github.com/username/reponame.git
```  

16. Open `publishconf.py` and add these settings:  
```python
SITEURL = "https://your-github-username.github.io/your-repo-name"
RELATIVE_URLS = False
OUTPUT_PATH = "docs/"
```  

17. Stage changes:  
```sh
git add .
```  

18. Commit changes:  
```sh
git commit -m "Added resume"
```  

19. Build the site with Pelican:  
```sh
pelican content -s publishconf.py
```  

20. Move output to the `gh-pages` branch:  
```sh
ghp-import output -b gh-pages
```  

21. Push to GitHub:  
```sh
git push origin gh-pages
```  

22. View your website on GitHub Pages:  
```
https://username.github.io/reponame
```


## Further Resources  
Listed below are additional resources to deepen your understanding of the tools used in this guide:  

1. [Markdown Tutorial](https://www.markdownguide.org/basic-syntax/)  
2. [Pelican Documentation](https://docs.getpelican.com/en/latest/)  
3. [GitHub Pages Tutorial](https://docs.github.com/en/pages/quickstart)  
4. [How To Write A Good Resume](https://hbr.org/2022/05/how-to-write-a-resume-that-will-stand-out)
5. [How To Use Git](https://docs.github.com/en/get-started/using-git)


## FAQs  

### General Questions
* Why is Markdown better than writing raw HTML?  
Markdown is a lightweight markup language that simplifies text formatting. It is preferable to raw HTML because it does not require complex tags, making it faster and easier to use.  

* What if I don’t want to use GitHub Pages?  
You can use other hosting options like Hugo, or a self-hosted server. You’ll need to adjust your publishing process accordingly.

* Can I use a different Pelican theme?  
Yes! You can find and install other themes from Pelican Themes. Just update the THEME variable in ```pelicanconf.py```.

* How do I update my resume after publishing?  
Edit resume.md, then rebuild the site with ```pelican content -s publishconf.py```, and push the updated version to GitHub Pages using ```ghp-import```.

* Do I need to run pelican-quickstart every time I update my resume?  
No, pelican-quickstart is only needed when setting up a new site. After that, just update your content and rebuild the site.

### Technical Troubleshooting
* Why is my theme not showing up?  
Ensure the THEME variable in ```pelicanconf.py``` is correctly set to the theme’s path. Also, check that the theme is installed properly.

* My resume is not updating on GitHub Pages. What should I do?  
Make sure you’ve run ```pelican content -s publishconf.py```, used ```ghp-import output -b gh-pages```, and pushed your changes with git push ```origin gh-pages```.

* Why is my site showing a 404 error on GitHub Pages?  
Check if the ```gh-pages``` branch is set as the deployment source in your repository settings under GitHub Pages.



## Credits  
**Wriiten by:** Oluwatomisin Bickersteth  
**Reviewed by:** Brett Loewen  
**Theme:**  [Octopress]()
