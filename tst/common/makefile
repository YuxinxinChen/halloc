include ../common-def.mk

TGT=libcommontest.a
SRC_C=*.cu
SRC_H=*.h
SRC=$(SRC_C) $(SRC_H)
TMP=$(TGT) *~ \#*

ARCH := -gencode arch=compute_30,code=sm_30 \
	-gencode arch=compute_35,code=sm_35 \
	-gencode arch=compute_60,code=sm_60 \
	-gencode arch=compute_70,code=sm_70

FLAGS= $(ARCH) -O3 -rdc=true -lib -I../include
ifeq ($(WITH_SCATTER), 1)
FLAGS += -DWITH_SCATTER
endif

build: $(TGT) 
$(TGT):	$(SRC) makefile
	nvcc $(FLAGS) -o $(TGT) $(SRC_C)

clean:
	rm -f $(TMP)
