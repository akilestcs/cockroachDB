# cockroachDB
#Please download the karl.tar file and untar in a new folder.
#once all the .sql files untar , run below script in command line to import all tables.

for i in `ls`
do
j=`echo $i | sed ’s/.sql//g’`
echo $i; cockroach import table $j mysqldump $i --insecure ; sleep 5;
done

#once all imported successfully, download the extra.sql and run below command from command line.

cockroach import table cities1 mysqldump extra.sql --insecure

#Once this is completed, connect to cockroach DB and drop the table cities1.

cockroach sql --insecure
drop table cities1;
