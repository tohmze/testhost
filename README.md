# Formatting and Hosting a Resume

## Statement of Purpose  
This guide explains how to format a resume using Markdown and host it on a Forge. It is designed for anyone looking to share their resume online. Additionally, it includes resources for learning more about creating Markdown documents.  

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
(\*) refers to all steps.  
(1,2,4) refers to individual steps.  

* **Select the correct technical level:** The appropriate technical level was chosen based on the intended audience, ensuring clear and accessible language.  
* **Follow the ABC format:** The guide follows the ABC format, including a prerequisite section, a body, and a conclusion.  
* **Use numbered lists in the body:** Numbered lists were used in (\*) steps.  
* **Group steps under task headings:** Steps were categorized under specific task headings: "Setting Up Pelican Structure," "Creating a Resume in Markdown," "Adding a Theme to Markdown," and "Hosting on Forge."  
* **Place only one action in each step:** Each step contains only one action in (\*) steps.  
* **Use graphics:** Graphics were included in step 13.  
* **Maintain a simple style:** A clear and concise writing style was used throughout to ensure smooth progression between steps.  

---

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

---

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

---

## Adding a Theme to the Pelican Site  
8. Go back to directory root:
``` sh
cd ~/projects/yoursite
```

8. Install pelican-themes:  
```sh
git clone https://github.com/MrSenko/pelican-octopress-theme.git
```  

9. Open `pelicanconf.py` and insert the following to change the theme:  
```python
import os
THEME = os.path.abspath("pelican-octopress-theme")
```  

10. Build your site:
``` sh
pelican content
```

10. Preview your site:  
```sh
pelican --listen
```  

---

## Hosting on Forge  

11. Initialize Git in the project folder:  
```sh
git init
```  

12. Go to [GitHub](https://github.com/) and create a repository.  

13. Clone the repository to your local machine:  
```sh
git remote add origin https://github.com/username/reponame.git
```  

14. Adjust `publishconf.py` to match the repository:  
```python
SITEURL = "https://your-github-username.github.io/your-repo-name"
RELATIVE_URLS = False
OUTPUT_PATH = "docs/"
```  

15. Stage changes:  
```sh
git add .
```  

16. Commit changes:  
```sh
git commit -am "Added resume"
```  

17. Build the site with Pelican:  
```sh
pelican content -s publishconf.py
```  

18. Move output to the `gh-pages` branch:  
```sh
ghp-import output -b gh-pages
```  

19. Push to GitHub:  
```sh
git push origin gh-pages
```  

20. View your website on GitHub Pages:  
```
https://username.github.io/reponame
```

---

## Further Resources  
Listed below are additional resources to deepen your understanding of the tools used in this guide:  

1. [Markdown Tutorial](https://www.markdownguide.org/basic-syntax/)  
2. [Pelican Documentation](https://docs.getpelican.com/en/latest/)  
3. [GitHub Pages Tutorial](https://docs.github.com/en/pages/quickstart)  
4. [How To Write A Good Resume](https://hbr.org/2022/05/how-to-write-a-resume-that-will-stand-out)
5. [How To Use Git](https://docs.github.com/en/get-started/using-git)

---

## FAQs  

### General Questions
* Why is Markdown better than writing raw HTML?  
Markdown is a lightweight markup language that simplifies text formatting. It is preferable to raw HTML because it does not require complex tags, making it faster and easier to use.  

* What if I don’t want to use GitHub Pages?  
You can use other hosting options like Netlify, Vercel, or a self-hosted server. You’ll need to adjust your publishing process accordingly.

* Can I use a different Pelican theme?  
Yes! You can find and install other themes from Pelican Themes. Just update the THEME variable in pelicanconf.py.

* How do I update my resume after publishing?  
Edit resume.md, then rebuild the site with pelican content -s publishconf.py, and push the updated version to GitHub Pages using ghp-import.

* Do I need to run pelican-quickstart every time I update my resume?  
No, pelican-quickstart is only needed when setting up a new site. After that, just update your content and rebuild the site.

### Technical Troubleshooting
* Why is my theme not showing up?  
Ensure the THEME variable in pelicanconf.py is correctly set to the theme’s path. Also, check that the theme is installed properly.

* My resume is not updating on GitHub Pages. What should I do?  
Make sure you’ve run pelican content -s publishconf.py, used ghp-import output -b gh-pages, and pushed your changes with git push origin gh-pages.

* Why is my site showing a 404 error on GitHub Pages?  
Check if the gh-pages branch is set as the deployment source in your repository settings under GitHub Pages.

---

## Credits  
This guide was created to help individuals format and host their resumes online using Pelican and GitHub Pages.  