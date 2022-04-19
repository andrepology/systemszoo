> #idea See patterns in your artwork doing PCA, and visually annotating results. 

+ PCA
	+ Project images onto a space, cache, cast to [[Streamlit]]

#worklog
+ [[2022-02-28]] Basic PCA
	+ [+] Get images from Notion API, node.js
		+ Need to work on pagination
		+ handle for multiple images in page, currently appends
		+ is there a better REPL?
	+ Goal: cache the PCA coordinates, cast images to an image on slider
		+ Slider: 50 components
		+ Image: 2D of first two components
		+ Write up, pulled from assignments

+ [[2022-02-27]] Working with the Notion API
	- [x]  Auth Key
	- [x] Load database, retrieve page ids
		- Giving me practice with the [[Node]] REPL, which is nice. Keeping two terminals side by side and comfort with CLI is the best
	- [x] Request each page in database page
	- [x] Retrieve block children endpoint and get pages
	- [x] Filter out Blocks for Image objects
	- [x] Save images to disk
		- [ ] Tricky pagination issues

	