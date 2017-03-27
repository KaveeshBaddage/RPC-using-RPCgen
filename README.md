# RPC-using-RPCgen

RPC program.

This RPC program supports one remote procedure call that check given number is odd or even.



FILES:

oddEven.x

this is the RPC protocol definition file. Although it looks like 'C', it is not! This file is run through the C preprocessor and the result is processed by rpcgen. rpcgen will create a header file named oddEven.h containing data structure definitions and function prototypes for the C code generated. The generated C code is created in the files oddEven_clnt.c (which contains the client stubs) and oddEven_svc.c (which contains the main program for the server). rpcgen also creates any needed XDR filter functions in the file oddEven_xdr.c

oddEven_client.c - The main client program

	This client just calls each of the remote procedures once and prints out the results.When calling the clientstubs, user must pass pointers and the return value is a pointer.
	

oddEven_server.c: the actual remote procedure

The important thing here is to make sure the functions  expect the right kind of parameters and return the right thing. With RPC, everything has to be a pointer - the procedure argument is a pointer to the type your declared in the .x file, and the return value is a pointer to the return type declare inthe .x file.

oddEven_svc.c - The server main program, this was created by rpcgen.

oddEven_clnt.c - The client stubs, this file was created by rpcgen.

oddEven_xdr.c - the XDR filter(s) needed for this application, this file was created by rpcgen.


How to run :

First go to the project root and run below three commands

rpcgen -C oddEven.x
make -f Makefile.oddEven
./oddEven_server

Then open a new terminal and run the client using the following command. In the below command, after the localhost user should give any number as the parameter to check odd, even property.

./oddEven_client localhost 7

