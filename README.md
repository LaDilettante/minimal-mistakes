# Anh Le's blog

Theme from **[Minimal Mistakes](http://mmistakes.github.io/minimal-mistakes)*.

I describe my personal modifications below:

- Use Algolia for better search. Github pages only allows running `jekyll build`, not `jekyll algolia`, so set up `.travis.yml` to run `jekyll algolia` each time there is an update. `ALOGLIA_API_KEY` (admin key) is set on Travis' environment variable.

- Use Google Analytics and Google Site Verification.

- Use Disqus with Guest commenting turned on (do this on Disqus website)

### Installation

- Install Jekyll (including Ruby, `gem install bundler jekyll`)
- Clone minimal mistakes github
- Migrate content (posts, pages)
- Get rid of `gemspec` in Gemfile and .gemspec file (Don't really understand this step though. Gemspec seems like a development tool for the author to develop the theme into a gem. Since I'm only an user of the gem I don't need it?)

### Setting up
- `bundle update` (`bundle clean --force` if necessary)
- Check site configurations in `_config.yml`
- Check default YAML front matter in `_config.yml` (i.e. how posts, pages, tags, categories appear by default) 
- Change `_data/navigation.yml` for header nav bar
- Include Mathjax by inserting into `_include/head/custom.html` the following

```
<!-- Mathjax script -->
<script type="text/javascript"
        src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>
```

### Nice to have

- Setting up Algolia as search (in `_config.yml` and setting up `.travis.yml`)
- Setting up htmlproofer to check dead links and images in `.travis.yml` (See Jekyll guide)
- Setting up TravisCI to run htmlproofer to check for dead links and images

### Copy to server (when I still hosted at Duke)

The idea is to mount Duke CIFS (via VPN). Build the local site. Then copy the local site to `public_html/` in the mounted CIFS drive.

- `gem install github-pages` if jekyll is not set up
- Go to `/media/aql3/personal-webpage`
- `sudo rsync -av /link/to/personal-webpage/_site/ public_html/` (a = all, v = verbose)

### Some commands to remember

To write Rmd blog post in Rstudio, make sure that [`build.R`](https://raw.githubusercontent.com/yihui/knitr-jekyll/gh-pages/build.R) is included in the root jekyll directory (this is undocumented):
- `which jekyll`
- `servr::jekyll(command='/home/anh/.rvm/gems/ruby-2.3.0/wrappers/jekyll build')`

### base_path

Remove {{ site.url }} from {{ site.url }}{{ site.baseurl }} so that local development works
