Notes
- hoping these will be useful to either Miranda or whoever finishes/alters the site

To upload the site
- change the name of "draft6.html" to "index.html"
- change the name of "styles-draft6.css" to "styles.css" and also, in line 3 of draft6.html
- upload index.html, styles.css, PatchFun.ttf, the doors folder and the content folder all to the same directory (might be public_html) of the site hosting service

To edit the contact form to go to your email, create an account / form on formspree.io, get a link for your form, and replace the form link in draft6.html (can search FORMSPREE LINK, line 56, link goes on line 58).

To add your social links, replace "instagram link here", "youtube link here" etc in draft6.html with your social links.

To edit the images for the Art gallery, in the file draft6.html, go to the function "getGalleryImages()" - you can also search "gallery images". Above this function is a list of file names. Change the filenames, add to them, etc - the function will automatically load the first four as the opening gallery images and the rest when the visitor cycles through.

To edit the videos displayed in each video gallery, or the "Meet Miranda" video, go the function loadiframes() and edit the list for whichever category (media, comedy, film). These are currently built for three videos apiece. The meet miranda video is a single link in quotes mirandasrc="link". These should be YouTube or Vimeo (or whatever embeddable video player) embed links (YouTube has specific embed links, vimeo might not).

To edit the font, change the h1 { font-family: } in the CSS file. I coded this in scss using SASS, but the .css file can be edited directly.

To edit the colors:
text: 
- in scss (for coders): edit the var $text-color
- in the plain css: find and replace the color you want to edit
- so for the text color, find and replace #fb0446 with the color you want from an html color picker site (any format they give you will work - hsl, rgb)
background color:
- edit the body { background-color: #02825F; } (line 12)

Technical notes

SCSS file structure:
- top level css
- overlays
- mixins
- layout - front page sections
- front page sections 


The way the site works:
- asset loading: load the iframes + gallery images 2 seconds after page load (frontpage load speed + prevents interruption of 'peek' animation)

- 6 doors
- if mobile:
changeDoorState('category'):
- onclick, reveal headers for each door
- on second click, open the door
	- overlay becomes full screen, z-index increases
	- at pace with door opening animation
	- x appears

- desktop:
changeDoorState('category'):
- hover: open the doors slightly, reveal headers
- click: open the door


There are some artifacts of old ways of building
- built a two click system that opened the doors slightly on mobile, '.ajar' classnames
	- css 3d transforms didn't work reliably on mobile with z-indexing, so .ajar functionality reduced to just header text opacity
