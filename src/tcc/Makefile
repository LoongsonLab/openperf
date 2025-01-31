NAME = riscv-tcc-$(mainargs)

mainargs ?= ref

BENCH_LIBS = bench openlibm soft-fp

SRCS := tcc.c my_qsort.c fs.c ./configs/$(mainargs)-config.c ./resources/resources-$(mainargs).S

INC_DIR += 	../common/openlibm/include \
			../common/openlibm/src \
			./include \
			../common/bench/include


include $(AM_HOME)/Makefile.app

WORK_DIR  = $(shell pwd)

BENCH_LINKAGE += $(addsuffix -$(ARCH).a, $(join \
					 $(addsuffix /build/, $(addprefix $(WORK_DIR)/../common/, $(BENCH_LIBS))), \
					 $(BENCH_LIBS) ))
#override variable LINKAGE, we should link soft-fp first.
LINK_FILES   = $(OBJS)  $(BENCH_LINKAGE)\
  $(AM_HOME)/am/build/am-$(ARCH).a \
  $(addsuffix -$(ARCH).a, $(join \
    $(addsuffix /build/, $(addprefix $(AM_HOME)/libs/, $(LINK_LIBS))), \
    $(LINK_LIBS) \
))

