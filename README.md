# eksam

<?php
error_reporting(error_reporting() & (-1 ^ E_DEPRECATED));

$host="localhost";
$username="test";
$password="t3st3r123";
$db_name="test";
$tbl_name="counter";  

mysql_connect("$host", "$username", "$password"); 
mysql_select_db("$db_name")or die("cannot select DB");

$sql="SELECT * FROM $tbl_name";
$result=mysql_query($sql);
$rows=mysql_fetch_array($result);
$counter=$rows['counter'];

// if have no counter value set counter = 0
if(empty($counter)){
$counter=0;
$sql1="INSERT INTO $tbl_name(counter) VALUES('$counter')";
$result1=mysql_query($sql1);
}
echo "Selle lehe külastusi: ";
echo $counter;

$addcounter=$counter+1;
$sql2="update $tbl_name set counter='$addcounter'";
$result2=mysql_query($sql2);

mysql_close();
?>
