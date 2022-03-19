CXX = clang++
CXXFLAGS_DEBUG = \
	-std=c++20 \
	-glldb -g3 \
	-Wall -Wextra -Wpedantic -Werror=pedantic \
	-Wconversion -Wsign-conversion -Wfloat-equal \
	-Wshadow -Wunreachable-code \
	-fsanitize=address -fsanitize=undefined -fsanitize=leak \
	-fno-sanitize-recover=all -fsanitize=float-divide-by-zero \
	-fsanitize=float-cast-overflow

CXX_INCLUED = --include-directory=./include

CXXFLAGS_RELEASE = \
	-std=c++20 -O3 -DNDBUG -Wall

all: solution

solution: solution.cpp
	$(CXX) $(CXX_INCLUED) $(CXXFLAGS_DEBUG) solution.cpp -o solution.out
	./solution.out

opt: solution.cpp
	$(CXX) $(CXX_INCLUED) $(CXXFLAGS_RELEASE) solution.cpp -o solution.out
	./solution.out

.PHONY: clean

clean:
	rm -rfv *.out *.dSYM __pycache__ .DS_Store
