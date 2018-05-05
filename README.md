# TPS
[eocn@WB-GR-1 ~]$ cat /home/eocn/Setup/SCRIPT/eocn_tps.sh
#!/bin/bash
host=`hostname`
circle=WB
year=`date +%Y-%m-%d -d '3 days ago'`
cd /Log/TPS_FILE/Backup/
rm -f tps_$host.txt_$year*
ddate=`date +%Y-%m-%d-%-k -d '1 hour ago'`
cd /Log/SMPP/Backup/
>tps_$host.txt
zgrep -a "got request" Log.txt$ddate.gz|grep "submit:" |cut -c '1-19' |sort|uniq -c|sort -nr |head -5>tps.txt
sleep 10
exec<tps.txt
while read line
do
a=`echo $line|awk '{print $1}'`
b=`echo $line|awk '{print $2,$3}'`
echo datetime=$b
c=`echo $circle`
d=`echo $host`
echo "$a#$b#$c#$d">>/Log/TPS_FILE/Backup/tps_$host.txt_$ddate
done


now i am testing for master branch
done
