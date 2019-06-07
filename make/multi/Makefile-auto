CXXFLAGS=-std=c++14
OBJECTS=main.o circle_funcs.o

main: $(OBJECTS)
	g++ -o main $(LDFLAGS) $(OBJECTS)

circle_funcs.o: circle_funcs.cpp circle_funcs.h

main.o: main.cpp circle_funcs.h

clean:
	rm $(OBJECTS)
