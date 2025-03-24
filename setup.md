HTML files are constructed as is. Markdown files are constructed as follows:

1. YAML configs at the top of the markdown file specify an HTML layout in "/_layouts"
2. The layout specification captures the markdown content in a variable
3. The variable from (2) is fed to "/_includes/main.html", which is the basis for all pages on the site

Plugins