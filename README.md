# PhD Thesis Template 
This template is created based on Thesis requirements of NCBS-TIFR. 

# Structure

* `main.tex` : Standalone file which will combine all aspects of the thesis. You can customize view and arrangement of thesis from this file
* `main_ref.bib` : All bibliography (you can have multiple files as well. Just change details in `helpers\bib.tex`) 
* `front_matter\` : Includes all front matter files like declarations, certificate etc. 
* `chapters\` : Includes all chapters. To organize better, keep separate document for each chapter. 
* `figs\` : All figures
* `helpers\` : Acronyms and bibliography helper file
* `appendix\` : Appendices 
* `script.bat` : Compilation script (for Windows)


# Compilation
To compile all the structures (with `pdflatex`), follow following procedure

## Windows 
Just run `script.bat` (double click it)

## Unix and Mac 
use following procedure. You can check sample code in `script.bat`.

1. First Compile once to generate `.idx` file 
2. Make index from `.idx` file with `makeindex` command
3. Make `.acn` and `.acr` files from output produced from `makeindex`
4. Run `bibtex` on all `.aux` files produced (all chapters and appendix will produce separate `.aux` file to have separate bibliography)
5. Run `pdflatex` twice


## Technical details for making index and glossary

to create index run 

	makeindex  main.nlo -s nomencl.ist -o  main.nls

to create glossary run

	makeindex -s main.ist -t main.alg -o main.acr main.ac

## Technical details to have bibliography separate for separate chapters

To include separate references for each chapter, `natbib` and `chapterbib` packages are used. To use these packages, we have to add chapter files as "\include{}" instead "\input{}". Also we need to compile each chapter aux file seperately. We also need to include biblography in every chapter. It will follow this sequence,


	pdflatex main.tex
	bibtex chapter1.aux
	bitbex chapter2.aux ... and so on
	pdflatex main.tex
	pdflatex main.tex
