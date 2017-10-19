cpSetup
=======

<strong>Autor:</strong> Myles McNamara<br/><strong>Forked:</strong> Javier Galeote<br/><strong>Version:</strong> 1.4.0<br/><strong>Last Update:</strong> February 1, 2017

<strong>cpsetup</strong> es un script bash/shell personalizado para configurar y securizar un servidor CentOS/RHEL con cPanel y una amplia gama de aplicaciones, complementos y módulos. Este script también instalará cPanel si no está aún instalado.

Cada instalación y configuración/securización está organizada en funciones. De manera predeterminada, si ejecutas el script sin argumentos, el sistema te pedirá permiso para ejecutar cada instalación/configuración, así como te solicitará cualquier configuración requerida (correo electrónico, clave API, etc.).

También puedes ejecutar cualquiera de las funciones disponibles individualmente ... para ver una lista de funciones disponibles, ejecuta este comando:

```bash
./cpsetup --functions
```

Uso
=====

```bash
wget https://github.com/funmaking/cpsetup/raw/master/cpsetup
chmod +x cpsetup
./cpsetup
```

<table border="0">
<tr>
<td width="60%">
<h4>Características incluidas:</h4>
<ul>
    <li>Install ClamAV from Source</li>
    <li>Install <a href="https://documentation.cpanel.net/display/CKB/The+Let's+Encrypt+Plugin" target="_blank">Let's Encrypt for cPanel AutoSSL</a></li>
    <li>Install <a href="http://www.afterlogic.org/docs/webmail-lite/installation/install-on-cpanel" target="_blank">AfterLogic WebMail Lite</a></li>
    <li>Install <a href="http://configserver.com/cp/cse.html" target="_blank">ConfigServer Explorer</a></li>
    <li>Install <a href="http://configserver.com/cp/cmm.html" target="_blank">ConfigServer MailManage</a></li>
    <li>Install <a href="http://configserver.com/cp/cmq.html" target="_blank">ConfigServer MailQueues</a></li>
    <li>Install <a href="http://configserver.com/cp/csf.html" target="_blank">ConfigServer Firewall</a></li>
    <li>Install <a href="http://configserver.com/cp/cmc.html" target="_blank">ConfigServer ModSecurity Control</a></li>
    <li>Install <a href="https://www.configserver.com/free/mailscanner.html" target="_blank">ConfigServer MailScanner</a></li>
    <li>Install <a href="http://configserver.com/cp/cxs.html" target="_blank">ConfigServer Exploit Scanner</a></li>
    <li>Install <a href="https://www.rfxn.com/projects/linux-malware-detect/" target="_blank">R-fx Malware Detect</a></li>
    <li>Install <a href="http://www.softaculous.com/" target="_blank">Softaculous</a></li>
    <li>Install <a href="https://www.ndchost.com/cpanel-whm/addons/watchmysql/" target="_blank">WatchMySQL</a></li>
    <li>Install <a href="https://github.com/major/MySQLTuner-perl" target="_blank">MySQL Tuner</a></li>
    <li>Install <a href="https://www.cloudflare.com/static/media/pdf/cloudflare-cpanel-installation-activation-guide.pdf" target="_blank">cPanel mod_cloudflare</a> (<a href="https://github.com/tripflex/cloudflarecp" target="_blank">cloudflarecp</a>)</li>
    <li>Install <a href="https://www.cloudflare.com/railgun" target="_blank">CloudFlare RailGun</a></li>
    <li>Install yum terminal colors</li>
    <li><a href="https://www.cloudflare.com/docs/railgun/installation.html" target="_blank">Configure/Setup CloudFlare RailGun</a></li>
    <li>Configure CloudFlare RailGun and MemCached (using socket)</li>
    <li>Update Firewall Allow list with CloudFlare IPs</li>
    <li>Update Firewall Configuration</li>
    <li>Update SSH Configuration ( Port, and UseDNS )</li>
    <li>Update cPanel Configurations</li>
    <li>Update Pure FTP Configurations</li>
    <li>Update cPanel Tweak Settings</li>
    <li>Update MySQL Settings</li>
    <li>Update PHP Settings</li>
    <li>Update Apache Global Configuration</li>
</ul>
<h4>Depreciated (but still available) Features/Functions:</h4>
<ul>
    <li>Install <a href="https://www.ndchost.com/cpanel-whm/addons/accountdnscheck/" target="_blank">Account DNS Check</a>* (depreciated)</li>
    <li>Install <a href="http://how2.be/en/community/phpinimgr/" target="_blank">PHP.ini Manager</a>* (depreciated)</li>
    <li>Install <a href="https://www.ndchost.com/cpanel-whm/addons/cleanbackups/" target="_blank">Clean Backups</a>* (depreciated)</li>
</ul>
<h4>Future Enhancements:</h4>
<ul>
<li>You tell me, open up an issue and suggest a new feature!</li>
</ul>
</td>
<td width="40%">
<p align="center"><img src="screenshot.png"></p>
</td>
</tr>
</table>

Depreciated Functions/Installs (*)
----------------

| Name | Reason |
|---|---|
| Account DNS Check | Reported to no longer work on CentOS 7, or WHM > 11.52 |
| PHP.INI Manager   | WHM now has built in handling, and unsure of status of plugin |
| Clean Backups     | No longer works or updated? |

> I decided to remove these from the auto install process because I either do not know the status of them (compatibility wise) with WHM,
> they are not compatible with latest release, or because the developers either do not provide ANY changelog, or even if they do,
> they don't even date the versions, which IMO is sloppy dev work, and as such, they do not belong in the auto install process.


Argumentos Disponibles
----------------------

```
cpsetup - sMyles cPanel Setup Script
Usage example:
./cpsetup [(-h|--help)] [(-v|--verbose)] [(-V|--version)] [(-u|--unattended)] [(-m|--menu)] [(-r|--run) value] [(-R|--functions)]
Options:
-h or --help: Displays this information.
-v or --verbose: Verbose mode on.
-V or --version: Displays the current version number.
-u or --unattended: Unattended installation ( bypasses all prompts ).
-m or --menu: Show interactive UI menu (NOT yet implimented)
-r or --run: Run a specific function.
-R or --functions: Show available functions to use with -r or --run command.
```

Cambios en el Firewall
----------------------

| Option            | Original Value | New Value |
|-------------------|----------------|-----------|
| `RESTRICT_SYSLOG` | 0              | 3         |
| `SMTP_BLOCK`      | 0              | 1         |
| `LF_SCRIPT_ALERT` | 0              | 1         |
| `SYSLOG_CHECK`    | 0              | 1800      |
| `PT_ALL_USERS`    | 0              | 1         |


Cambios en  SSH
---------------

Any options that have `(prompt)` means you will be prompted to specify your own custom value if `-u` was not used as an argument.

| Option   | Original Value | New Value    |
|----------|----------------|--------------|
| `Port`   | 22             | 222 (prompt) |
| `UseDNS` | yes            | no           |


Cambios en la Configuración de cPanel
-------------------------------------

| Option                     | Original Value | New Value               |
|----------------------------|----------------|-------------------------|
| Shell Fork Bomb Protection | Disabled       | Enabled                 |
| Compiler Access            | Enabled        | Disabled                |
| Root Forwarder Email       | None           | User Specified (prompt) |


Cambios en Pure FTP
--------------------

| Option                | Original Value | New Value | Result                   |
|-----------------------|----------------|-----------|--------------------------|
| `RootPassLogins`      | yes            | no        | Can't login with root pw |
| `AnonymousCantUpload` | no             | yes       | Anonymous can't upload   |
| `NoAnonymous`         | no             | yes       | Anonymous can't login    |


Cambios en cPanel Tweak Settings
---------------------------------

| Option                               | Original Value | New Value |
|--------------------------------------|----------------|-----------|
| BoxTrapper                           | Enabled        | Disabled  |
| Referrer Blank Sanity Check          | Disabled       | Enabled   |
| Referrer Safety Check                | Disabled       | Enabled   |
| Hide Login PW from CGI Scripts       | Disabled       | Enabled   |
| Max Emails Account Can Send Per Hour | Unlimited      | 199       |
| Restrict outgoing SMTP to root, exim, and mailman | Enabled | Disabled |
| Proxy Subdomains (whm.example.com, etc)| Enabled | Disabled |


Cambios en MySQL
----------------

| Option       | Original Value | New Value |
|--------------|----------------|-----------|
| local-infile | 1              | 0         |


Cambios en Configuraciones de PHP
---------------------------------

| Option            | Original Value | New Value                                                                                            |
|-------------------|----------------|------------------------------------------------------------------------------------------------------|
| enable_dl         | On             | Off                                                                                                  |
| disable_functions | None           | show_source, system, shell_exec, passthru, exec, phpinfo, popen, proc_open, allow_url_fopen, ini_set |


Cambios en la Configuración global de Apache
--------------------------------------------

| Option           | Original Value | New Value   |
|------------------|----------------|-------------|
| Server Signature | On             | Off         |
| Server Tokens    | All            | ProductOnly |
| Trace Enable     | On             | Off         |


Configuración CloudFlare RailGun
--------------------------------

| Option                  | Original Value             | New Value                         |
|-------------------------|----------------------------|-----------------------------------|
| memcached.servers       | /tmp/memcached.sock        | /var/run/memcached/memcached.sock |
| activation.railgun_host | YOUR_PUBLIC_IP_OR_HOSTNAME | (user defined)                    |
| activation.token        | YOUR_TOKEN_HERE            | (user defined)                    |


Cambios en CloudFlare RailGun MemCached
----------------------------------------

| Option    | Original Value | New Value                            |
|-----------|----------------|--------------------------------------|
| PORT      | 11211          | 22222                                |
| USER      | memcached      | memcached                            |
| MAXCONN   | 1024           | 20480                                |
| CACHESIZE | 64             | 4096                                 |
| OPTIONS   |                | -s /var/run/memcached/memcached.sock |


### Precaución

Usalo bajo tu propio riesgo, si no sabes lo que estás haciendo probablemente no deberías usar este script. Yo mismo y cualquier contribuyente a este proyecto no asumimos absolutamente ninguna responsabilidad por lo que hagas con este script. Yo **recomiendo** leer el guión para que entiendas lo que hace antes de usarlo.

# Change Log

## [1.4.0](https://github.com/tripflex/cpsetup/tree/1.4.0) (2017-02-01)
[Full Changelog](https://github.com/tripflex/cpsetup/compare/1.3.3...1.4.0)

**Implemented enhancements:**

- Added AfterLogic WebMail Lite installer
- Added Let's Encrypt AutoSSL for cPanel installer
- Added import for CloudFlare new public key
- Added Disable Proxy Subdomains (whm.example.com, etc) to harden config call
- Added Disable SMTP Restrictions to harden config call (when using CSF this should NOT be enabled)
- Use hostname if nothing set at prompt or in file for RailGun Host
- Moved CloudFlare RailGun install process and config process to separate functions

**Bug Fixes:**
- Fixed/Updated URL to download ConfigServer Firewall install file
- Fixed incorrect function call for MySQL Tuner install

**Other:**
- Removed prompt to install CleanBackups
- Removed prompt to install PHP.ini Manager
- Removed prompt to install Account DNS Check
