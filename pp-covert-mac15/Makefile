CFLAGS=-O1 -I /usr/local -fPIC -std=gnu99
CC=gcc

TARGETS=sender receiver sender_debug receiver_debug

UTILS=util.o

all: $(TARGETS) $(DEBUGTARGETS)
	cp sender pp-llc-send
	cp receiver pp-llc-recv

%.o: %.c
	$(CC) $(CFLAGS) -c $<

%_debug.o: %.c
	$(CC) $(CFLAGS) -DDEBUG -c $< -o $@

$(TARGETS): %:%.o util.o
	$(CC) $(CFLAGS) $^ -o $@


.PHONY:	clean

clean:
	rm -f *.o $(HELPERS) $(TARGETS) pp-llc-send pp-llc-recv
