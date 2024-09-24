# Structuring Content using the Table of Contents

In order to build your book, Jupyter Book needs to know how you want to structure the content that you have created, that is: 

* **Which files should be displayed on your website?**
* **In which order should the pages appear?**
* **In what form should the content be displayed?**

The answers to these questions are written in a `YAML` file called `_toc.yml`, which defines the `Table of Contents`, as well as the formatting of your book. It can be found in, e.g., the lecture folder of the [template](https://github.com/M-earnest/course_template_diler). The `_toc.yml`, therefore, defines the structure of your course website. 

In the simplest form, the `_toc.yml` looks like this:

```format: jb-book
root: index`
chapters:
- file: path/to/chapter1
- file: path/to/chapter2
  sections:
  - file: path/to/chapter2/section1
```

While this might seem overwhelming at first, it is actually really simple. Below, you'll find a short description of the keys. Keys are words, helping Jupyter Book to understand what you are expressing in the ToC.

|Key|Description|
|---|---|
|`format:`|*Format* defines how the ToC will be interpreted. For our purposes, `jb-book` will be the appropriate option.|
|`root:`|*Root* defines the landing (aka first) page of your book. The paths that you define will be relative to the root.|
|`chapters:`|Contains a list of files. No argument is needed here|
|`file:`|Path to the files that you want to include in your book. All the paths are relative to the root.|
|`sections:`|Defines sections of a chapter.|

Furthermore, you can also **subdivide chapters into parts** using the `parts:` argument:

```format: jb-book
root: index
parts:
  - caption: Name of Part 1
    chapters:
    - file: path/to/part1/chapter1
    - file: path/to/part1/chapter2
      sections:
      - file: path/to/part1/chapter2/section1
  - caption: Name of Part 2
    chapters:
    - file: path/to/part2/chapter1
    - file: path/to/part2/chapter2
      sections:
      - file: path/to/part2/chapter2/section1
```
|Key|Description|
|---|---|
|`parts:`|Parts can further subdivide and group chapters and, thus, consist of a list of chapters.|

```{note} Note
The chapter names displayed on your website are defined by the top-level heading of the respective document. For instance, for this page, the top-level header looks like this: `# Structuring Content using the Table of Contents` 
```

#### Adapting the toc.yml/Table of Contents

To add your course content, simply provide the path to your newly created or adapted file, including the respective filename to this document. For this, you can simply copy-paste the existing lines of the provided "toc.yml" and exchange the example filenames with your own filenames. It is further easiest if you simply adapt the `index.md` file provided with our template as the `"root"`, i.e. the landing page of a website.

In practice, the provided structure for our template looks like the following. 

Where our ["toc.yml"](https://github.com/M-earnest/course_template_diler/blob/master/lecture/_toc.yml) looks like this:

</br>

<img src="https://github.com/felixkoerber/jb/blob/main/static/template_toc.png?raw=true" alt="depicting an example of a new repository" class="bg-primary" width="500px">

</br>

and results in this site layout:

</br>

<img src="https://github.com/felixkoerber/jb/blob/main/static/template_layout.png?raw=true" alt="depicting an example of a new repository" class="bg-primary" width="500px">


___
#### Autogenerate the Table of Contents from a list of files

While we generally recommend customizing the ToC yourself using the template we provide, Jupyter Book also offers a built-in function that generates the Table of Content based on filenames of your content. 

To use this, enter the following code into the terminal of your liking:

`jupyter-book toc from-project path/to/book -f [jb-book/jb-article]`

```{note} Note
To use this command, open your OS-respective Terminal, and copy the path to where your files are as an argument (here displayed as "path/to/book")
```

This function will search your respective path for content files and generate the `_toc.yml` based on the content files. Keep in mind that:
* Each sub-folder must have at least one content file inside it
* The ordering of files in `_toc.yml` will depend on the alphanumeric order of the filenames (e.g., `folder_01` comes before `folder_02`, and `apage` comes before `b_page`)
* If there is a file called `index.md` in any folder, it will be listed first.

In addition to that, there are a few arguments you can add to the command to control the generation, which are outlined below:

```Usage: jupyter-book toc from-project [OPTIONS] SITE_DIR

  Create a ToC file from a project directory.

Options:
  -e, --extension TEXT            File extensions to consider as documents
                                  (use multiple times)  [default: .rst, .md]
  -i, --index TEXT                File name (without suffix) considered as the
                                  index file in a folder  [default: index]
  -s, --skip-match TEXT           File/Folder names which match will be
                                  ignored (use multiple times)  [default: .*]
  -t, --guess-titles              Guess titles of documents from path names
  -f, --file-format [default|jb-book|jb-article]
                                  The key-mappings to use.  [default: default]
  -h, --help                      Show this message and exit.
  ````

While this should cover the basics, feel free to check out [Jupyter Book's Manual](https://jupyterbook.org/en/stable/structure/toc.html) for further information.

### Next section

[Publishing](./tutorialcontent/publishing/publishing)
- [Build and publish your course](./tutorialcontent/publishing/account)

