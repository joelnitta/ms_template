# ms_template

An example repository for automated creation of scientific manuscripts in `pdf` 
and Microsoft Word format for submission to journals.

## Rendering manuscripts

To render the manuscript, run `render.R` in the `code` folder: 
`Rscript code/render.R`.

Rendered output will show up in the `results` folder in `pdf` and `docx` format.

## Adjusting styles

Adjust the `csl` (bibliography style), `docx` (MS Word format such as line 
spacing, fonts, etc), and `sty` (misc. `latex` formatting) files in the `ms` 
folder as needed to produce rendered manuscripts with appropriate styling for 
your journal of choice without the need to edit the `Rmd` file (hardly). 

For details, see the `Rmd` file and the [rendered output of this example](https://github.com/joelnitta/ms_template/blob/master/example_output/ms.pdf).

## Dependencies

Basically, `R`, various `R` packages, `pandoc`, and `latex`. But see below.

## Running with Docker

Rather than specify all the various dependencies needed in detail, [I recommend 
using this Docker image](https://hub.docker.com/r/rocker/verse) from the [Rocker
project](https://www.rocker-project.org/).

To use it, first [install Docker](https://docs.docker.com/install/) and clone 
this repository.

Navigate to the cloned repository (where `/path/to/repo` is the path on your 
machine), and launch the container:

```
cd /path/to/repo
docker-compose up -d
```

Enter the container:

```
docker exec -it ms_template_rmd_1 bash
```

Inside the container, install the `here` package, then run `render.R`:

```
Rscript -e 'install.packages("here")'
Rscript code/render.R
```

When it's finished, exit the container and take it down:

```
exit
docker-compose down
```