all: Markov.pdf
Markov.pdf: Markov.tex
	latexmk -quiet -bibtex -pvc -f -pdf -pdflatex="xelatex -synctex=1 -interaction=nonstopmode" -use-make Markov.tex
.PHONY: clean
clean:
	latexmk -CA -bibtex
