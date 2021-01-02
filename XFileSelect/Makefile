

	LIB_DIR := ../libxputty/libxputty/
	HEADER_DIR := $(LIB_DIR)include/

	# include path for library headers
	INCLUDES := -I. -I$(HEADER_DIR) 
	# link flags to dynamic link cairo and X11 (default)
	LDFLAGS += -fPIC -Wl,-z,noexecstack -Wl,--no-undefined `pkg-config --cflags --libs cairo x11` -lm
	CXXFLAGS += -O2 -D_FORTIFY_SOURCE=2 -Wall -fstack-protector 
	DEBUG_CXXFLAGS += -g -D DEBUG

	BLUE = "\033[1;34m"
	RED =  "\033[1;31m"
	NONE = "\033[0m"

	XFILESELCT_SOURCES := $(wildcard *.c)
	XFILESELCT_OBJ := $(patsubst %.c,%.o,$(XFILESELCT_SOURCES))
	EXEC_FILES := $(patsubst %.c,%,$(XFILESELCT_SOURCES))

.PHONY : all clean

all: $(EXEC_FILES) 

debug: CXXFLAGS = $(DEBUG_CXXFLAGS) 
debug: all

clean:
	rm -f $(XFILESELCT_OBJ) $(EXEC_FILES)

$(HEADER_DIR)*.h:
	@echo $(RED)You need to build libxputty before build XFileSelet!!$(NONE)
	@echo $(RED)Just build from the top directory to keep the order$(NONE)
	@exit 1

$(XFILESELCT_OBJ): $(XFILESELCT_SOURCES) $(HEADER_DIR)*.h
	$(CC) -c $(patsubst %.o,%.c,$@) -o $@  $(INCLUDES) $(LDFLAGS)

$(EXEC_FILES): $(XFILESELCT_OBJ)
	$(CC) $(CXXFLAGS) -Wall $(patsubst %,%.c,$@) -L. $(LIB_DIR)libxputty.a -o $@  $(INCLUDES) $(LDFLAGS)


