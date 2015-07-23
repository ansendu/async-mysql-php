# async-mysql-php
�ĵ���[http://www.huyanping.cn/php%E5%BC%82%E6%AD%A5%E5%B9%B6%E5%8F%91%E8%AE%BF%E9%97%AEmysql%E7%AE%80%E5%8D%95%E5%AE%9E%E7%8E%B0/](http://www.huyanping.cn/php%E5%BC%82%E6%AD%A5%E5%B9%B6%E5%8F%91%E8%AE%BF%E9%97%AEmysql%E7%AE%80%E5%8D%95%E5%AE%9E%E7%8E%B0/)
mysql �첽�ͻ��ˣ�����mysqli::poll�򵥷�װ   
������mysql���ִ����SQLִ�г���ʱ�����׳��쳣      
���ؽ����˳����attach˳��һ��  
�ӿ����£� 
```php
try{
    $async_mysql = new \Jenner\Mysql\Async();
    $async_mysql->attach(
        ['host' => '127.0.0.1', 'user' => 'root', 'password' => '', 'database' => 'test', 'port'=>3306],
        'select * from stu'
    );
    $async_mysql->attach(
        ['host' => '127.0.0.1', 'user' => 'root', 'password' => '', 'database' => 'test', 'port'=>3306],
        'select * from stu limit 0, 3'
    );
    $result = $async_mysql->execute();
    print_r($result);
}catch (Exception $e){
    echo $e->getMessage();
}
```

���ܲ��Ա�������  
-------------------------
�ܽ᣺�첽�����ķ�ʽ�����ϱ���ͻ��������ڴ��еķ��ʷ�ʽ�� 
���Խ��������ʹ�ø÷�ʽ����������������mysql���ٶȣ������������٣������������ҵ��
һ������£�ִ�е�ʱ��ȡ������ӵ�һ��SQL��
```shell
# ͬ��
[root@iZ942077c78Z async-mysql-php]# php tests/performance_sync.php 
------------------------------------------
mark:[total diff]
time:4.2648551464081s
memory_real:18944KB
memory_emalloc:18377.171875KB
memory_peak_real:28416KB
memory_peak_emalloc:27560.3828125KB
[root@iZ942077c78Z async-mysql-php]# php tests/performance_sync.php 
------------------------------------------
mark:[total diff]
time:4.2285549640656s
memory_real:18944KB
memory_emalloc:18377.171875KB
memory_peak_real:28416KB
memory_peak_emalloc:27560.3828125KB
[root@iZ942077c78Z async-mysql-php]# php tests/performance_async.php  
------------------------------------------
mark:[total diff]
time:1.455677986145s
memory_real:38144KB
memory_emalloc:32574.015625KB
memory_peak_real:66816KB
memory_peak_emalloc:65709.7734375KB
# �첽
[root@iZ942077c78Z async-mysql-php]# php tests/performance_async.php 
------------------------------------------
mark:[total diff]
time:1.8936941623688s
memory_real:38144KB
memory_emalloc:32574.015625KB
memory_peak_real:66816KB
memory_peak_emalloc:65709.7734375KB
[root@iZ942077c78Z async-mysql-php]# php tests/performance_async.php 
------------------------------------------
mark:[total diff]
time:1.5208158493042s
memory_real:38144KB
memory_emalloc:32574.015625KB
memory_peak_real:66816KB
memory_peak_emalloc:65709.7734375KB
```