工具如何使用：
    wsdl2h -o outfile.h infile.wsdl 实现wsdl文件到h文件的数据映射

    soapcpp2 -c outfile.h生成相应的底层通信stub，strech程序

    如果不需要wsdl的文件，可以直接从.h文件来生成代码
        soapcpp2 -c ../include/add.h，自动生成一些远程调用需要的文件
