# TPS
REMOTE_IP="10.102.42.75"
SCP_PASSWORD="eocn@123"
#And now transfer the file over
expect -c
"
   set timeout 1
   spawn scp /Log/TPS_FILE/Backup/tps_$host.txt_$ddate eocn@$REMOTE_IP:/home/eocn/Setup/TPSInsertLogger/logs/
   expect yes/no { send yes\r ; exp_continue }
   expect password: { send $SCP_PASSWORD\r }
   expect 100%
   sleep 1
   exit
"
now am adding in second code to tps_eocn
now i am testing for master branch
done
