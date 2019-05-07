## 文件操作和读写 基于(fs.read fs.write) 异步读写

#### 可读流
可以读流读取的时候会先将内容读取到预先定义好的内存空间中，然后执行读取, 每次只读取定义的大小字节，读取成功将触发data事件，并将读取内容返回，然后开始下次读取，直到读取完成，触发end事件


#### 可写流

可写流会在内存中预定一块缓存区域，然后开始往目标文件写入，第一次会直接写入文件，此时后续要写入的内容会暂时放在缓存区， 当写入成功之后，会从缓存区依次拿取数据写入。直到清空之后再次重复刚才的步骤 以此来实现一边读取 一边写入 占用较少资源