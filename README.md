# Curriculum Vitae

This repository is a simple CV targetted at graduate admissions. It is based on the class file provided at this [blog](http://linux.dsplabs.com.au/resume-writing-example-latex-template-linux-curriculum-vitae-professional-cv-layout-format-text-p54/).

## Build Instructions

This CV is built using the TeX Live LaTex distribution from the `indicium_vitae` yaml file. Assuming Ruby, `rake`, and `pdflatex` are in the execution path:

    $ rake pdf

Or if you just want to view the TeX output:

    $ rake tex

In addition you can generate HTML output from the same yaml file with:

    $ rake html

## Deploy Instructions

The Rakefile includes a `gh-pages` task to deploy the cv as both a HTML document and a downloadable pdf. Running:

   $ rake gh-pages

Will run both the `html` and `pdf` targets, checkout the `gh-pages` branch, move the HTML ouput to `index.html`, mv the pdf output to `cv-YEAR-MM.pdf`, and commit the changes. Then deploying to be hosted on github is as simple as:

   $ git push origin gh-pages

As of this writting the resume can be found at [johnbender.github.com/cv](http://johnbender.github.com/cv/) and the pdf can be downloded from the same address by appending `cv-2012-08.pdf`.
