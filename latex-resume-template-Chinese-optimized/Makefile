LATEXMK ?= latexmk
LATEXMK_FLAGS ?= -xelatex -interaction=nonstopmode -halt-on-error
JOB ?= job_1
JOB_SOURCE := Template/resume-$(subst _,-,$(JOB)).tex

.PHONY: all job clean

all:
	$(LATEXMK) $(LATEXMK_FLAGS) Template/main.tex

job:
	$(LATEXMK) $(LATEXMK_FLAGS) $(JOB_SOURCE)

clean:
	$(LATEXMK) -C Template/main.tex
	$(LATEXMK) -C Template/resume-job-1.tex
	$(LATEXMK) -C Template/resume-job-2.tex
