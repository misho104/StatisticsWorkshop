PROGNAME      = runSigCalc
SOURCES       = runSigCalc.cc getExclusionSignificance.cc getDiscoverySignificance.cc SigCalc.cc fitPar.cc
INCLUDES      = getExclusionSignificance.h getDiscoverySignificance.h SigCalc.h fitPar.h
OBJECTS       = $(patsubst %.cc, %.o, $(SOURCES))
ROOTCFLAGS   := $(shell root-config --cflags)
ROOTLIBS     := $(shell root-config --libs)
ROOTGLIBS    := $(shell root-config --glibs)
ROOTLIBS     := $(shell root-config --nonew --libs)
CFLAGS       += $(ROOTCFLAGS)
LIBS         += $(ROOTLIBS)
#  Not sure why Minuit isn't being included -- put in by hand
#
LIBS         += -lMinuit
LDFLAGS       = -O

$(PROGNAME):    $(OBJECTS)
		g++ -o $@ $(OBJECTS) $(LDFLAGS) $(LIBS)

%.o : %.cc $(INCLUDES)
	g++ ${CFLAGS} -c  -g -o $@ $<

test:
	@echo $(ROOTCFLAGS)

clean:	
	-rm -f ${PROGNAME} ${OBJECTS}
