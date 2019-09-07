# Java环境配置的几种方式
https://docs.oracle.com/javase/tutorial/essential/environment/index.html

1. Properties
纯文本键值对，可以从任意stream中得到，用java.util.Properties访问
Java在System中也有一个Properties对象维护自己的配置，用System.getProperty和System.getProperties访问，如java.home, os.name, user.dir等
2. 命令行参数
通过添加JAVA_TOOL_OPTIONS到环境变量中，可以设置默认的Java参数，如果手动提供参数，将被覆盖
3. 系统的环境变量
System.getenv可以得到系统的环境变量，但由于不同操作系统的环境变量名称不统一，如果通过system property可以实现，就不要使用系统环境变量
4. Preference API
5. JAR中的application使用manifest来形容改archive中的内容
6. Java Web Start application使用JNLP来配置
7. Java Plug-in applet的配置部分是由所嵌入的HTML的tag决定的
8. 还有java.util.ServiceLoader提供一个简单的service provider设施，service provider可以作为扩展安装，也可以把他们加到class path，或其他方式
9. 命令行I/O对象，例如命令行用户输入等