CC = gcc
CFLAGS ?= -Wall -Wextra -g
OBJ = main.o utils.o
TARGET = my_program

all: $(TARGET)

$(TARGET): $(OBJ)
	$(CC) $(CFLAGS) -o $@ $^

%.o: %.c utils.h
	$(CC) $(CFLAGS) -c $< -o $@

clean:
	rm -f $(OBJ) $(TARGET)

test: all
	./$(TARGET)

.PHONY: all clean test

help:
	@echo "MEDS Project Build System"
	@echo "Usage:"
	@echo "  make       - Compiles the project"
	@echo "  make clean - Removes object files and the binary"
	@echo "  make test  - Builds and runs the program"
	@echo "  make help  - Shows this message"

.PHONY: all clean test help