all: octave.log
	$(eval OCTVTABSM=$(shell grep _MTAB $< | sed 's/_MTAB//g' | sed ':a;N;$!ba;s/\n/ /g'))
	$(eval OCTVTABSN=$(shell grep _NTAB $< | sed 's/_NTAB//g' | sed ':a;N;$!ba;s/\n/ /g'))
	$(foreach i, $(OCTVTABSM), sed -n '/^$i_MTAB/,/^$i_MEND/{p;/^$i_MEND/q}' $< | grep -v $i_MTAB | grep -v $i_MEND | grep -v '#' | sed 's/\=/\&/g' | sed 's/$$/\\\\ \\hline/g' > $i_tab.tex;)
	$(foreach i, $(OCTVTABSN), sed -n '/^$i_NTAB/,/^$i_NEND/{p;/^$i_NEND/q}' $< | grep -v $i_NTAB | grep -v $i_NEND | grep -v '#' | sed 's/\=/\&/g' | sed 's/$$/\\\\ \\hline/g' > $i_tab.tex;)

octave.log: circuitanalysis.m
	octave $< > $@

clean:
	@rm -f octave.log octave-workspace *.eps *~ *.tex

.PHONY: all clean
