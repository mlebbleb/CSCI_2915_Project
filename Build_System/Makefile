# Example Makefile (use in bash on windows)
#
# This is an example Makefile which can be used in MacOS and linux and in windows using the bash
# terminal. The file is used for automation of files using a relatively basic project organized
# into multiple directories with a direcory for source files, header files, object files and
# exicutable binaries
#
# To test out this file, place a copy of this make file in an empty directory, go into the terminal
# and enter the comand make init. This will create all the directries used by this makefile
#
# To change the compiler used, change the value of to the dessired compiler


CXX = g++
CPPFLAGS = -g -Wall
OPT_CPPFLAGS = -O2 -Wall -DNDEBUG

RM=rm
RD=rmdir
MD=mkdir

BIN = main

HDR_DIR = Header
SRC_DIR = Source
OBJ_DIR = Object
BIN_DIR = Binary

SRCS = $(wildcard $(SRC_DIR)/*.cpp)
HDRS = $(wildcard $(HDR_DIR)/*.h)
OBJS = $(patsubst $(SRC_DIR)/%.cpp, $(OBJ_DIR)/%.o, $(SRCS))
BINS = $(BIN_DIR)/$(BIN)

all: $(BINS)


#initialize directories for new project
init: $(HDR_DIR) $(SRC_DIR) $(OBJ_DIR) $(BIN_DIR)

#compile for debuging
$(BINS): $(OBJS)
	$(CXX) $(CPPFLAGS) -o $(BINS) $(OBJS)

$(OBJ_DIR)/%.o: $(SRC_DIR)/%.cpp
	$(CXX) $(CPPFLAGS) -o $@ -c $^ -I $(HDR_DIR)

#create missing directories
$(OBJ_DIR):
	$(MD) $@

$(BIN_DIR):
	$(MD) $@

$(SRC_DIR):
	$(MD) $@

$(HDR_DIR):
	$(MD) $@


#compile optemised binary
release: clean
release:
	$(CXX) $(OPT_CPPFLAGS) -o $(BINS) $(SRCS) -I $(HDR_DIR)

clean: 
	$(RM) $(OBJ_DIR)/* $(BIN_DIR)/* $(TEST_BIN_DIR)/*