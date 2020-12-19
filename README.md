## University of Oslo Carpentry

This is the source code for the Github page of Carpentry at UiO. 
You can view the website [here](http://uio-carpentry.github.io/).
This site is mostly used for internal activities. 
If you are interested in participating in one of our workshops, please see [this page](https://www.ub.uio.no/english/courses-events/courses/other/Carpentry/)

## How to make changes to the content

* Changes can be made directly to the markdown files. Their is a Github action running that will rerender the site whenever a new commit is made on the main branch. 
* Content is mostly in `/content`. The directory structure should be fairly self-explanatory.
* To see the refreshed site after changes, wait for a few seconds, then go to https://uio-carpentry.github.io/?version=[somerandomcharacters]. Change [somerandomcharacters] to something random. This can be faster then waiting for the CDN to notice the changes [(see)](https://stackoverflow.com/questions/24851824/how-long-does-it-take-for-github-page-to-show-changes-after-changing-index-html).


## How to Build Locally

1. Clone the repository from Github
2. Install [Go](https://golang.org/) and [Hugo Extended](https://gohugo.io) on your machine. Go is needed so we can use Hugo modules to load the theme. Hugo *extended* is needed because some themes use fancy CSS preprocessing. 
   * For Windows, installation via package manager is recommended. For chocolatey, use `choco install golang` and `choco install hugo-extended`. A restart may be required for everything to work. 
   * On Mac, it's easiest to use homebrew with `brew install go` and `brew install hugo`. Homebrew automatically installs the extended version of Hugo.
3. Run `hugo server` in the project directory (optional: add `-D` to also render drafts). If you are experiencing issues, try to run `hugo mod get` to (re)load all the modules.
5. Navigate to http://localhost:1313 to see the site. The local server has *live reload*, so changes to the source code will be reflected immediately.

## Contribute

Issues and pull requests are welcome!
If you have questions, please contact the maintainers.
