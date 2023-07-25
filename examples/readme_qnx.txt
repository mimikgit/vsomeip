1.build instructions
Suppose currently at the vsomeip/build_qnx dirctory, the instructions to build this two examples is listed as the following. 

cd nto/aarch64/le/build/examples
make

2.runing the request/response example
copy the udp client config files to current directory as the following

cp ../../../../../../config/vsomeip-udp-service.json ./
cp ../../../../../../config/vsomeip-udp-client.json ./

modify the unicast ip in the config files to correspondence ip of server and client. then running request/response example as the following.

VSOMEIP_CONFIGURATION=vsomeip-udp-client.json VSOMEIP_APPLICATION_NAME=client-sample ./request-sample
VSOMEIP_CONFIGURATION=vsomeip-udp-service.json VSOMEIP_APPLICATION_NAME=service-sample ./response-sample

3.the issue found
currently the client on qnx is working fine. the service on qnx is working but has issue. it was working for a few of comminucation trascations and then stop to work.
 


