TARGET = prog
SHELL=/bin/bash

INCDIR = include
SRCDIR = src
OBJDIR = _obj

CC = $(CROSS_COMPILE)gcc
CFLAGS = -std=c11
CFLAGS += -fPIC -O3
# indicate compiler that reentrant versions of C library functions shall be used
CFLAGS += -pthread

COMMIT_ID := $(shell git rev-parse --short HEAD)
CFLAGS += -DCOMMIT_ID_DEF=$(COMMIT_ID)

ifdef DEBUG
	CFLAGS += -g3
	CFLAGS += -save-temps
else
	CFLAGS += -Wall -Wextra -Werror=comment
endif

LIBS = -lm

.PHONY: all

all: default

default: $(TARGET) Makefile

SOURCES = $(wildcard $(SRCDIR)/*.c)
HEADERS = $(wildcard $(INCDIR)/*.h)
OBJECTS = $(patsubst %.c,%.o,$(SOURCES))

$(OBJDIR)/%.o: %.c $(HEADERS)
	@mkdir -p $(OBJDIR)/$(SRCDIR)
	$(CC) $(CFLAGS) -c $< -o $@ -I$(INCDIR)
                
.PRECIOUS: $(TARGET) $(OBJDIR)/$(OBJECTS)

$(TARGET): $(addprefix $(OBJDIR)/,$(OBJECTS))
	$(CC) $(addprefix $(OBJDIR)/,$(OBJECTS)) -Wall $(LIBS) -o $@

.PHONY: clean
clean:
	-rm -rf $(OBJDIR)
	-rm -f $(TARGET)
