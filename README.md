# myrocks-docker
stack docker-compose intégrant RocksDB comme moteur de stockage à l'image mariadb:10.3-focal

cf [http://myrocks.io/](http://myrocks.io/) et restrictions spécifiques à ce moteur [https://github.com/facebook/mysql-5.6/wiki/MyRocks-limitations](https://github.com/facebook/mysql-5.6/wiki/MyRocks-limitations "MyRocks limitations") particulièrement **Foreign Key, Spatial Index, and Fulltext Index are not supported**

pour vérifier :

    select * from information_schema.plugins where plugin_name='ROCKSDB';

et

    SELECT engine,GROUP_CONCAT(DISTINCT TABLE_SCHEMA) Table_Schema_List,COUNT(*) FROM information_schema.tables GROUP BY engine;


et

    select table_schema as database_name,
       table_name,
       engine
    from information_schema.tables
    where table_type = 'BASE TABLE'
      and table_schema not in ('information_schema','mysql',
                               'performance_schema','sys')
    -- and table_schema = 'your database name'
    order by table_schema,
    table_name;
