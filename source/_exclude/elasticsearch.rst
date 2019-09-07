Elasticsearch
=============

If 
基于Apache Lucene。Lucene是一个Java library，包括了搜索的基本组件，如inverted index。Elasticsearch在Lucene基础上实现了分布式。

Index-time
  ES接受JSON数据，处理后存于inverted index等数据格式。数据处理取决于mappings。如text格式数据，会先tokenize为一个个token（terms）。

周边工具
============

1. https://appbase.io/：主要业务是托管Elasticsearch，亦提供一系列周边工具
2. http://mobz.github.io/elasticsearch-head/：很丑，好像是管理ES集群的
