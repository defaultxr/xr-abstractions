REST = pdx7

all: html tex pdf 

tex:
	rst2latex --documentclass=scrartcl $(REST).txt $(REST).tex

pdf: tex
	pdflatex $(REST).tex

html:
	rst2html --stylesheet="default.css" $(REST).txt $(REST).html

clean:
	rm $(REST).tex $(REST).html $(REST).pdf $(REST).aux $(REST).log $(REST).out
