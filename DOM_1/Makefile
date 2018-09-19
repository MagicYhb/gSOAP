PWD = $(pwd)
GSOAP_ROOT = $(PWD)/../gsoap
WSNAME = add
CC = g++ -g -DWITH_NONAMESPACES
INCLUDE = -I$(GSOAP_ROOT)

#CFLAGS +=  -Wall -I . -g -MMD
#CFLAGS  += `pkg-config --cflags glib-2.0`
CFLAGS += \
		-I./soappcpp2_dir \
		-I./stdsoap2_dir \
		-I./include

SRCS:= \
	./soappcpp2_dir/soapC.c ./stdsoap2_dir/stdsoap2.c ./soappcpp2_dir/soapServer.c ./soappcpp2_dir/soapClient.c ./addserver.c ./addclient.c ./addtest.c 

OBJ_LIST := $(addsuffix .o,$(basename $(SRCS)))

%.o:%.c
	$(CC) $(CFLAGS) -c $^ -o $@

SERVER_OBJS = ./soappcpp2_dir/soapC.o ./stdsoap2_dir/stdsoap2.o ./soappcpp2_dir/soapServer.c $(WSNAME)server.o 
CLIENT_OBJS = ./soappcpp2_dir/soapC.o ./stdsoap2_dir/stdsoap2.o ./soappcpp2_dir/soapClient.c $(WSNAME)client.o $(WSNAME)test.o

all: server
server: $(OBJ_LIST) 
	$(CC) $(INCLUDE) $(CFLAGS) -o $(WSNAME)server $(SERVER_OBJS) 

client: $(OBJ_LIST)
	$(CC) $(INCLUDE) $(CFLAGS) -o $(WSNAME)test $(CLIENT_OBJS)

clean:
	rm -f *.o *.a

clean_all:
	rm -f *.o *.a $(WSNAME)server $(WSNAME)test
