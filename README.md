# CASAdocs
Common Astronomy Software Applications Documentation

- view latest master build at: https://casadocs.readthedocs.io/en/latest  [![Documentation Status](https://readthedocs.org/projects/casadocs/badge/?version=latest)](https://casadocs.readthedocs.io/en/latest/?badge=latest)
- view stable release build at: https://casadocs.readthedocs.io/en/stable  [![Documentation Status](https://readthedocs.org/projects/casadocs/badge/?version=stable)](https://casadocs.readthedocs.io/en/stable/?badge=stable)

**Table of Contents**
- [Editing CASADocs](#editing-casadocs) : How to edit the user manual sections of CASAdocs stored in Jupyter notebooks
    - [Common syntax](#common-syntax)
    - [Adding chapters and paragraphs](#adding-chapters-and-paragraphs)
    - [Adding figures](#adding-figures)
    - [Adding links](#adding-links)
    - [Adding in-chapter references](#adding-in-chapter-references)
- [Editing API Content](#editing-api-content) : How to edit the CASA interface specifications stored as RestructuredText files
    - [Adding/Removing/Hiding tasks](#addingremovinghiding-tasks)
- [Branching CASADocs](#branching-casadocs) : How to make CASADocs edits on a branch and see them on Readthedocs
    - [Corresponding code branches](#corresponding-code-branches)
    - [Viewing a branch on Readthedocs](#viewing-a-branch-on-readthedocs)
    - [Review and pull request](#review-and-pull-request)
- [Building Documentation Locally](#building-documentation-locally) : How to make CASADocs edits on a local clone

**Quick Links**
- [View Branches](https://readthedocs.org/projects/casadocs/versions/) : See branch builds on Readthedocs
- [View Builds](https://readthedocs.org/projects/casadocs/builds/) : See the status of your build on Readthedocs

## Editing CASADocs

Editing CASA Docs can be done on branches, where pull requests can be triggered to merge changes back to master (see information below), or it can be done directly on master ('latest') itself: https://casadocs.readthedocs.io/en/latest [![Documentation Status](https://readthedocs.org/projects/casadocs/badge/?version=latest)](https://casadocs.readthedocs.io/en/latest/?badge=latest).

Most of the casadocs content is written in markdown format using the Google Colab web service to edit Jupyter notebooks of text cells. 
Go to the chapter page, and click the *“Open in Colab”* link at the top to update documentation within the Notebook environment. 
To save updates, select as default ```File -> Save a copy in Github```. This will save the updated notebook to the master (‘latest’) build of CASA Docs. 
A new documentation build is triggered for every commit to the repository. 

It can take 5 to 10 minutes to complete and for changes to propagate to master.

**Note: API pages (e.g., casatasks and casatools) are handled differently, as will be explained later in this document.**

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


## Branching CASAdocs

Updates made to master ('latest') are immediately public. This can be useful for minor or urgent updates to the documentation 
that do not require a review. Making a documentation *branch* is useful for larger documentation updates, updates that require 
a review, or updates that should be merged at a later stage (e.g., simultaneously with the code).

To make a branch, go to: https://github.com/casangi/casadocs/tree/master/docs

Under the default *“master”* label on the top-left, go to *“find or create a branch”*, add a name (e.g., “test_branch”) and 
press *“create branch: test_branch” from “master”*.

To view the documentation for this branch, navigate to: https://casadocs.readthedocs.io/en/test_branch (example only, not a real link)

One can then update the text on the branch. This is easiest to do through Colab:
https://colab.research.google.com/github/casangi/casadocs/ <br>
Open the “test_branch” that you have just created, then edit the Notebook.

There are two ways to save the updates:
- Direct save to “master”, by choosing *“Branch: master”*. This will surpass any reviews and trigger an automatic new build. 
- Save back to the branch, by choosing *“Branch:  test_branch_instructions”*. This can now go through review and pull request, as explained below.

*Warning:* the default is to save updated straight to “master”, so be careful to save material that needs to pass review back to the branch first!

### Corresponding code branches

To create new documentation for a Jira ticket development branch (ie CAS-12345) that is not yet merged to (Bitbucket) master, a corresponding 
casadocs branch of the **same name** should be made. The casadocs build script attempts to find a corresponding source code Bitbucket branch of the 
same name. If found, it will use the XML from that Bitbucket branch when building the API casatools and casatasks pages. If no corresponding branch 
is found, casadocs will default to the Bitbucket master.

This allows developers to see the effects of their tool/task parameter changes.

### Viewing a branch on Readthedocs

When a new branch is created, readthedocs will automatically activate it, build it, and then hide it from public display. This 
prevents developer branches from appearing on the casadocs website. But they can still be viewed by directly navigating to the 
URL of the same name as the branch that was created.

Branches will NOT appear in the version list flyout box on the bottom left corner of Readthedocs, nor will they be indexed by search engines.
However they can be found (by anyone) by navigating directly to the Readthedocs CASADocs project dashboard:

[https://readthedocs.org/projects/casadocs/versions/](https://readthedocs.org/projects/casadocs/versions/)

### Review and pull request

After saving the updates, one automatically is reverted back to github. When clicking *“pull requests”* on the top bar of the github page, the updated notebook now appears as *“test_branch had recent pushed 1 minute ago”*.

Clicking *“compare and pull request”* allows you to see the changes, leave comments, and *“request”* colleagues to review the updates. Then click *“create pull request”*.

After all reviewers have completed their reviews, press *“merge pull request”* to merge the updates to *“master”*. 

Once approved, the pull request can be merged to master (either by the reviewer or yourself) by pressing *“merge pull request”*. As instructed on github, the pull request can then be safely deleted by clicking *“delete branch”*. 


## Building Documentation Locally
This documentation repository can be edited and built locally by users with access to Python3. First clone the repo (git clone `https://github.com/casangi/casadocs.git`), then navigate to the root of the cloned directory in a terminal and use the following commands:

```
$: python3 -m venv docvenv
$: source docvenv/bin/activate
(docvenv) $: pip install --upgrade pip wheel
(docvenv) $: pip install -r requirements.txt
(docvenv) $: cd docs
(docvenv) $: sphinx-build -a -E -b html . ./build
```
The **Pandoc** library must be installed or the build will error out. The build script attempts to install it through Python commands. If that doesn't work, then it will need to be manually installed by finding the appropriate distro for the OS being used.

After building the documentation, it can be viewed in a web browser by pasting the full file path to the **index.html** in the URL field. The **index.html** file is in the `build` directory created under `docs` (i.e. */home/user/test_docs/casadocs/docs/build/index.html*). 


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



