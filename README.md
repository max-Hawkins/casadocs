# CASAdocs
Common Astronomy Software Applications Documentation

- view latest master build at: https://casadocs.readthedocs.io/en/latest  [![Documentation Status](https://readthedocs.org/projects/casadocs/badge/?version=latest)](https://casadocs.readthedocs.io/en/latest/?badge=latest)
- view stable release build at: https://casadocs.readthedocs.io/en/stable  [![Documentation Status](https://readthedocs.org/projects/casadocs/badge/?version=stable)](https://casadocs.readthedocs.io/en/stable/?badge=stable)

## Editing CASA Docs

Always edit the **master** ('latest') build at https://casadocs.readthedocs.io/en/latest [![Documentation Status](https://readthedocs.org/projects/casadocs/badge/?version=latest)](https://casadocs.readthedocs.io/en/latest/?badge=latest).

Go to the chapter page, and click the *“Open in Colab”* link at the top to update documentation within the Notebook environment. 
To save updates, select as default ```File -> Save a copy in Github```. This will save the updated notebook to the master (‘latest’) build of CASA Docs. 
A new documentation build is triggered for every commit to the repository. 

It can take 5 to 10 minutes to complete and for changes to propagate to master.

**Note: API pages (e.g., casatasks and casatools) are handled differently, as will be explained later in this document.**


## Editing Regular Content
Most of the casadocs content is written in markdown format using the Google
Colab web service to edit Jupyter notebooks of text cells.  Jupyter notebook
pages have a link at the top to *"Open in Colab"* for editing.  Modified pages
can be saved back in to the casadocs repository from the Colab window under ```File -> Save a copy in Github```.

The nbsphinx package is used to convert notebooks to Sphinx/readthedocs format.
There is some special markdown syntax available that may not render in Google 
Colab.  For the complete set of markdown syntax avaiable, go here:
- https://nbsphinx.readthedocs.io/en/0.7.1/markdown-cells.html

### Common syntax

- **Open an editor** by double-clicking the text in a text-box. After updates are implemented, double-click on the right-hand text-box again for the editor to close and changes to show up in the Colab Notebook. Do not forget to ```File -> Save a copy in Github``` when finished!

- **Code boxes (green)** can be added by backeting the text with \`\`\`. Code boxes render in grey in Colab. Example:

   \`\`\`
   <br>
   This text will appear in a green/grey code box
   <br>
   \`\`\`
   ```
   This text will appear in a green/grey code box
   ```

- **Warning boxes (orange)** can be added with \<div class=\"alert alert-warning\"\>. Warning boxes render as normal text in Colab, but show as orange boxes on readthedocs. Example:

   \<div class=\"alert alert-warning\"\><br>
   This is a warning that can be added to the text <br>
   \</div\>
   <div class="alert alert-warning">
   This is a warning that can be added to the text
   </div>

- **Note boxes (blue)** can be added with  \<div class=\"alert alert-info\"\>. Note boxes render as normal text in Colab, and only show as blue boxes on readthedocs. Example:

   \<div class=\"alert alert-info\"\> <br>
   This is a note that can be added to the text <br>
   \</div\>
   <div class="alert alert-info">
   This is a note that can be added to the text
   </div>

- **Bullet points** can be added by a preceding \-.<br> 
*Important:* leave a blank line between the text and the first bullet point! If not, the layout will look ok in the notebook, but be messed up on readthedocs. Example:

   *This is a list of bullet points*<br>
   <br>
   \- *Bullet point 1*<br>
   \- *Bullet point 2*<br>
   <br>
   will render properly, but the following will not:<br>
   <br>
    *This is a list of bullet points*<br>
   \- *Bullet point 1*<br>
   \- *Bullet point 2*<br>  
   
- **Math symbols** can be added mostly using the standard convention for Mathematics, such as used by Latex (with conventional \$...\$ and \\\(...\\\).

### Adding chapters and paragraphs

Notebooks have sub-level chapters, and chapters have sub-sub-level paragraphs. All chapters and paragraphs of the Notebook show up in CASA Docs’ *Table of Contents*, visible on the left side.

To add a new chapter or paragraph, click the “\+ Text” button, either on the top bar, or at the bottom of the previous chapter or paragraph. The new text box will be added as a sub-directory of the current text box. Therefore, a chapter can be added when inside the top-level box of the notebook, while a paragraph can be added while inside a chapter box.

Titles of new paragraphs should be preceded by \#\# , e.g., “\#\# Imaging”.

   
### Adding figures

Upload the image to the following github folder:
https://github.com/casangi/casadocs/tree/master/docs/notebooks/media 

Then insert the image in the notebook using this syntax:<br>
\!\[filename\](https://github.com/casangi/casadocs/blob/master/docs/notebooks/media/filename.png?raw=1).<br> 
Optional: you can control the height/width using this syntax after the image \{.image-inline width="635" height="347"\}. This does not render properly in colab, only on readthedocs!

### Adding links

*Internal chapter pages:* To add a link named “this link”, put the link-name in brackets and add in parenthesis the top-notebook-directory as .ipynb, and optionally add \# plus the sub-directory. Example:

- \[this link\](usingcasa.ipynb\#Starting-CASA) to link *“this link”* to the sub-directory *“Starting CASA”* within the *“Using CASA”* chapter.

*Internal API pages:* Same as above, but put in parenthesis “../tasks/” and add the .rst file. Example: 

- \[this link\](../tasks/task_tclean.rst)

*External pages:*  Same as above, but add the URL in brackets. Example: 

- \[this link\](htts://www…).

Do not use https to link to other CASA Docs pages, unless they need to point to a static snap-shot of a particular CASA version on GitHub or Plone. During branching, internal links will be properly handled, while https links remain static.


### Adding in-chapter references

To add references to a notebook-chapter, add a text-box to the bottom of the notebook (using the “\+ Text” button on the top-left) with title “\#\# Bibliography”. Then list your references:<br>
<br>
\#\# Bibliography<br>
<br>
“1. Reference 1”<br> 
“2. Reference 2”<br>
 etc.<br> 
<br>
In the notebook text, link to reference 1 as follows: \[\\\[1\\\]\](\#Bibliography). Example: see<br> 
https://colab.research.google.com/github/casangi/casadocs/blob/master/docs/notebooks/synthesis_imaging.ipynb



## Editing API Content
API (Application Programming Interface) content is generally created by combining xml from the CASA source code
repository with ReStructuredText (rst) files held in the casadocs repository.
The xml can only be updated through development branches of the source code,
while the rst files can be edited directly in the Github repository browser
window.

- Task descriptions can be found under ```docs/tasks```
- Tool descriptions can be found under ```docs/tools```
- Shell descriptions can be found under ```docs/api/casashell```

Example: to update a task description page, go to https://github.com/casangi/casadocs/tree/master/docs/tasks. Click on the .rst file of the task, select *“Edit this File”* on the top-right, update the file, *“Preview”* it, and click *“Commit Changes”* at the bottom of the page.
*Note: updating "parameters" information requires updating the XML files in the code!*

API uses RestructuredText format: 
- https://docutils.sourceforge.io/docs/user/rst/quickref.html

Sphinx RST syntax and examples can be found here:
- https://sphinx-rtd-theme.readthedocs.io/en/stable/demo/demo.html

### Updating XML
When the XML is updated in the CASA source code repo, the files need to be synced back 
to the casadocs repo. This is done through a manually triggered Github Action rather 
than automatically to allow for specific updates to different release branches if necessary.

To update the xml file sync from the CASA source code repo, go to the ```Actions``` tab in
Github, select ```Update_XML``` and click ```Run Workflow```

Verify the files have been updated by navigating to the ```xml``` folder in the root of the
Github repo.

### Adding/Removing/Hiding Tasks
Tasks will only appear in the readthedocs site if they have both an xml file in the ```xml```
folder and a matching rst file in the ```docs/tasks``` folder.  A task can be removed or hidden
from readthedocs by deleting or renaming the rst file to something that does not match the
xml file name.

When a new task is added to CASA, the new xml file will be picked up by the Action described 
above. A new ```rst``` file must also be added to ```docs/tasks``` using the same format as
the others (with sections for Description/Examples/Developer).

Example: to add a new task do CASA Docs by importing importing the corresponding XML files, creating an .rst file in the API, and then editing the API information:

- On GitHub one has to pull in xml changes, including the new xml file for a new task:
https://github.com/casangi/casadocs/actions?query=workflow%3AUpdate_XML

- Then a new .rst file needs to be added to docs/tasks folder for the new task:
https://github.com/casangi/casadocs/tree/master/docs/tasks

- Then edit the .rst file to fill in the appropriate description and other relevant info (see *Editing API Content*).

## Building Documentation Locally
This documentation repository can be edited and built locally by users with access to Python3. First clone the repo, then navigate to the root of the cloned directory in a terminal and use the following commands:

```
$: python3 -m venv docvenv
$: source docvenv/bin/activate
(docvenv) $: pip install --upgrade pip wheel
(docvenv) $: pip install -r requirements.txt
(docvenv) $: cd docs
(docvenv) $: sphinx-build -a -E -b html . ./build
```

## Re-generating Plone content from Scratch
This should not be necessary and is here only for reference on how
to regenerate the original content from Plone.  

Scrapy and Docker must installed ahead of time, then install the 
python prerequisites from the local build instructions.

1. Scrape the latest Plone CASAdocs (creates html folder):
   ```
   $: scrapy crawl sitemap
   $: docker run -p 8050:8050 scrapinghub/splash
   $: scrapy crawl full
   ```

2. Generate content pages (creates markdown folder)
   ```
   $: python scripts/convert_html.py
   ``` 

3. Generate notebook files (creates docs/notebooks folder)
   ```
   $: python scripts/build_notebooks.py
   ```

4. Locally build pages to verify (this will also call scripts/parse_task_xml.py)
   ```
   $: cd docs
   $: sphinx-build -a -E -b html . ./build
   ```



