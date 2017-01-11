# Wordpress

## What is Wordpress?

Wordpress is a staple in the web community - it's a simple CMS (Content Management System) that allows a non-technical person to CRUD all of their website's info through an easy to use GUI (Graphical User Interface).

Once just a simple blogging platform, WordPress is now used on 27% of public websites - so statistically, you've got a 1 in 4 chance of needing to know how to use it.

## Set Up

1. Download Wordpress from <https://wordpress.org/latest.zip>
1. Unzip the downloaded file.
1. Place it in a local repo that you want to use for the project.
1. Point MAMP to Wordpress Directory:
	- Click on Preferences
	- Click on Web Server
	- Click the folder icon next to "Document Root" and find the unzipped wordpress directory
	- Click OK
1. Go to <http://localhost:8888/>
1. Choose your language
1. Click "Let's Go!"
1. Create a `wordpress` sub database in MySQL
	- Download a mysql GUI client (<http://www.sequelpro.com/download> and click download)
	- Open downloaded .dmg file
	- Drag application icon to Applications directory and double click it.
	- Click 'Socket' as your connection type
	- Fill in the following info
		- Host: 127.0.0.1 (same as localhost)
		- Username: root
		- Password: root
	- Click Connect
	- Open the Sequel Pro (Query) terminal and type `CREATE DATABASE wordpress;` (these commands do not run on `enter`)
	- Click the "Run Previous" button to run it (it might also be say "Run Current")
	- In the terminal type `SHOW DATABASES;`, then click 'run' again
	- Confirm that `wordpress` is listed in the output
1. Back in your web browser, fill out the info like so:
	- Database Name: wordpress
	- User Name: root
	- Password: root
	- Database Host: localhost
	- Table Prefix: wp_
1. Click "Run the intall"
1. Fill out the info on the next page and click "Install Wordpress"
1. Click "Log In"
1. Log In
1. The frontend of your will be visible at http://localhost:8888/

## Frontend Vrs. Admin

Wordpress consists of two 'halves' - the frontend side, which you see by visiting <http://localhost:8888/> and the admin panel, which you see by visiting <http://localhost:8888/wp-admin/>. The Admin panel is where you make changes to the site's appearance, content, and settings. The frontend will display those results.

In the admin panel, you'll see quite a few options for creating content - most notably Posts, Media, and Pages:

**Posts** are the equivalent of individual blog posts. Since Wordpress started as a blogging platform, they still get top billing in the menu, as well as a default place on the homepage of all default templates. Inside this menu, you'll be able to create, edit and delete your posts, as well as tag them, sort them, and assign them to categories.

**Media** acts as a repository of all media on your site - photos, video, music, etc. Anything stored here can be easily refernced using Wordpress' built-in media tools. Clicking the media link will allow you to upload, sort, and categorize all the media on your site.

**Pages** are what we think of tradtionally when it comes to web pages - you might have one for about, contact, home, etc. The pages link will allow you to create, sort, and categorize your pages. 

### What's the difference between posts and pages?

A few key differences:

**Posts** are NOT full pages - they are 'components' that can be inserted into pages - either as a whole, or as a list. There is a `single.php` file that acts as a default wrapper for any posts that is visited by itself, and don't allow you to insert custom page-specific HTML. As a result, posts are good for recurring content that has a distinct pattern and design to it. The list of most recent posts is easy to call into pages dynamically, so that no dev work is needed to update the site.

**Pages** are essentially blank HTML files that will act as a single HTML page. They're good for unique content-rich pages that might differ visually from one another. However, they take a bit more skill to update and assign to the menu. 

## Themes

Most of your work as a developer will take place in `Appearance > Themes`. Clicking into this menu item will show a list of all the themes you have installed. You can choose which one you want to use on the frontend, as well as customize some of the options for each one:

![Themes](img/themes.png)


1. Themes
	- Can add new themes
	- Can customize themes
	- Widget
		- Usually placed in a sidebar or someplace similar
	- Menus
		- A set of links to be placed anywhere
	- Header
		- Theme sets location
	- Background
		- Behind themes
	- Editor
		- Edit CSS and PHP Files
1. Plugins
	- Akismet
		- Checks for spam in comments
	- WooCommerce
		- Ecommerce!
	- Can write your own
1. Users
	- Administrator – somebody who has access to all the administration features within a single site.
	- Editor – somebody who can publish and manage posts including the posts of other users.
	- Author – somebody who can publish and manage their own posts.
	- Contributor – somebody who can write and manage their own posts but cannot publish them.
	- Subscriber – somebody who can only manage their profile.
1. Tools
	- Can import/export from/to other blogs
1. Settings
	- General
		- Site Name
		- URL
		- main point of contact
	- Reading
		- Have a static page (from Pages) instead of list of articles on your front page
		- How many posts on summary page
		- Content of feed
	- Discussion
		- Comment settings
			- Who can comment
			- How long the discussion is open for
			- Nesting comments
			- How many comments per page of comments
			- Comment notification
			- Comment moderation settings
	- Media
		- Small/Medium/Large sizes
	- Permalinks
		- URLs are generated based around SEO
		- You can customize
			- Post
			- Category
			- Tags

## Theming

### Set Up

1. Go to wp-content/themes/
1. Duplicate a theme directory
1. cd into new theme directory
1. open style.css and edit Theme Name and other values in comments
	- This affects how theme is displayed in wordpress admin panel
1. change screenshot.png

### Important Files

1. index.php
	- home
1. header.php
	- top part of site
1. sidebar.php
	- sidebar
1. sidebar-content-bottom.php
	- additional menu widgets
1. single.php
	- view a particular post`
1. page.php
	- view a page
1. content.php
	- content of a post
1. comments.php
	- comments section
1. footer.php
	- footer

### Important Functions

Functions that start with `the_` can usually be prepended with or replaced by `get_`.  When this is done, value is returned, not printed

1. `get_header()`
	- display header
1. `is_home()`
	- is home page
1. `is_front_page()`
	- is this the front page (single page to display, not containing articles
1. `get_sidebar()`
	- display sidebar
1. `get_footer()`
	- display footer
1. `bloginfo('name')`
	- name of blog
1. `bloginfo('description')`
	- description of blog
1. `have_posts()`
	- are there posts left to display?
1. `the_post()`
	- pull up the next post in the queue
1. `the_posts_pagination()`
	- how to show next/previous buttons
1. `have_comments()`
	- does the article have comments
1. `comments_open()`
	- are people allowed to comment
1. `get_comments_number()`
	- get the number of comments
1. `wp_list_comments()`
	- list comments
1. `the_comments_navigation()`
	- pagination for comments
1. `comment_form()`
	- create comment form
1. `the_author()`
	- display author of the article
1. `the_title()`
	- display the title of the article
1. `the_content()`
	- display the body of the article
1. `the_permalink()`
	- display permalink for the article
1. `get_template_part()`
	- use a sub template for some chunk of data
