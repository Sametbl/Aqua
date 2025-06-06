# Author: Hai Cao -- cxhai.sdh221@hcmut.edu.vn
# Copyright 2024

TOP=testbench
SEED=2

## Do NOT change the content below unless you know what you're doing
FLAGS =  --binary -Wall --trace --sv --timing
FLAGS += -O3 --compiler gcc -CFLAGS -std=gnu++20
FLAGS += -x-initial unique
FLAGS += -x-assign unique
FLAGS += --assert
FLAGS += --build -j 0 --quiet
LFLAGS = --lint-only --sv --timing --quiet
LFLAGS = --lint-only --sv --timing --quiet --lint-only ../04_verilator/conf.vlt

RFLAGS =  +verilator+seed+$(SEED)
RFLAGS += +verilator+quiet

TARGET = -f ../00_src/flist.f

.PHONY: lint
lint:
	@echo "-> LINT"
	verilator $(LFLAGS) $(TARGET)

.PHONY: all
all: clean sim run
.PHONY: sim
sim:
	@echo "-> SIMULATION"
	@rm -rf ./obj_dir *.vcdt
	verilator $(FLAGS) $(TARGET)

.PHONY: run
run:
	@echo "-> RUN"
	./obj_dir/V$(TOP) $(RFLAGS)

.PHONY: wave
wave:
	gtkwave wave.vcd wave.gtkw 2>/dev/null

.PHONY: clean
clean:
	@echo "-> CLEAN"
	@rm -rf ./obj_dir *.vcdt

