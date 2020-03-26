Within the Digital Excellence project, the [wiki](https://git.fhict.nl/dex/dex-backend/-/wikis/home) is used to host technical documentation and other information about the project.

This guide explains how you can add or edit pages within the wiki.

If you are having troubles editing the wiki, do not hesitate to ask for help.



## Table of contents

[[_TOC_]]



## Markdown 

While the GitLab wiki system does support other formats for styling your pages (RDoc, AsciiDoc, and Org), in this guide we will focus on Markdown.

GitLab uses “GitLab Flavored Markdown” (GFM). It extends the [CommonMark specification](https://spec.commonmark.org/current/) (which is based on standard Markdown) in several ways to add additional useful functionality. It was inspired by [GitHub Flavored Markdown](https://help.github.com/en/articles/basic-writing-and-formatting-syntax).

[Here](https://docs.gitlab.com/ce/user/markdown.html) you can find the supported Markdown for GitLab.



## Editing the wiki

There are two ways of editing the wiki.

The easiest way to edit the wiki is using GitLab's [web interface](#using-the-web-interface).

For more advanced users, it is possible to add and edit pages [locally using Git](#adding-and-editing-wiki-pages-locally-using-git). This allows you to use your favourite Markdown editor.



### Using the web interface

*Source: https://docs.gitlab.com/ce/user/project/wiki/*

The easiest way to edit the wiki is using the web interface.

The web interface provides a simple Markdown editor to add or edit wiki pages.



#### Creating a new wiki page

Create a new page by clicking the **New page** button that can be found in all wiki pages.

You will be asked to fill in a title for your new wiki page.

You can specify a full path for the wiki page by using ‘/’ in the title to indicate subdirectories. Any missing directories will be created automatically. For example, a title of `docs/my-page` will create a wiki page with a path `/wikis/docs/my-page`.

Once you enter the page name, it’s time to fill in its content. GitLab wikis support Markdown, RDoc, AsciiDoc, and Org. For Markdown based pages, all the [Markdown features](https://docs.gitlab.com/ce/user/markdown.html) are supported and for links there is some [wiki specific](https://docs.gitlab.com/ce/user/markdown.html#wiki-specific-markdown) behavior.

In the web interface the commit message is optional, but the GitLab Wiki is based on Git and needs a commit message, so one will be created for you if you do not enter one.

When you’re ready, click the **Create page** and the new page will be created.

![New page](https://docs.gitlab.com/ce/user/project/wiki/img/wiki_create_new_page.png)



#### Editing a wiki page

To edit a page, simply click on the **Edit** button. From there on, you can change its content. When done, click **Save changes** for the changes to take effect.



#### Deleting a wiki page

You can find the **Delete** button only when editing a page. Click on it and confirm you want the page to be deleted.



#### Moving a wiki page

You can move a wiki page from one directory to another by specifying the full path in the wiki page title in the [edit](#editing-a-wiki-page) form.

![Moving a page](https://docs.gitlab.com/ce/user/project/wiki/img/wiki_move_page_1.png)

![After moving a page](https://docs.gitlab.com/ce/user/project/wiki/img/wiki_move_page_2.png)

In order to move a wiki page to the root directory, the wiki page title must be preceded by the slash (`/`) character.



#### Viewing a list of all created wiki pages

Every wiki has a sidebar from which a short list of the created pages can be found. The list is ordered alphabetically.

![Wiki sidebar](https://docs.gitlab.com/ce/user/project/wiki/img/wiki_sidebar.png)

If you have many pages, not all will be listed in the sidebar. Click on **More pages** to see all of them.



#### Viewing the history of a wiki page

The changes of a wiki page over time are recorded in the wiki’s Git repository, and you can view them by clicking the **Page history** button.

From the history page you can see the revision of the page (Git commit SHA), its author, the commit message, when it was last updated, and the page markup format. To see how a previous version of the page looked like, click on a revision number.

![Wiki page history](https://docs.gitlab.com/ce/user/project/wiki/img/wiki_page_history.png)



### Adding and editing wiki pages locally using Git

Since wikis are based on Git repositories, you can clone them locally and edit them like you would do with every other Git repository.

#### Clone your wiki

You can clone the wiki Git repository using the terminal or using your favourite Git GUI.

```
git clone https://git.fhict.nl/dex/dex-backend.wiki.git
cd dex-backend.wiki
```



#### Creating a new wiki page

Optionally, create a new (sub)folder for your page. Make sure to replace spaces with dashes (-).

Create a new Markdown file (.md). Make sure to replace spaces with dashes (-).

Open the Markdown file using your favourite editor. For example Typora (a WYSIWYG Markdown editor) or Notepad (or any other text editor).

When you finish editing your file, save it to your local repository. After that you can commit and push the newly created page using Git.



#### Editing a wiki page

Find the Markdown file of the page you like to edit.

Open the Markdown file using your favourite editor. For example [Typora](https://typora.io/) (a WYSIWYG Markdown editor) or any other text editor.

When you finish editing your file, save it to your local repository. After that you can commit and push the edited page using Git.



#### Deleting a wiki page

Find the Markdown file of the page you like to delete.

Delete the file from your local repository. After that you can commit and push the changes using Git.



#### Moving a wiki page

Find the Markdown file of the page you like to move.

Move the file within your local repository. After that you can commit and push the changes using Git.