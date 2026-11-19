# helpdesk

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

## Процесс обновления
```
sudo dnf update
sudo dnf install -y epel-release
sudo dnf install -y httpd mod_ssl mod_http2 mod_perl
sudo dnf install -y mariadb-server
sudo dnf config-manager --set-enabled crb
sudo dnf install -y  perl-Archive-Tar  perl-Archive-Zip  perl-Authen-SASL  perl-Crypt-Eksblowfish  perl-Crypt-SSLeay  perl-DBD-MySQL  perl-DBD-Pg  perl-Digest-SHA  perl-LDAP  perl-libwww-perl  perl-LWP-Protocol-https  perl-Mail-IMAPClient  perl-Net-DNS  perl-Template-Toolkit  perl-Text-CSV_XS  perl-XML-LibXML  perl-XML-LibXSLT  perl-XML-Parser  perl-App-cpanminus  perl-YAML-LibYAML  perl-JSON-XS  perl-TimeDate  perl-DateTime
```
