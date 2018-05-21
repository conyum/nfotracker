# nfotracker
Rss feed for .NFO from trackers. including Race-details and release-details.

DEMO: ```
SOON ```

Info: Demo show enough.

Requirements:
```bash
php5-fpm, php5, php5-curl, apache2, nginx(for caching if wanted), varnish 5.2(speeds up site alot, if wanted)
```
install (Ubuntu 14.04):

1), ```sudo apt-get install php5 php5-fpm php5-curl apache2 mariadb-server libapache2-mod-php5 php5-mysql nohup```<br />
2a), change AllowOverride from "None" to "All" in apache2 config-file<br />
2b), a2enmod rewrite<br />
2c), upload all files to /var/www/html/<br />
3), MariaDB settings:<br />
```php
[mysqld]
ft_min_word_len=1
ft_stopword_file='stopword_file.txt'
tmp_table_size=2G
max_heap_table_size=2G
```
<br />
4), create a file called startup.sh in /var/www/ and add inside:

```sh

#!/bin/bash
while [ true ]; do

 wget -O /dev/null http://127.0.0.1:80/xtra/processor.php?q=tracker1
sleep 10
 wget -O /dev/null http://127.0.0.1:80/xtra/processor.php?q=tracker1
sleep 15
 wget -O /dev/null http://127.0.0.1:80/xtra/processor.php?q=tracker1
sleep 10
 wget -O /dev/null http://127.0.0.1:80/xtra/processor.php?q=tracker1
sleep 15

done
```

5a), Import database.sql

5b), change credentials in /var/www/html/xtra/broken_dreams.php to whatever database credentials you have.

6), Start the startup.sh loop with:

```bash
cd /var/www/
nohup ./startup.sh >/dev/null 2>&1 &
```

should be all. 
