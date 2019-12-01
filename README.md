# Introducing SinkDSM at oemof dev meeting 2019

Slides for the talk about DSM modeling (newly introduced SinkDSM) in oemof at dev meeting 2019

## Building PDF slides

```
pandoc -t beamer --pdf-engine=xelatex -o slides.pdf slides.md
```

## Packages you might need

```
sudo apt get install texlive
sudo apt get install texlive-fonts-extra
sudo apt get install pandoc
sudo apt get install xetex
```

Pandoc might be better installed in a [newer version](https://pandoc.org/installing.html).