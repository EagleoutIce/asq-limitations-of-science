# Alle Bilder
TEXFILES := $(shell ls *.tex)
PDFFILES := $(addsuffix .pdf,$(basename $(TEXFILES)))

JOBCOUNT := 9

CLEANTARGETS := .log .aux .out .ind .bbl .blg .lof .lot .toc .idx .acn .acr .alg .glg .glo .gls .fls .fdb_latexmk .auxlock .md5 .SATZE .ZSM .UB .TOP .listing .upa .ilg .TOPIC .DEFS -slave.pdf .atfi
CLEANTARGET  := CompilexClean

void = return 0;

CompilexClean = echo "\033[38;2;255;191;0m> Lösche temporäre Dateien...[m" && \
     for fd in $(CLEANTARGETS); do rm -f $(OUTPUTDIR)*$$fd; done

# Kompilieren
all:
	@echo "Printmode disabled"
	@$(MAKE) --no-print-directory $(PDFFILES) CLEANTARGET=void -j $(JOBCOUNT) --output-sync=line
	@$(MAKE) --no-print-directory clean

%.pdf: %.tex global-config.src
	sltx -q compile --root -rimage-noprint-pdflatex.recipe $<
	@$(call $(CLEANTARGET))

clean:
	@$(call $(CLEANTARGET))
	sltx cls

cleanpdf:
	rm -f *.pdf
