###############################################################################

LANG1=spa
LANG2=eus

PREFIX1=$(LANG1)-$(LANG2)

BASENAME=matxin-$(PREFIX1)

TARGETS_COMMON=$(PREFIX1).verb_transfer.fst \
	       $(PREFIX1).bilingual.bin \
	       $(PREFIX1).changes.bin \
	       $(PREFIX1).cfg

@ap_include@

###############################################################################

$(PREFIX1).verb_transfer.fst: $(BASENAME).verb_transfer.foma
	foma -f $< $@

$(PREFIX1).bilingual.bin: $(BASENAME).bilingual_mur.xml 
	lt-comp lr $< $@

$(PREFIX1).changes.bin: $(BASENAME).changes_morph.xml
	lt-comp lr $< $@

$(PREFIX1).cfg: $(BASENAME).$(PREFIX1).cfg
	cat $<  > $@

###############################################################################

EXTRA_DIST= $(BASENAME).bilingual_mur.xml \
	$(BASENAME).changes_morph.xml \
	$(BASENAME).changes_sint.dat \
	$(BASENAME).chunk_type.dat \
	$(BASENAME).interchunk_move1.dat \
	$(BASENAME).interchunk_move2.dat \
	$(BASENAME).interchunk_move3.dat \
	$(BASENAME).interchunk_order.dat \
	$(BASENAME).intrachunk_move2.dat \
	$(BASENAME).intrachunk_move.dat \
	$(BASENAME).lexical_selection.dat \
	$(BASENAME).prep.dat \
	$(BASENAME).spa-eus.cfg \
	$(BASENAME).verb_transfer.foma

matxin_spa_eusdir=$(prefix)/share/matxin/$(BASENAME)
matxin_spa_eus_srcdir=$(prefix)/share/matxin/$(BASENAME)

matxin_spa_eus_DATA=$(TARGETS_COMMON)

# All modes are created by the same goal, listing several will just give problems with make -j2
noinst_DATA=modes/$(PREFIX1).mode

install-data-local: install-modes

CLEANFILES = $(TARGETS_COMMON)
clean-local:
	-rm -rf .deps modes

