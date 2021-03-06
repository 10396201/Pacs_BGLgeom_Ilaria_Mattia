# ====================================================================
#   					"BGLgeom library"
#      Course on Advanced Programming for Scientific Computing
#                     Politecnico di Milano
#                         A.Y. 2015-2016
#
#		Copyright (C) 2017 Ilaria Speranza & Mattia Tantardini
#=====================================================================

# Inlcuding general Makefile.in
MAKEFILEH_DIR = ../
include $(MAKEFILEH_DIR)/Makefile.inc

# Including Makefile.inc of the local folder
-include Makefile.inc

#======================================================================

.PHONY: all clean distclean help doc exec

.DEFAUL_GOAL: help

help:
	@echo "make help: ----- Prints this help"
	@echo "make all: ------ Makes executable and documentation"
	@echo "make exec: ----- Makes executable"
	@echo "make test: ----- Makes the test"
	@echo "make doc: ------ Makes documentation"
	@echo "make clean: ---- Cleans all object files"
	@echo "make distclean:  Cleans all"
	@echo ""
	@echo "REMEMBER: without specifying RELEASE=yes inbetween 'make' and"
	@echo "          its target, the target will be built in debug mode."
	@echo "REMEMBER: use 'make -B test' if you previously compiled the"
	@echo "          main executable."

all: exec doc clean

exec: $(OBJS_OTHER) $(EXEC)

test: $(OBJS_OTHER) $(EXEC_TEST)

$(TARGET_DIR)/%: $(BUILD_DIR)/%.o
	@mkdir -p $(TARGET_DIR)
	$(CXX) $(CXXFLAGS) $(CPPFLAGS) $(OBJS_OTHER) $< -o $@ $(LDLIBS)

$(BUILD_DIR)/%.o: $(SOURCE_DIR)/%.cpp
	@mkdir -p $(BUILD_DIR)
	$(CXX) $(CXXFLAGS) $(CPPFLAGS) -c $< -o $@

doc:
	@mkdir -p $(DOC_DIR)
	doxygen Doxyfile
	$(MAKE) -C $(DOC_DIR)/latex

clean:
	-rm -rv $(BUILD_DIR)

distclean: clean
	-rm -rv $(TARGET_DIR)
	-rm -rv $(DOC_DIR)

