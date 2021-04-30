# University of Oslo Carpentry

This is the source code for the Github page of Carpentry at UiO. 
You can view the website [here](http://uio-carpentry.github.io/).
This site is mostly used for internal activities. 
If you are interested in participating in one of our workshops, please see [this page](https://www.ub.uio.no/english/courses-events/courses/other/Carpentry/)

## How to make changes to the content?

> :warning: **Changes should be made on the master branch, *not* gh-pages.** The `gh-pages` branch gets created automatically from the master branch once a day. Any manual changes made to `gh-pages` branch will be lost. Make changes to `master`.

* Changes can be made 
    1. Directly to the markdown files on Github. 
    2. Locally, using `hugo new ...` command. This is convenient for making new posts, as it allows to work with templates. It also allows to preview the changes.
    3. (not tested) Using RStudio's blogdown / hugodown. This allows to use R Code in a post and convert it to  

* To make changes locally, fork/clone the repository (see below). Tipp: GitHub Desktop is great if you are unfamiliar with Git's command line interface. 
* You can preview your local changes using hugo locally (`hugo serve`, see instructions below)
* If the changes are big, it is good practice to create a pull request and ask for a review instead of committing directly to `master`. 
* There is a Github action running that will rerender the site whenever a new commit is made on the master branch and twice per day at 2am and 2pm, to keep the workshop list up to date. Note that the rebuild won't be triggered by changes to the files in the org repo (e.g., the onboarding checklist). In that case, either wait for the next bi-daily automatic rebuild or use the [run workflow button in the Github actions panel](https://github.com/uio-carpentry/uio-carpentry.github.io/actions?query=workflow%3A%22Rebuild+site+and+deploy+to+Github+pages%22) 
* The published site is at https://uio-carpentry.github.io. Usually the rebuild is fast (less than a minute). If it takes very long, have a look at the Github Actions panel, to see if the build has failed.
* If you make changes to the Hugo modules (i.e., add/change/remove modules), use `hugo mod clean` [More info here.](https://gohugo.io/hugo-modules/use-modules/)

### Content Structure - Where to find what?

* Almost all content is in the `content/` directory.
* Each section has its own folder with an `_index.md` that is used as a front page and for configuration. 
* The structure of the menu is defined in `content/_menu/index.html`
* Exception: The reports get imported into `content/reports/` from the `organisational` repo via Hugo modules. Module imports are configured in `config.toml`. To change those files, change them in the source repository.
* Files that get reused (logos) should be in `static/`. When the site is rendered, the files in static end up in the top level, thus they can be linked to via '/myfile.xyz' [(more info)](https://gohugo.io/content-management/static-files/).
* Data that need to be pre-processed by Hugo to create content (e.g. a members list) should be in `data/`.

### Other building blocks of the site

* The theme (Hugo Book) is imported as a hugo module from an external Github repo. See `config.toml`. The theme has a couple of configuration options and `shortcodes` for layouts. [See here.](https://themes.gohugo.io/hugo-book/#configuration)
* The upcoming workshops are piped in from UiOs xml feed and rendered in the agenda. See `layouts/shortcodes/event-feed.html`
* There is a Google Calendar widget that's currently not in use, but you can still find it in `layouts/shortcodes/google-calendar.html`

## How to build and test the site locally?

1. Clone/Fork the repository from Github
2. Install [Go](https://golang.org/) and [Hugo Extended](https://gohugo.io) on your machine. Go is needed so we can use Hugo modules to load the theme. Hugo *extended* is needed because some themes use fancy CSS preprocessing. In principle you could just download and add the Hugo excecutable to the project folder, but it's probably better to install it systemwide: 
   * For Windows, installation via package manager is recommended. For chocolatey, use `choco install golang` and `choco install hugo-extended`. A restart may be required for everything to work. 
   * On Mac, it's easiest to use homebrew with `brew install go` and `brew install hugo`. Homebrew automatically installs the extended version of Hugo.
3. Run `hugo server` in the project directory (optional: add `-D` to also render drafts). If you are experiencing issues, try to run `hugo mod get` to (re)load all the modules.
4. Navigate to http://localhost:1313 to see the site. The local server has *live reload*, so changes to the source code will be reflected immediately.

## How to update the theme

The ([theme](https://themes.gohugo.io/hugo-book/)) is loaded as a Hugo Module. It is fixed to a particular version (i.e., a particular commit in the source repo). That way, upstream changes to the theme won't accidentally break our site. However, at some point it might make sense to update the theme with the latest upstream changes. To do that, clone the repo and run `hugo mod get github.com/alex-shpak/hugo-book` in the command line ([more info](https://gohugo.io/commands/hugo_mod_get/)). This will update the tagged version number in the `go.mod` file. Commit the changed version number, and the next time the site is rebuilt, the new version will be used. 
## Contribute

Issues and pull requests are welcome!
If you have questions file an issue on Github.

## License

**author:** Carpentry@UiO members  
**copyright:**  
- 2020, Carpentry@UiO members'  
- Governance docs and Carpentry@UiO logo: [![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)  
- Everything else(?): [![CC0](http://i.creativecommons.org/p/zero/1.0/88x31.png)](http://creativecommons.org/publicdomain/zero/1.0/)
