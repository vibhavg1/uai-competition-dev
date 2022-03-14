# test-page1
https://uaicompetition.github.io/test-page1/

## TLDR

### Dev mode
(skip if we only add md files)

`git clone repository`

commands for docker for environment build
* `docker build -t ruby-environment .`
* `docker run --volume="$PWD:/usr/src/app" -it ruby-environment bundle install`
* `docker build -t minimal-mistakes .`

command for rendering website in local
* `docker run --volume="$PWD:/usr/src/app" -p 4000:4000 -t minimal-mistakes`

command for deployment
* `docker run --rm -it --volume="$PWD:/srv/jekyll" --volume="$PWD:/usr/src/app" --env JEKYLL_ENV=production jekyll/jekyll:3.8 jekyll build`

### Important files
* _config.yml: configuration files to set up default parameters
* _data/navigation.yml: menu top and sidebar (define link to others here)
* _pages: storing page files or templates
* _posts: storing blog posts, Announcements are posts
* _summary and _leaderboards: collections of web pages for Summary and Leaderboards

### Adding content

#### contents using pages (single mark down file)
* home file showing welcome message: index.md
* file formats: _pages/roots/file-formats/*.md
* competition-entry: _pages/roots/competition-entry/*.md
* introduction: _pages/roots/information/introduction.md
* imporatant dates: _pages/roots/information/important-dates.md

#### contents using posts (like blog posts)
announcements are posts.
copy one of the files, modify the data and title of the file, and edit contents.
the post will be organized by category.
* _posts/*.md

#### contents using collections (group of pages)
summary and leader boards are collections
* _summary/*.md: add files for summary
* _leaderboards/*.md: add files for leader boards

### Links of MD files
see https://jekyllrb.com/docs/permalinks/
using `permalink: /:title/` in config casued several errors.
