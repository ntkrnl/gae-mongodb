GAE python mongodb完全兼容接口

只需要把datastore_mongodb_stub.py pymongo bson复制到
在你的model.py里面加入这几句话
gae的app就可以无缝使用mongodb数据库了
其中mongodb://xxxxxx是mongodb uri
port写数据库端口，也可以忽略此参数
具体见DatastoreMongoDBStub函数的声明


    import os
	import datastore_mongodb_stub
    from google.appengine.api import apiproxy_stub_map
    
    mongodb = datastore_mongodb_stub.DatastoreMongoDBStub(os.environ['APPLICATION_ID'], False, 'datastore_v3', None, None, 'mongodb://xxxxxx', port)
    apiproxy_stub_map.apiproxy.ReplaceStub('datastore_v3', mongodb)