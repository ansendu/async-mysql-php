# async-mysql-php

mysql �첽�ͻ��ˣ�����mysqli::poll�򵥷�װ   
������mysql���ִ���ʱ�����׳��쳣   
��ִ��sqlʧ��ʱ��������result����Ӧ�ֶα�־Ϊfalse��������ʾ������Ϣ   
���ؽ����˳����attach˳��һ��  
�ӿ����£� 
```php
try{
    $async_mysql = new \Jenner\Mysql\Async();
    $async_mysql->attach(
        ['host' => '127.0.0.1', 'user' => 'root', 'password' => '', 'database' => 'test'],
        'select * from stu'
    );
    $async_mysql->attach(
        ['host' => '127.0.0.1', 'user' => 'root', 'password' => '', 'database' => 'test'],
        'select * from stu limit 0, 3'
    );
    $result = $async_mysql->execute();
    print_r($result);
}catch (Exception $e){
    echo $e->getMessage();
}
```