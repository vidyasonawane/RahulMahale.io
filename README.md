# RahulMahale.io
A personal website of Rahul Mahale.

## How to update the website?
* To add the new blog:
  - create name_of_blog.md file in `content\blogs` folder
  - Note: the name of the blog will appear in the url.
  - After creating a file, add the following content at the start 
   
   ```
      +++
      date = "2013-11-08"
      title = "<Title of the blog>"
      tags = [""]    
      categories = [""]  
      +++
      <Content of the blog>
  ```
   - Save the file and run it using "hugo serve", the blog will appear in blogs section.
   
   (Note: Similar to the blogs, one can also add talks by using same method mentined above)
   
* To add a new images in the gallery:
  - Add the image in `\static\images\portfolio` folder.
  - The name of the image will visible after hovering over that image in the gallery.
     
* To add a new tab in navigation bar:
  - Add the following code in `config.toml` file.
 
   ```
      [[languages.en.menu.main]]
      name = "/Blogs"
      weight = 2
      url = "blogs/"   
  ```
   - `name` will appear on website as a tab in navigation bar
   - `weight` indicates the position of the tab starting from left side.
   - create a folder `blogs` in the content folder. The name of url and the name of the folder must be same.
        
* To change the profile picture
  - change the image `static\images\rahulMahale.jpg`
 
