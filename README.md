<h1 align="center">The Trove</h1>

<p align="center">Welcome! This is a repository for (not limited to) student in Bioinformatics to share knowledge or tips and tricks in programming. Feel free to contribute if you have any suggestion.</p>
<br>
<p align="center">
  <img alt="githubdark-logo" src="https://cdn.jsdelivr.net/gh/anggi3234/anggi3234.github.io@master/assets/img/sample/Bioinformatics.svg" width="580">
  <br>
  <a href="https://github.com/StylishThemes/GitHub-Dark/tags">
    <img src="https://img.shields.io/github/v/tag/anggi3234/anggi3234.github.io?label=version" alt="Version">
  </a>
  <a href="https://david-dm.org/StylishThemes/GitHub-Dark?type=dev">
    <img src="https://img.shields.io/david/dev/StylishThemes/GitHub-Dark.svg?label=devDependencies&style=flat" alt="devDependencies">
  </a>
</p>
<h3 align="center">Learn, Practice, Contribute.</h3>

# Table of Contents
* [About](#About)
* [Installation](#installation)
  * [Setting up your local environment](#setting-up-your-local-environment)
* [Usage](#usage)
  * [Initialization](#initialization)
  * [Configuration](#configuration)
  * [Run Locally](#run-locally)
  * [Deployment](#deployment)
    * [Deploy on GitHub Pages](#deploy-on-github-pages)
* [Contributions and Development](#contributions-and-development)
* [Credit](#credit)
* [Notes](#notes)


## About

This place is intended to help friends who are currently pursuing Bioinformatics degree or even to those who are not, but are curious to learn more in the subject. You can find helpful contents or even tips and tricks to learn more about: Bioinformatics in general, programming tips and tricks, or other things relating to productivity boosts or hacks for working from home that you think are helpful for in the current pandemic situation. Feel free to contribute if you have suggestions or contents.

## Installation

>This installation tutorial is adapted from the [jekyll-theme-chirpy](https://github.com/cotes2020/jekyll-theme-chirpy) repository, the forked repository used as the Jekyll theme for the website.

Prior to installation, you would need to install the necessary Jekyll dependencies: `Ruby`,  `Bundler`, `RubyGems`. You can find the tutorials to do that from [Jekyll Website](https://jekyllrb.com/docs/installation/) for the respective operating systems. Once installed, you can then fork and test the website on your local environment before submitting a pull request to contribute.

To ![fork](https://user-images.githubusercontent.com/136959/42383736-c4cb0db8-80fd-11e8-91ca-12bae108bccc.png)[fork](https://github.com/anggi3234/anggi3234.github.io/fork) the repository, go to the GitHub project page and click the fork button on the top right corner.


![Forking](https://github.com/anggi3234/anggi3234.github.io/master/assets/img/sample/forking.png?raw=true)

Once done, you can see the copy of the repository in your own profile. Rename the repository to `USERNAME.github.io` and change the `USERNAME` to your Github username or the desired name.


![Renaming](https://github.com/anggi3234/anggi3234.github.io/master/assets/img/sample/renaming.png?raw=true)



### Setting up your local environment

Clone the the forked project to your local computer by:
- Using the terminal

  ```terminal
  $ git clone https://github.com/USERNAME/USERNAME.github.io.git -b master --single-branch
  ```

- Using Github Desktop (You can use this if you prefer a GUI view)


You will need to complete the installation for Jekyll plugins prior to setting up the build.

Navigate to the directory of your project in your local computer and run:

```terminal
$ bundle install
```

`bundle` will automatically install all the dependencies specified by `Gemfile`.

In order to generate some extra files (_categories_, _tags_ and _last modified list_), we need to use some tool scripts. And they require dependency package [yq](https://github.com/mikefarah/yq#install) to be installed. What's more, if your machine is running Debian or macOS, you also need to install [GNU coreutils](https://www.gnu.org/software/coreutils/).

- on Debian:

  ```console
  $ sudo apt-get install coreutils
  ```

- on macOS:

  ```console
  $ brew install coreutils
  ```

## Usage

Running [**This Project**](https://github.com/anggi3234/anggi3234.github.io/) requires some extra files, which cannot be generated by Jekyll native commands, so please strictly follow the methods mentioned below to run or deploy your website.

### Initialization

Go to the root directory of the project and start initialization:

```console
$ bash tools/init.sh
```

> **Note**: If you not intend to deploy it on GitHub Pages, append parameter option `--no-gh` at the end of the above command.

What it does is:

1. Remove some files or directories from your repository:

    - `.travis.yml`
    - files under `_posts`
    - folder `docs`

2. If you use the `--no-gh` option, the directory `.github` will be deleted. Otherwise, setup the GitHub Action workflow by removing extension `.hook` of `.github/workflows/pages-deploy.yml.hook`, and then remove the other files and directories in folder `.github`.

3. Automatically create a commit to save the changes.

### Configuration

Generally, go to `_config.yml` and configure the variables as needed. Some of them are typical options:

- `url`
- `avatar`
- `timezone`
- `theme_mode`

### Run Locally

You may want to preview the site contents before publishing, so just run it by:

```terminal
$ bash tools/run.sh
```

Then open a browser and visit to <http://localhost:4000>.

Few days later, you may find that the file changes does not refresh in real time by using `run.sh`. Don't worry, the advanced option `-r` (or `--realtime`) will solve this problem, but it requires [**fswatch**](http://emcrisostomo.github.io/fswatch/) to be installed on your machine.


### Deployment

Before the deployment begins, checkout the file `_config.yml` and make sure the `url` is configured correctly. Furthermore, if you prefer the [_project site_](https://help.github.com/en/github/working-with-github-pages/about-github-pages#types-of-github-pages-sites) and don't use a custom domain, or you want to visit your website with a base url on a web server other than **GitHub Pages**, remember to change the `baseurl` to your project name that starting with a slash. For example, `/project`.

Assuming you have already gone through the [initialization](#initialization), you can now choose ONE of the following methods to deploy your website.

#### Deploy on GitHub Pages

For security reasons, GitHub Pages build runs on `safe` mode, which restricts us from using tool scripts to generate additional page files. Therefore, we can use **GitHub Actions** to build the site, store the built site files on a new branch, and use that branch as the source of the Pages service.

1. Push any commit to `origin/master` to trigger the GitHub Actions workflow. Once the build is complete and successful, a new remote branch named `gh-pages` will appear to store the built site files.

2. Browse to your repository on GitHub and choose the branch `gh-pages` as the [publishing source](https://docs.github.com/en/github/working-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site) throught _Settings_ → _Options_ → _GitHub Pages_:
    ![gh-pages-sources](https://raw.githubusercontent.com/anggi3234/anggi3234.github.io/master/assets/img/sample/gh-pages-sources.png)

3. Visit your website at the address indicated by GitHub.


## Contributions and Development

If you'd like to contribute to this repository, you can try to:

1. Make sure you have a [Github](https://github.com) account before you contribute.
2. [![fork](https://user-images.githubusercontent.com/136959/42383736-c4cb0db8-80fd-11e8-91ca-12bae108bccc.png) Fork](https://github.com/anggi3234/anggi3234.github.io/fork) this project repository and clone it locally.
3. Create a new branch from `master` and create a descriptive name.
4. Follow the installation guide to set up the environment locally for testing.
5. After completing the development and installation, commit and upush to the remote repository.
6. Submit a new pull request to be reviewed.

Thanks for the contribution! :sparkles:


## Credit
The web template (Jekyll theme) for this project is forked from [jekyll-theme-chirpy](https://github.com/cotes2020/jekyll-theme-chirpy) by [cotes2020](https://github.com/cotes2020).


## Notes

If you're unsure on how to contribute or are unfamiliar with GitHub, you can see the [documentation]( https://docs.github.com/en) here.  

## License

This work is published under [MIT](https://github.com/cotes2020/jekyll-theme-chirpy/blob/master/LICENSE) License.

[⬆️ UP](#Table-of-Contents)
