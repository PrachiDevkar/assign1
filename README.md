exam@exam-ThinkCentre-M71e:~$ cassandra/bin/cqlsh
Connected to Test Cluster at 127.0.0.1:9042.
[cqlsh 5.0.1 | Cassandra 2.1.11 | CQL spec 3.2.1 | Native protocol v3]
Use HELP for help.
cqlsh> create keyspace mykyspace with replication={'class':'SimpleStrategy','replication_factor':1};
cqlsh> use mykyspace;
cqlsh:mykyspace> insert into student(roll,fname,lname) values(1,'prachi','devkar');
cqlsh:mykyspace> select * from student;

 roll | fname   | lname
------+---------+-------
    1 | prachi | devkar

(1 rows)
cqlsh:mykyspace> insert into student(roll,fname,lname) values(2,'rutuja','smith');
cqlsh:mykyspace> insert into student(roll,fname,lname) values(3,'Ashwini','doe');
cqlsh:mykyspace> select * from student;
 roll | fname   | lname
------+---------+-------
    1 | prachi   | devkar
    2 |  rutuja  | smith
    3 |  ashwini |   doe

(3 rows)
cqlsh:mykyspace> create index on student(lname);
cqlsh:mykyspace> select * from student where lname='doe';

 roll | fname  | lname
------+-------+-------
    3 | ashwini|   doe

(1 rows)
cqlsh:mykyspace> select * from student where fname='prachi';
InvalidRequest: code=2200 [Invalid query] message="No secondary indexes on the restricted columns support the provided operators: "
cqlsh:mykyspace> select * from student where roll=1;

 roll | fname    | lname
------+---------+-------
    1 | prachi | devkar

(1 rows)

