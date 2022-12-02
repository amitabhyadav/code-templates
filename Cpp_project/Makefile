#Basic Makefile for C++ code

# Specify the compiler to use
CC = g++

# Specify the flags to use during compilation
CFLAGS = -Wall -Iinclude

# Specify the sources to compile
SOURCES = $(wildcard src/*.cpp)

# Specify the objects to create
OBJECTS = $(patsubst src/%.cpp,objects/%.o,$(SOURCES))

# Specify the target executable
TARGET = myprogram

# Specify the build rules
all: $(TARGET)

$(TARGET): $(OBJECTS)
    $(CC) $(CFLAGS) $(OBJECTS) -o $(TARGET)

$(OBJECTS): objects/%.o : src/%.cpp
    $(CC) $(CFLAGS) -c $< -o $@

# Specify the clean rule
clean:
    rm -f $(TARGET) $(OBJECTS)

# Specify the help rule
help:
    @echo "Usage: make [target]"
    @echo ""
    @echo "Available targets:"
    @echo "  all      Build the target executable"
    @echo "  clean    Remove the target executable and object files"
    @echo "  help     Show this help message"
