# make the strong coupled plasma CUDA code

CC = nvcc
CFLAGS = -Xptxas -v 
SM13 = -arch=sm_13 -D__MY_ARCH__=130
SM20 = -arch=sm_20 -D__MY_ARCH__=200
FAST = -ftz=true -prec-div=false -prec-sqrt=false -use_fast_math


# if no specific compilation is selected use fast option
all: fast

# TODO: there is new NVIDIA hardware avaiable - adjust compilation
# issue #5

# best for hardware architectur SM_13
13: plasma.kernel plasma.hpp vector.hpp random/* main.cu parameters.hpp utilities.hpp makefile
	$(CC) $(CFLAGS) $(SM13) main.cu -o scp.exe

# best for hardware architectur SM_20 + no fast math
slow: plasma.kernel plasma.hpp vector.hpp random/* main.cu parameters.hpp utilities.hpp makefile
	$(CC) $(CFLAGS) $(SM20) main.cu -o scp.exe

# best for hardware architectur SM_20 + with fast math
fast: plasma.kernel plasma.hpp vector.hpp random/* main.cu parameters.hpp utilities.hpp makefile
	$(CC) $(CFLAGS) $(SM20) $(FAST) main.cu -o scp.exe

# remove the executable
clean:
	rm -f *.exe
