# Blog
This is just a blog.  
I'm sorry, as this is own diary, so nobody commit anything into this project.  
If you have some time and be interested in this blog, please go the blog from the below URL:smiley:  
https://fukugit.github.io/blog/

## Getting Started
This project can be ran on local environment. Run the below command to work it.  

### Prerequisites
This project is consisted of Hugo, so it is necessary to install it first.  
1. `brew install hugo`  

### Installing
1. `git clone https://github.com/fukugit/blog.git`  

2. `cd blog/themes/`  

3. `git submodule add https://github.com/fukugit/github-style.git github-style`

4. `cd ./github-style`  

5. `git submodule update --init --recursive`  

6. `git checkout develop`  

## Running
1. `cd blog`  

2. `hugo server --ignoreCache`  

3. Open `http://localhost:1313/blog/` with your browser.  

## Writing blog
### Add new page
Copy the `2019-12-07.md`, and paste it into the same folder then rename.  

### Update header
Changes part of header in the coped markdown file.  
Be careful, the `draft` part, it should be kept `false`. If you change it to `true`,
 the blog will not be appeared, even if whole blog can be appeared on local.  

### Add image
Create folder under the `/log/static/img` like `2019-12-17`.  
After putting images, you can write image tag in markdown file to show the image like the below.  
```
![1](../../img/2019-12-07/1.jpg)  
```

## Build
1. `rm -Rf docs/`  

2. `hugo`  

3. `mv public/docs`  

4. `git add .`  

5. `git commit -m "Add a image file"`  

6. `git push`  

## Acknowledgments
I applied the theme of [github-style](https://github.com/MeiK2333/github-style.git). Thank you for providing good theme.  
