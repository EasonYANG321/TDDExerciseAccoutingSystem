TARGET:=ut_run

GXX:=clang++
SRC_DIRS:=.
C_SRCS:=$(foreach d, $(SRC_DIRS), $(wildcard $d/*.c))
CXX_SRCS:=$(foreach d,$(SRC_DIRS), $(wildcard $d/*.cpp))
C_OBJS:=$(C_SRCS:.c=.o)
CXX_OBJS:=$(CXX_SRCS:.cpp=.o)
GTEST_DIR:=../googletest/googletest
FLAGS:=-I$(GTEST_DIR)/include -I . 
LDFLAGS:=-L$(GTEST_DIR)/build -lgtest -lstdc++ 

$(TARGET) : $(CXX_OBJS) $(C_OBJS)
	echo $(LDFLAGS)
	echo $(CXX_SRCS)
	$(GXX) -o $@ $^ $(LDFLAGS)

$(C_OBJS) : %.o : %.c
	$(GXX) -c -o $@ $^ $(FLAGS)

$(CXX_OBJS) : %.o : %.cpp
	echo $@
	$(GXX) -c -o $@ $^ $(FLAGS)

clean:
	-rm $(C_OBJS) $(CXX_OBJS) $(TARGET)

