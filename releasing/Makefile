VERSION = 0.1.1111

OUTDIR = Udapi-$(VERSION)

all: clone doc

clone:
	mkdir -p $(OUTDIR)

	git clone https://github.com/udapi/udapi-perl.git $(OUTDIR)/udapi-perl
	rm -rf $(OUTDIR)/udapi-perl/.git

	git clone https://github.com/udapi/udapi-python.git $(OUTDIR)/udapi-python
	rm -rf $(OUTDIR)/udapi-python/.git

doc:    perldoc pydoc javadoc

pydoc:
	mkdir -p $(OUTDIR)/doc/python
	export PYTHONPATH=udapi-python/:$PYTHONPATH && pydoc -w udapi.core.node.Node
	mv udapi.core.node.Node.html $(OUTDIR)/doc/python

tgz:
	tar -czf $(OUTDIR).tgz $(OUTDIR)

clean:
	rm -rf $(OUTDIR)

