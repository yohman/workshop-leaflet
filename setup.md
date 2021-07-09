
# Setup for the course
You will need:

1. a [GitHub](https://github.com/) account
1. a GitHub repository for the course
1. enable GitHub Pages
1. Git installed on your computer (below)
1. Visual Studio Code installed on your computer (below)

## Create a GitHub repository for this course

First, we need to make sure you have a GitHub account, and a dedicated repo for this course.

Go to your GitHub page, click on "Repositories" and "New"

Enter the following information:

<kbd><img src="images/repo.png"></kbd>

Confirm that your repository has been created.

## Enable GitHub Pages

GitHub pages will allow you to use GitHub as a web server for your html/javascript/css files.

1. In your GitHub class repo, which should be something like this: https://github.com/your_github_name/leaflet, go to `Settings`
2. In the left menu panel, select **Pages**
1. Choose the `main` branch and save

	<kbd><img src="images/pages.png"></kbd>

1. Take a note of your new "Pages" url:

	<kbd><img src="images/pagesurl.png"></kbd>


## Install Git

- https://git-scm.com/

For MacOS, choose the "homebrew" option (it takes about 10-15 mins to install homebrew)

Once homebrew is installed, Open terminal and enter the following command:

`$ brew install git`

When git is installed, check your installation:

`git --version`

## Set the Git configuration

Open a terminal window and enter the following with your GitHub credentials:

```PowerShell
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```
	
## Install VS Code

- Install the text editor [Visual Studio Code](https://code.visualstudio.com/download)

