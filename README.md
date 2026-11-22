# helpdesk
https://github.com/genilsonaborges/znuny-commands/blob/main/Znuny_install_EN.md
curl -L https://github.com/znuny/Znuny/archive/refs/tags/rel-6_0_17.tar.gz -o /tmp/znuny-6.0.17.tar.gz

## Сверь локаль
timedatectl
locale
## Сверь настройки в Config.pm
В главном конфиге /opt/otrs/Kernel/Config.pm иногда жестко прописывают:
• Старый FQDN или IP-адрес в параметре $Self->{FQDN}.
• Пути к кастомным шрифтам (например, DejaVu для кириллицы при генерации PDF).
• Настройки сессий в файлах (/opt/otrs/var/sessions) или в оперативной памяти (/dev/shm / tmpfs).

## Уточнить
• После переноса достаточно выполнить пересборку кэша и конфигов (Maint::Config::Rebuild и Maint::Cache::Delete), чтобы OTRS подхватил их пути.

# 1. OS
### Было
Версия OS:
```
cat /etc/redhat-release
CentOS Linux release 7.5.1804 (Core)
```
```
uname -a
Linux helpdesk.ascon.ru 3.10.0-1160.15.2.el7.x86_64 #1 SMP Wed Feb 3
```
### Сейчас
Версия OS:
```
cat /etc/redhat-release
AlmaLinux release 9.9 (Chartreuse Bobcat)
```
```
uname -a
Linux helpdesk 5.14.0-741.22.1.el9_9.x86_64 #1 SMP PREEMPT_DYNAMIC Thu Nov 12 14:34:46 UTC 2026 x86_64 x86_64 x86_64 GNU/Linux
```

## 2. HTTPD
### Было
Версия HTTPD: 
```
httpd -v
Server version: Apache/2.4.34 (codeit)
```

### Сейчас
Версия HTTPD:
```
httpd -v
Server version: Apache/2.4.62 (AlmaLinux)
Server built:   Oct 14 2026 00:00:00
```

## 3. Модули HTTPD
### Было
```
httpd -M
Loaded Modules:
 core_module (static)
 so_module (static)
 http_module (static)
 access_compat_module (shared)
 actions_module (shared)
 alias_module (shared)
 allowmethods_module (shared)
 auth_basic_module (shared)
 auth_digest_module (shared)
 authn_anon_module (shared)
 authn_core_module (shared)
 authn_dbd_module (shared)
 authn_dbm_module (shared)
 authn_file_module (shared)
 authn_socache_module (shared)
 authz_core_module (shared)
 authz_dbd_module (shared)
 authz_dbm_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_owner_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 brotli_module (shared)
 cache_module (shared)
 cache_disk_module (shared)
 cache_socache_module (shared)
 data_module (shared)
 dbd_module (shared)
 deflate_module (shared)
 dir_module (shared)
 dumpio_module (shared)
 echo_module (shared)
 env_module (shared)
 expires_module (shared)
 ext_filter_module (shared)
 filter_module (shared)
 headers_module (shared)
 include_module (shared)
 info_module (shared)
 log_config_module (shared)
 logio_module (shared)
 macro_module (shared)
 mime_magic_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 remoteip_module (shared)
 reqtimeout_module (shared)
 request_module (shared)
 rewrite_module (shared)
 setenvif_module (shared)
 slotmem_plain_module (shared)
 slotmem_shm_module (shared)
 socache_dbm_module (shared)
 socache_memcache_module (shared)
 socache_shmcb_module (shared)
 status_module (shared)
 substitute_module (shared)
 suexec_module (shared)
 unique_id_module (shared)
 unixd_module (shared)
 userdir_module (shared)
 version_module (shared)
 vhost_alias_module (shared)
 watchdog_module (shared)
 mpm_event_module (shared)
 ssl_module (shared)
 systemd_module (shared)
 cgid_module (shared)
 perl_module (shared)
 http2_module (shared)
```
71 модуль 

### Сейчас
```
sudo httpd -M
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using fe80::250:56ff:feb1:659%ens33. Set the 'ServerName' directive globally to suppress this message
Loaded Modules:
 core_module (static)
 so_module (static)
 http_module (static)
 access_compat_module (shared)
 actions_module (shared)
 alias_module (shared)
 allowmethods_module (shared)
 auth_basic_module (shared)
 auth_digest_module (shared)
 authn_anon_module (shared)
 authn_core_module (shared)
 authn_dbd_module (shared)
 authn_dbm_module (shared)
 authn_file_module (shared)
 authn_socache_module (shared)
 authz_core_module (shared)
 authz_dbd_module (shared)
 authz_dbm_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_owner_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cache_module (shared)
 cache_disk_module (shared)
 cache_socache_module (shared)
 data_module (shared)
 dbd_module (shared)
 deflate_module (shared)
 dir_module (shared)
 dumpio_module (shared)
 echo_module (shared)
 env_module (shared)
 expires_module (shared)
 ext_filter_module (shared)
 filter_module (shared)
 headers_module (shared)
 include_module (shared)
 info_module (shared)
 log_config_module (shared)
 logio_module (shared)
 macro_module (shared)
 mime_magic_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 remoteip_module (shared)
 reqtimeout_module (shared)
 request_module (shared)
 rewrite_module (shared)
 setenvif_module (shared)
 slotmem_plain_module (shared)
 slotmem_shm_module (shared)
 socache_dbm_module (shared)
 socache_memcache_module (shared)
 socache_redis_module (shared)
 socache_shmcb_module (shared)
 status_module (shared)
 substitute_module (shared)
 suexec_module (shared)
 unique_id_module (shared)
 unixd_module (shared)
 userdir_module (shared)
 version_module (shared)
 vhost_alias_module (shared)
 watchdog_module (shared)
 brotli_module (shared)
 dav_module (shared)
 dav_fs_module (shared)
 dav_lock_module (shared)
 lua_module (shared)
 mpm_event_module (shared)
 proxy_module (shared)
 lbmethod_bybusyness_module (shared)
 lbmethod_byrequests_module (shared)
 lbmethod_bytraffic_module (shared)
 lbmethod_heartbeat_module (shared)
 proxy_ajp_module (shared)
 proxy_balancer_module (shared)
 proxy_connect_module (shared)
 proxy_express_module (shared)
 proxy_fcgi_module (shared)
 proxy_fdpass_module (shared)
 proxy_ftp_module (shared)
 proxy_http_module (shared)
 proxy_hcheck_module (shared)
 proxy_scgi_module (shared)
 proxy_uwsgi_module (shared)
 proxy_wstunnel_module (shared)
 ssl_module (shared)
 systemd_module (shared)
 cgid_module (shared)
 perl_module (shared)
 http2_module (shared)
 proxy_http2_module (shared)
```
94 модуля, 71 основных модулей от старого сервера + 23 новых стандартных

## 4. База данных
### Было
Версия MariaDB:
```
mysql -V
mysql  Ver 15.1 Distrib 10.1.48-MariaDB, for Linux (x86_64) using
```

### Сейчас
```
mysql -V
mysql  Ver 15.1 Distrib 10.5.29-MariaDB, for Linux (x86_64) using  EditLine wrapper
```

## 5. Perl
### Было
Версия Perl:
```
perl -v
This is perl 5, version 16, subversion 3 (v5.16.3) built for x86_64-linux-thread-multi
```

### Сейчас
Версия Perl:
```
perl -v
This is perl 5, version 32, subversion 1 (v5.32.1) built for x86_64-linux-thread-multi
```

## 6. Модули Perl
### Было
Модули Perl`a:
```
sudo /opt/otrs/bin/otrs.CheckModules.pl
   o Apache::DBI......................ok (v1.12)
   o Apache2::Reload..................ok (v0.13)
   o Archive::Tar.....................ok (v1.92)
   o Archive::Zip.....................ok (v1.30)
   o Crypt::Eksblowfish::Bcrypt.......ok (v0.009)
   o Crypt::SSLeay....................ok (v0.64)
   o Date::Format.....................ok (v2.24)
   o DateTime.........................ok (v1.04)
   o DBI..............................ok (v1.627)
   o DBD::mysql.......................ok (v4.023)
   o DBD::ODBC........................Not installed! (optional - Required to connect to a MS-SQL database.)
   o DBD::Oracle......................Not installed! (optional - Required to connect to a Oracle database.)
   o DBD::Pg..........................ok (v2.19.3)
   o Digest::SHA......................ok (v5.85)
   o Encode::HanExtra.................ok (v0.23)
   o IO::Socket::SSL..................ok (v1.94)
   o JSON::XS.........................ok (v3.01)
   o List::Util::XS...................ok (v1.27)
   o LWP::UserAgent...................ok (v6.26)
   o Mail::IMAPClient.................ok (v3.37)
     o IO::Socket::SSL................ok (v1.94)
     o Authen::SASL...................ok (v2.15)
     o Authen::NTLM...................ok (v1.09)
   o ModPerl::Util....................ok (v2.000010)
   o Net::DNS.........................ok (v0.72)
   o Net::LDAP........................ok (v0.56)
   o Template.........................ok (v2.24)
   o Template::Stash::XS..............ok (undef)
   o Text::CSV_XS.....................ok (v1.00)
   o Time::HiRes......................ok (v1.9725)
   o XML::LibXML......................ok (v2.0018)
   o XML::LibXSLT.....................ok (v1.80)
   o XML::Parser......................ok (v2.41)
   o YAML::XS.........................ok (v0.54)
```
### Стало
Модули Perl`a:
```
sudo /opt/otrs/bin/otrs.CheckModules.pl
  o Apache::DBI......................ok (v1.12)
  o Apache2::Reload..................ok (v0.13)
  o Archive::Tar.....................ok (v2.38)
  o Archive::Zip.....................ok (v1.68)
  o Crypt::Eksblowfish::Bcrypt.......ok (v0.009)
  o Crypt::SSLeay....................ok (v0.72)
  o Date::Format.....................ok (v2.24)
  o DateTime.........................ok (v1.54)
  o DBI..............................ok (v1.643)
  o DBD::mysql.......................ok (v4.053)
  o DBD::ODBC........................Not installed! Use: 'cpan DBD::ODBC' (optional - Required to connect to a MS-SQL database.)
  o DBD::Oracle......................Not installed! Use: 'cpan DBD::Oracle' (optional - Required to connect to a Oracle database.)
  o DBD::Pg..........................ok (v3.14.2)
  o Digest::SHA......................ok (v6.02)
  o Encode::HanExtra.................ok (v0.23)
  o IO::Socket::SSL..................ok (v2.073)
  o JSON::XS.........................ok (v4.04)
  o List::Util::XS...................ok (v1.56)
  o LWP::UserAgent...................ok (v6.26)
  o Mail::IMAPClient.................ok (v3.42)
    o IO::Socket::SSL................ok (v2.073)
    o Authen::SASL...................ok (v2.16)
    o Authen::NTLM...................ok (v1.09)
  o ModPerl::Util....................ok (v2.000012)
  o Net::DNS.........................ok (v1.29)
  o Net::LDAP........................ok (v0.68)
  o Template.........................ok (v3.009)
  o Template::Stash::XS..............ok (undef)
  o Text::CSV_XS.....................ok (v1.65)
  o Time::HiRes......................ok (v1.9764)
  o XML::LibXML......................ok (v2.0206)
  o XML::LibXSLT.....................ok (v1.99)
  o XML::Parser......................ok (v2.46)
  o YAML::XS.........................ok (v0.82)
```
Все модули полностью перенесены, есть повышение версий модуля

## Процесс обновления
```
sudo dnf update
sudo dnf install -y epel-release
sudo dnf install -y httpd mod_ssl mod_http2 mod_perl
sudo dnf install -y mariadb-server
sudo dnf config-manager --set-enabled crb
sudo dnf install -y perl-Archive-Tar perl-Archive-Zip perl-Authen-SASL perl-Crypt-Eksblowfish perl-Crypt-SSLeay perl-DBD-MySQL perl-DBD-Pg perl-Digest-SHA perl-LDAP perl-libwww-perl perl-LWP-Protocol-https perl-Mail-IMAPClient perl-Net-DNS perl-Template-Toolkit perl-Text-CSV_XS perl-XML-LibXML perl-XML-LibXSLT perl-XML-Parser perl-App-cpanminus perl-YAML-LibYAML perl-JSON-XS perl-TimeDate perl-DateTime perl-Encode-HanExtra


sudo useradd -d /opt/otrs -c 'OTRS user' -g apache -s /bin/bash -M otrs



## • Проверьте в /opt/otrs/Kernel/Config.pm, не зашиты ли там жестко старый IP-адрес сервера, старый hostname или пути, которых нет на AlmaLinux.
## • Проверьте  на старом сервере пакеты which htmldoc wkhtmltopdf pdftotext catdoc xls2csv unzip unrar fetchmail certbot 2>/dev/null
## • Проверьте  на старом сервере настройки для БД grep -RhoE '^[^#;[:space:]].*' /etc/my.cnf /etc/my.cnf.d/ 2>/dev/null


# 1. Крон пользователя root и пользователя otrs
crontab -l 2>/dev/null
crontab -u otrs -l 2>/dev/null

# 2. Системные кроны
cat /etc/crontab
ls -la /etc/cron.d/

# 3. Самописные скрипты в /usr/local/bin
ls -la /usr/local/bin/

# Список установленных пакетов OTRS
su - otrs -c "/opt/otrs/bin/otrs.Console.pl Admin::Package::List"

```

## Момент переноса
```
# 1. Выключаем веб-сервер, чтобы клиенты и агенты не создавали новые тикеты и сессии
sudo systemctl stop httpd

# 2. Останавливаем планировщик Cron и демон OTRS (чтобы не забиралась почта и не срабатывали триггеры)
sudo su - otrs -c "/opt/otrs/bin/Cron.sh stop"
sudo su - otrs -c "/opt/otrs/bin/otrs.Daemon.pl stop"

# 3. Если на сервере крутится локальный почтовик (Postfix/Exim) или Fetchmail — ставим их на паузу
sudo systemctl stop postfix 2>/dev/null || true

Фаервол

----------------------------------------------

# 1. Снимаем дамп базы (замените otrs на имя вашей БД, если оно другое)
mysqldump -u root -p --single-transaction --routines --triggers --events --databases otrs | gzip > /tmp/otrs_db.sql.gz

# 2. Выгружаем пользователей и их права в виде SQL-запросов
mysql -u root -p -N -e "SELECT CONCAT('SHOW GRANTS FOR \'', user, '\'@\'', host, '\';') FROM mysql.user WHERE user NOT IN ('root', 'mysql.sys', 'mariadb.sys', '');" | mysql -u root -p -N | sed 's/$/;/' > /tmp/grants.sql

----------------------------------------------

# 1. Копируем дампы БД
scp /tmp/otrs_db.sql.gz /tmp/grants.sql root@IP_НОВОГО_СЕРВЕРА:/tmp/

# 2. Копируем всю директорию /opt/otrs с сохранением симлинков, прав и времени модификации
rsync -avz --delete /opt/otrs/ root@IP_НОВОГО_СЕРВЕРА:/opt/otrs/

# 3. Копируем ваши конфиги виртуальных хостов Apache и SSL-сертификаты (проверьте свои пути)
scp -r /etc/httpd/conf.d/* root@IP_НОВОГО_СЕРВЕРА:/tmp/old_httpd_conf.d/

----------------------------------------------

# 1. Загружаем базу и права в MariaDB
gunzip < /tmp/otrs_db.sql.gz | mysql -u root -p
mysql -u root -p < /tmp/grants.sql
mysql -u root -p -e "FLUSH PRIVILEGES;"

# 2. Выставляем правильные права на /opt/otrs для пользователя otrs и группы apache
sudo /opt/otrs/bin/otrs.SetPermissions.pl --web-group=apache

# 3. Чистим старый кэш и пересобираем конфиг
sudo su - otrs -c "/opt/otrs/bin/otrs.Console.pl Maint::Cache::Delete"
sudo su - otrs -c "/opt/otrs/bin/otrs.Console.pl Maint::Config::Rebuild"

---------------------------------------------


# 3. Проверяем подключение к перенесенной базе MariaDB
sudo su - otrs -c "/opt/otrs/bin/otrs.Console.pl Maint::Database::Check"



# Копируем папку на новый сервер (выполнить со старого сервера):
rsync -avz --delete /opt/otrs/ root@IP_НОВОГО_СЕРВЕРА:/opt/otrs/

# 1. Выставляем правильные права на /opt/otrs для пользователя otrs и группы apache
sudo /opt/otrs/bin/otrs.SetPermissions.pl --web-group=apache



# Копируем файлы cron (если их еще нет в /opt/otrs/var/cron/ без суффикса .dist)




sudo su - otrs -c "/opt/otrs/bin/Cron.sh start"
sudo su - otrs -c "/opt/otrs/bin/otrs.Daemon.pl start"


```
