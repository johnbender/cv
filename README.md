# Curriculum Vitae

This repository is a simple CV targetted at graduate admissions. It is based on the class file provided at this [blog](http://linux.dsplabs.com.au/resume-writing-example-latex-template-linux-curriculum-vitae-professional-cv-layout-format-text-p54/).

## Build Instructions

This CV is built using the TeX Live LaTex distribution from the `indicium_vitae` yaml file. Assuming Ruby, `rake`, and `pdflatex` are in the execution path:

    $ rake pdf

Or if you just want to view the TeX output:

    $ rake tex

Soon there will also be HTML output driven by the same data.
