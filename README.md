# Shiny Website Example
This repository contains a basic, demonstrative example for an [RStudio Community forum post](https://community.rstudio.com/t/rmarkdown-website-using-shiny-prerendered-documents/29333/) relating to RMarkdown documents using the `shiny_prerendered` runtime and Shiny Server. 

## Problem Description

As can be seen in `_site.yml`, page navigation occurs using a navbar, in which the `href` of the individual menu items target the associated `Rmd` files directly. 

When using the `shiny` runtime, the website functions as expected. That is, clicking on a menu item in the navbar will cause the URL to update to `http://<shiny-server>/<targeted-file>.Rmd` and the page to render. 

However, when using the `shiny-prerendered` runtime, the website ceases functioning. That is, clicking on a menu item in the navbar **will still** cause the URL to update to `http://<shiny-server>/<targeted-file>.Rmd`, but instead of rendering the new page, the `index.Rmd` page will simply be refreshed. The same behavior occurs if the URL is manually entered, even without having first visited `index.Rmd`. I assume this is because of the way Shiny Server handles RMarkdown files; that is,

> If a hosted directory does not include a `server.R` file, Shiny Server will look to see if it contains any `.Rmd` files. If so, Shiny Server will host that directory in "R Markdown" mode using `rmarkdown::run` .

Since `rmarkdown::run()` targets `index.Rmd` by default, this is the page that will remain displayed no matter which `Rmd` file is targeted in the URL. 

## Running the Examples

The examples can be viewed either by opening one of the `Rmd` files in RStudio and clicking "Run Document" to trigger the start of a Shiny Server, or by copying the `shiny_runtime` and `shiny_prerendered_runtime` directories to an existing, deployed Shiny Server and navigating to the server in a browser. 
