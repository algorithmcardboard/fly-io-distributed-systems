.PHONEY: install
install:
	go install .

.PHONY: download-maelstrom

MAELSTROM_URL := https://github.com/jepsen-io/maelstrom/releases/download/v0.2.4/maelstrom.tar.bz2
MAELSTROM_ARCHIVE := maelstrom.tar.bz2
MAELSTROM_DIR := ../maelstrom

download-maelstrom:
	curl -L -o $(MAELSTROM_ARCHIVE) $(MAELSTROM_URL)
	mkdir -p $(MAELSTROM_DIR)
	tar --strip-components=1 -xjf $(MAELSTROM_ARCHIVE) -C $(MAELSTROM_DIR)
	rm $(MAELSTROM_ARCHIVE)


.PHONY: run
run: install
	../maelstrom/maelstrom test -w echo --bin ~/go/bin/maelstrom-echo --node-count 1 --time-limit 10