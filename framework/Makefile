
base:	draft-ejj-teas-ns-framework-00.txt

draft-framework.xml:	draft-framework.md
	kramdown-rfc2629 draft-framework.md > draft-framework.xml

draft-framework.txt:	draft-framework.xml
	xml2rfc draft-framework.xml

draft-ejj-teas-ns-framework-00.txt: draft-framework.txt
	mv -v draft-framework.txt draft-ejj-teas-ns-framework-00.txt

#base:	draft-framework.txt
#
#LIBDIR := lib
#include $(LIBDIR)/main.mk
#
#$(LIBDIR)/main.mk:
#ifneq (,$(shell grep "path *= *$(LIBDIR)" .gitmodules 2>/dev/null))
#	git submodule sync
#	git submodule update $(CLONE_ARGS) --init
#else
#	git clone -q --depth 10 $(CLONE_ARGS) \
#	    -b master https://github.com/martinthomson/i-d-template $(LIBDIR)
#endif

clean:
	rm -f *~

