# Rāpoi-docs
Documentation for the Rāpoi cluster.

Built using the <a href="http://127.0.0.1:8000">sphinx</a>-based <a href="https://docs.readthedocs.io/en/stable/intro/getting-started-with-sphinx.html">Read the Docs theme</a> and deployed via <a href="https://www.mkdocs.org/">Mkdocs</a>. ```mkdocs.yml``` configures basic site structure, menu structure and Table of Contents depth, and can also customise other variables. ```Extra.css``` defines non-standard styling. 

Currently, heading levels 1 and 2 (# and ##) creating clickable menu items in the side nav bar:
![Menu levels example](docs/img/Menu_structure.png)

## Workflow for updating docs (locally via CLI):

1. Make sure you're on the ```master``` branch on the ```raapoi-docs``` repository.

1. Navigate to the ```docs``` folder and open and edit (or create) the appropriate ```.md``` file, (e.g. ```examples.md```).

1. Save once changes are made, then ```add```, ```commit```, and ```push``` to ```origin master```.

1. Now deploy this with MKdocs commands:

	```mkdocs build --clean``` <br>
	(This builds the markdown files into a ```/site``` folder, where each ```.md``` file creates a folder of the same name with it's own ```index.html```). 
	<br>
	Note: ```clean``` overwrites and cleans existing ```/site``` directory. 

1. (Optional) To see changes locally, use ```mkdocs serve``` which will print a variant of: 
	```
	plummema@ITS-7MTSF2S MINGW64 /h/GIT_HUB/raapoi-docs (master)
	$ mkdocs serve
	INFO    -  Building documentation...
	INFO    -  Cleaning site directory
	[I 190619 12:41:14 server:298] Serving on http://127.0.0.1:8000
	```
	The local site is now viewable at <a href="http://127.0.0.1:8000">```http://127.0.0.1:8000```</a>. This supports real time previes, so any local changes made and saved will update the server automatically.

1. When ready to publish, use:
```mkdocs gh-deploy``` (optional ```--clean``` can be appended to deploy a clean version)

	This pushes changes from ```.md``` files to the relevant ```html``` pages in the ```/site``` folder of the ```gh-pages``` branch. 
	It should return something like: 
	```
	plummema@ITS-7MTSF2S MINGW64 /h/GIT_HUB/raapoi-docs (master)
	$ mkdocs gh-deploy
	INFO    -  Cleaning site directory
	INFO    -  Building documentation to directory: H:\GIT_HUB\raapoi-docs\site
	INFO    -  Copying 'H:\GIT_HUB\raapoi-docs\site' to 'gh-pages' branch and pushing to GitHub.
	INFO    -  Your documentation should shortly be available at: https://vuw-research-computing.github.io/raapoi-docs/
	```
	That's it! If editing multiple files, make local changes on all the required files first, then these steps only need be worked through once.

	Note: the repo publishes docs from the ```gh-pages``` branch, but if using ```mkdocs gh-deploy``` refrain from editing in that branch, use the above workflow (i.e. editing ```master``` instead).

