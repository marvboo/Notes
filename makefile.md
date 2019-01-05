
Just edit the "MODIFY" section with a name for your executable, and define the include paths, libraries, and library paths.
```

	# makefile
	# use vim :set list to show invisible characters.
	# 	(makefiles use TAB characters)
	#
	#  	make clean
	#	make VERSION=DEBUG

	#       make clean
	#	make VERSION=PROFILE

	#	make clean
	#	make VERSION=RELEASE

	VERSION = DEBUG

	DEBUG_CFLAGS = -g #-Og (enables optimizations that do not interfere with debugging)
	PROFILE_CFLAGS = -pg
	RELEASE_CFLAGS = -Ofast

	ifeq "$(VERSION)" "PROFILE"
	CFLAGS = $(PROFILE_CFLAGS)
	else
	ifeq "$(VERSION)" "DEBUG"
	CFLAGS = $(DEBUG_CFLAGS)
	else
	ifeq "$(VERSION)" "RELEASE"
	CFLAGS = $(RELEASE_CFLAGS)
	endif
	endif
	endif

	CXX = g++
	CC = $(CXX)
	CXXFLAGS = $(CFLAGS)
	CXXFLAGS += -MMD -MP -std=c++14 -Wall -pedantic -Weffc++ -Wextra -pthread


	###################### MODIFY #########################################
	EXEC = nameOfYourExecutable

	# define directories containing header files other than /usr/include
	INCLUDES = -Isrc#-I../include

	# define library paths in addition to /usr/lib
	LFLAGS = #-L../lib

	# define libraries to link into executable:
	# to link in x library (libx.so or libx.a), use -lx
	LDLIBS = #-lx -ly

	###################### END MODIFY ######################################

	vpath %.cpp src		#look for .cpp files in currentdir/src
	vpath %.h src

	SRC = $(wildcard *.cpp) $(wildcard src/*.cpp)
	OBJS=$(SRC:.cpp=.o)
	DEP=$(SRC:.cpp=.d)
	-include $(DEP)

	.PHONY: clean

	all: $(EXEC)
		rm -f $(DEP)
		@echo project compiled

	$(EXEC): $(OBJS)
		$(CXX) $(CXXFLAGS) $(INCLUDES) -o $(EXEC) $(OBJS) $(LFLAGS) $(LDLIBS)

	# suffix replacement rule for building .o's from .c's
	# it uses automatic variables $<: the name of the prerequisite of
	# the rule(a .c file) and $@: the name of the target of the rule (a .o file)
	# (see the gnu make manual section about automatic variables)
	#  $< is the name of the first dependency
	#  $@ is the filename of the current target
	.cpp.o:
		$(CXX) $(CXXFLAGS) $(INCLUDES) -c $< -o $@

	clean:
		rm -f $(OBJS) $(EXEC) $(DEP) core

	rebuild:
		rm -f $(DEP) core

```
