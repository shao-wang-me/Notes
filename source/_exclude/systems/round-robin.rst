Round robin
===========

循环制，一个一个来。在不同系统中的具体实现不完全相同，但是本质就是“一个一个来”。

比如在负载均衡中，round robin就是每次把一个请求给下一个server、processor，循环往复。而在processor scheduling中，则是time slicing。
