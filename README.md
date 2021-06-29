# Radical AI's public-facing website
This repo contains the contents of our [public-facing website](https://radicalai.net/)!

## Things to know about the website 
1. Changes to the `gh-pages` branch of this repo are automatically propagated to the website (after some delay time).
2. Our website is now `jekyll` compatable, so content can be easily added and edited using markdown files.
3. While any user with "contributor" status on this repo has push access to the `gh-pages` branch, we will use a (very mild) code review process to make sure any new changes to the website are okay'd by at least one other RadAI member (read on).

## How to update the website's contents
### Getting access to this repo
Ask a member of [our github orgnanization](https://github.com/orgs/radicalAI) to add you as a (1) a member of the organization or (2) an outside collaborator who has access to this repo only.
At the time of this writing, all [collaborators on this repo](https://github.com/radicalAI/radical-ai/graphs/contributors) are members of the github org, and thus would be good people to ask about this.

### Downloading software to host local version of the site
#### Clone this repo
Use the command 
```
git clone git@github.com:radicalAI/radical-ai.git
```
for ssh cloning or 
```
git clone https://github.com/radicalAI/radical-ai.git
```
for https.
#### Download ruby and jekyll
We use `jekyll` to view our local changes to the website before it is published.
`jekyll` produces static webpages (html files) starting from markdown files that contain the content (e.g. text) and layout files that specify how to format the content.
The main reason to use `jekyll` is that markdown files tend to be easier to work with than standard html files.
Because `jekyll` is written in the `Ruby` programming language, it must be installed using the `gem` package manager, which in turn requires installing `Ruby`.
Here are the basic steps (which may take a while...):
1. [Install ruby](https://www.ruby-lang.org/en/documentation/installation/) on your machine using instructions specific to your operating system (e.g. `brew install ruby` for MacOS).
2. add `Ruby` and `gem` to your system path then restart your terminal, e.g. for bash shells: `echo 'export PATH="/usr/local/opt/ruby/bin:/usr/local/lib/ruby/gems/3.0.0/bin:$PATH"' >> ~/.bash_profile` then `source ~/.bash_profile` 
3. Confirm that the `gem` package manager is available by `which gem` or `gem -v` (revisit steps 1--3 if this fails).
4. Use `gem` to install `jekyll` using this command:
```
gem install bundler jekyll
```
5. Confirm that `jekyll` is available by `which jekyll` or `jekyll -v`

If you get stuck, check out the following installation guides
* [Installing Ruby](https://www.ruby-lang.org/en/documentation/installation/)
* [Installing jekyll](https://jekyllrb.com/docs/installation/macos/)

### Hosting a local version of the website
`jekyll` can be used to host a local version of the website using the following command:
```
jekyll serve
```
Note that it must be run from the root directory of this repo, so you might have to `cd ./radical-ai` if you just cloned this repo.

Your terminal will print out the local port where the website will be hosted. It will look something like this
```
            Source: $HOME/git/radical-ai
       Destination: $HOME/radical-ai/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
                    done in 0.063 seconds.
 Auto-regeneration: enabled for '$HOME/git/radical-ai'
    Server address: http://127.0.0.1:4000
```

Open up `http://127.0.0.1:4000` (or equivalent port) in your web browser and check out the current website!

### Making local changes
Now that you have a local server running the website, you can make changes to the content files (e.g. `index.md`. `principles.md`), and these changes will be reflected in the local version your browser is looking at.
For example, `index.md` contains the landing page. 
This file has a bunch of markdown-formatted text in it, plus the following header
```
---
layout: main
---
```
The header tells `jekyll` to format the markdown contents using the layout file `_layouts/main.html`.
This header specifies which other pages (e.g. `principles.md`) should be hyperlinked at the top of the homepage (or any page that uses the "main" layout).

You can edit content directly in the markdown files, and add hyperlinks using [standard markdown format](https://www.markdownguide.org/cheat-sheet/).
For example if I were to add an extra line to the bottom of `index.md` that says
```
Check out [our principles](principles)
```
then this would add a hyperlink to the page `principles.md` at the bottom of the page for `index.md`.
Any edits to the markdown or layout files will be automatically propagated to the local version of the website we are hosting (e.g. `http://127.0.0.1:4000`).

### Getting these changes approved by a pull request
If you have edited the page locally, you might be ready to propagate these changes to the public webpage. 
This should happen by a pull request (PR), rather than a direct `git push`.
For starters, you might want to look at your local changes using `git status` and `git diff` from the repo root directory, and make sure everything looks ok to you.
To proceed with the pull request, you will need to 
1. commit these changes to a **new local branch**
2. push the contents of your local branch to a **new remote branch**
3. use the github.com interface to start the PR merging the new remote branch contents onto the main `gh-pages` branch.

Once the PR is submitted, ask a repo contributor to approve and merge the PR.
Once merged, the new content on `gh-pages` should automatically propagate (after some time) to the public website.
