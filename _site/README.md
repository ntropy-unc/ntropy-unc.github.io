# ntropy-unc.github.io
The offical website of the UNC Chapel Hill CTF Team


### Adding a Write-Up
* To add a write up, you can use either html or github flavored markdown to format it  
* Name your file in the format
```
YYYY-MM-DD-NameOfFile-WriteUp.markdown
```
Example:
```
2017-10-14-Square-Writeup.markdown
```
* Before any content, make sure the top of your writeup post has this format:
```
---
layout: default
title:  "Title of writeup to be displayed on website in quotes"
date:   YYYY-MM-DD 
categories: jekyll update post writeup
---
```
* The lines with layout, categories and --- should remain the same. Change the title and date line accordinly
* Upload the file to the \_posts directory
* Create an appropriately named subdirectory within the img directory containing any images used




### Adding Presentation Materials
TBD

### Editing the website locally
Github pages run on jekyll
To edit the website locally and see changes in a browser:
1. Install Ruby
2. Install Bundler
3. Install Github's version of Jekyll:  
   create a Gemfile with the following:
```
source 'https://rubygems.org'
gem 'github-pages'
```
   Then run bundle install  

To run Jekyll use the command:
```
bundle exec jekyll serve
```
The rendered website should be located on http://localhost:4000  
