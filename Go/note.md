1,图解Golang的内存分配
https://www.jianshu.com/p/2904efc7f1a8

2,操作 channel 的情况总结
操作				nil channel			closed channel		not nil, not closed channel
close			panic				panic				正常关闭
读 <- ch			阻塞					读到对应类型的零值		阻塞或正常读取数据。缓冲型 channel 为空或非缓冲型 channel 没有等待发送者时会阻塞
写 ch <-			阻塞					panic				阻塞或正常写入数据。非缓冲型 channel 没有等待接收者或缓冲型 channel buf 满时会被阻塞



