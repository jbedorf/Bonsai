CXX = g++
CC  = gcc
LD  = g++
F90 = gfortran

OMPFLAGS  = -fopenmp
OMPFLAGS += -D_GLIBCXX_PARALLEL

OFLAGS = -O3 -g -Wall
# OMPFLAGS=

CXXFLAGS =  -fPIC $(OFLAGS) -Wstrict-aliasing=2 $(OMPFLAGS)



LDFLAGS = 

SRCPATH = ./
SRC = density.cpp
OBJ = $(SRC:%.cpp=%.o)

SRC1 = read_tipsy.cpp
OBJ1 = $(SRC1:%.cpp=%.o)

PROG  = density
PROG1 = read_tipsy

RM = /bin/rm

all:	  $(PROG) $(PROG1)


$(PROG): $(OBJ) 
	$(LD) $(LDFLAGS) $^ -o $@ $(OMPFLAGS)

$(PROG1): $(OBJ1)
	$(LD) $(LDFLAGS) $^ -o $@ $(OMPFLAGS)

%.o: $(SRCPATH)/%.cpp
	$(CXX) $(CXXFLAGS) -c $< -o $@


clean:
	/bin/rm -rf *.o $(PROG)  $(PROG1)

$(OBJ): boundary.h  density.h  memalign_allocator.h  morton_key.h  Node.h  Particle.h  vector3.h  wtime.h
$(OBJ1): boundary.h  density.h  memalign_allocator.h  morton_key.h  Node.h  Particle.h  vector3.h  wtime.h read_tipsy.h

build_tree.ptx: $(CUDAKERNELSPATH)/support_kernels.cu $(INCLUDEPATH)/node_specs.h
compute_properties.ptx: $(CUDAKERNELSPATH)/support_kernels.cu $(INCLUDEPATH)/node_specs.h
compute_propertiesD.ptx: $(CUDAKERNELSPATH)/support_kernels.cu $(INCLUDEPATH)/node_specs.h
dev_approximate_gravity.ptx: $(CUDAKERNELSPATH)/support_kernels.cu $(INCLUDEPATH)/node_specs.h
dev_approximate_gravity_let.ptx: $(CUDAKERNELSPATH)/support_kernels.cu $(INCLUDEPATH)/node_specs.h
timestep.ptx: $(CUDAKERNELSPATH)/support_kernels.cu $(INCLUDEPATH)/node_specs.h
sortKernels.ptx: $(CUDAKERNELSPATH)/scanKernels.cu  $(CUDAKERNELSPATH)/support_kernels.cu $(INCLUDEPATH)/node_specs.h
parallel.ptx: $(CUDAKERNELSPATH)/support_kernels.cu $(INCLUDEPATH)/node_specs.h








