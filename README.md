paper
=====3G AT-COMMAND=====

get 3G status

/usr/sbin/ezpcom stats -d /dev/ttyUSB1   

open aerial

/usr/sbin/ezpcom radioon -d /dev/ttyUSB1

set module

SCRIPT='At+cfun=1' ezpcom -d /dev/ttyUSB1 -s /etc/chatscripts/script.gcom

get signal

SCRIPT='At+csq' ezpcom -d /dev/ttyUSB1 -s /etc/chatscripts/script.gcom

get module status

SCRIPT='At^sysinfo' ezpcom -d /dev/ttyUSB1 -s /etc/chatscripts/script.gcom

connect

/usr/sbin/pppd /dev/ttyUSB1 460800 lock noauth crtscts noaccomp nopcomp novj nobsdcomp noauth noipdefault usepeerdns nodefaultroute ipparam 0 linkname 0 unit 0 user "" password "" connect "WWAN_DIALSTR=\"*99***1#\" /usr/sbin/chat -v -E -f /etc/chatscripts/wwan.chat"
