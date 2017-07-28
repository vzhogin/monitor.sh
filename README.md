# monitor.sh

#!/bin/bash
# by Vyacheslav Zhogin
# nginx
RESTART="/etc/init.d/nginx restart"
PGREP="/usr/bin/pgrep"
NGINX="nginx"
$PGREP ${NGINX}
if [ $? -ne 0 ]; then
$RESTART
fi
# mysql
RESTARTM="/etc/init.d/mysql restart"
MYSQLD="mysqld"
$PGREP ${MYSQLD}
if [ $? -ne 0 ]; then
$RESTART
$RESTARTM
fi
