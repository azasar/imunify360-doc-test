﻿# Config File Description


Imunify360 config file is available on the following location after installation:

<span class="notranslate">_/etc/sysconfig/imunify360/imunify360.config_</span>

In the config file it is possible to set up Imunify360 configuration. The following options are available:

<table>
<tr>
<th colspan="2" align="left"><span class="notranslate">AUTO_WHITELIST:</span></th>
</tr>
<tr>
<td width="250px;"><span class="notranslate">timeout: 1440</span></td><td># set in minutes how long to keep automatically whitelisted IP</td></tr>
<tr><td><span class="notranslate">after_unblock_timeout: 1440</span></td><td>
# set in minutes for how long IP will be added to the <span class="notranslate">White List</span> after it passes Imunify360 CAPTCHA</td></tr>
<tr>
<th colspan="2" align="left"><span class="notranslate">DOS:</span></th>
</tr>
<tr>
<td width="250px;"><span class="notranslate">enabled: false</span></td><td># allows to enable (<span class="notranslate">true</span>) or disable (<span class="notranslate">false</span>) DOS detection</td></tr>
<tr><td><span class="notranslate">interval: 30</span></td><td># interval in seconds between DoS detection system activation</td></tr>
<tr><td><span class="notranslate">default_limit: 250</span></td><td># maximum default limit of connections from remote IP to local port before DoS protection will be triggered. Cannot be set lower than 100</td></tr>
<tr>
<td><span class="notranslate">port_limits:</span>
</td><td># allows to set limits per local port</td>
</tr>
<tr>
<td>80: 150
</td><td># limit on port 80 is set to 150 connections</td>
</tr>
<tr>
<th colspan="2" align="left"><span class="notranslate">INCIDENT_LOGGING:</span></th>
</tr>
<tr>
<td width="250px;"><span class="notranslate">min_log_level: 4</span></td><td># minimum severity level for incidents displayed in UI. Please find the levels description <a href="/dashboard/#incidents-logging">here</a></td></tr>
<tr><td><span class="notranslate">num_days: 100</span></td><td># incidents older than <span class="notranslate"><em>num_days</em></span> are automatically deleted</td></tr>
<tr><td><span class="notranslate">limit: 100000</span></td><td># how many incidents should be stored in Imunify360 log file</td></tr>
<tr><td><span class="notranslate">ui_autorefresh_timeout: 10</span></td><td># set auto refresh time for incidents in user interface</td></tr>
<tr>
<th align="left"><span class="notranslate">MOD_SEC:</span></th>
<th align="left"><span class="notranslate"># defines ModSecurity settings</span></th>
</tr>
<tr>
<td width="250px;"><span class="notranslate">ruleset: FULL</span></td><td># defines what ruleset to use: <span class="notranslate">FULL</span> (default value) or <span class="notranslate">MINIMAL</span>. If the amount of RAM on the server is less than 2.1GB, the ruleset value is automatically set to <span class="notranslate">MINIMAL</span>.</td></tr>
<tr>
<td width="250px;"><span class="notranslate">cms_account_compromise_prevention: true</span></td><td># enables WordPress account brute-force protection.</td></tr>
<td width="250px;"><span class="notranslate"><font color="Red">prev_settings: </font></span></td><td><font color="Red">For internal usage, do not edit</font></td></tr>
<tr>
<th colspan="2" align="left"><span class="notranslate">MOD_SEC_BLOCK_BY_SEVERITY:</span></th></tr>
 <tr><td><span class="notranslate">enable: true</span></td><td># allows to enable or disable option that moves IPs to <span class="notranslate">Gray List</span> if the ModSecurity rule is triggered</td></tr>
<tr><td><span class="notranslate">max_incidents: 2</span></td><td># set a number of repeats of the ModSecurity incident from the same IP for adding it to <span class="notranslate">Gray List</span></td></tr>
<tr><td><span class="notranslate">denied_num_limit: 2</span></td>
<td># set a number of repeats of the ModSecurity incidents that got Access Denied error from the same IP for adding it to <span class="notranslate">Gray List</span></td></tr>
<tr><td><span class="notranslate">check_period: 120</span></td>
<td># set a period in seconds during which incident from the same IP will be recorded as a repeat</td></tr>
<tr><td><span class="notranslate">severity_limit: 2</span></td>
<td># set a level of severity for DOS detection sensitivity. <a href="/dashboard/#settings">Read more</a> about severity levels</td></tr>
<tr>
<th align="left"><span class="notranslate">MOD_SEC_BLOCK_BY_CUSTOM_RULE:</span></th><th  align="left"># this section allows to add custom configuration for blocking by ModSecurity incidents</th></tr>
<tr><td>33332:</td>
<td># set ModSecurity rule ID</td></tr>
<tr><td><span class="notranslate">check_period: 120</span></td>
<td># set a period in seconds during which incident from the same IP will be recorded as a repeat</td></tr>
<tr><td><span class="notranslate">max_incidents: 10</span></td>
<td># set a number of repeats of the ModSecurity incident from the same IP for adding it to <span class="notranslate">Gray List</span></td></tr>
<tr>
<th colspan="2" align="left"><span class="notranslate">MALWARE_SCANNING:</span></th></tr>
<tr><td><span class="notranslate">try_restore_from_backup_first: false</span></td>
<td># allows to enable (<span class="notranslate">true</span>) or disable (<span class="notranslate">false</span>) automatic malicious file restore from backup if a clean copy exists,
otherwise <span class="notranslate"><em>default_action</em></span> is applied</td></tr>
<tr><td><span class="notranslate">default_action: quarantine</span></td>
<td># default action on malicious file detected.<br>
Available options:
<ul><li><span class="notranslate">quarantine</span> – do not delete and move to quarantine</li>
<li><span class="notranslate">notify</span> – do not delete and send email notification</li>
<li><span class="notranslate">delete</span> – delete malicious file</li>
<li><span class="notranslate">cleanup</span> – cleanup malicious file</li>
<li><span class="notranslate">cleanup_or_quarantine</span> – choose what to do with a malicious file</li></ul></td></tr>
<tr><td><span class="notranslate">enable_scan_inotify: False</span></td>
<td># enable (<span class="notranslate">true</span>) or disable (<span class="notranslate">false</span>) real-time scanning for modified files using <a href="https://en.wikipedia.org/wiki/Inotify" target="_blank">inotify</a> library</td></tr>
<tr><td><span class="notranslate">enable_scan_pure_ftpd: true</span></td>
<td># enable (<span class="notranslate">true</span>) or disable (<span class="notranslate">false</span>) real-time scanning for files uploaded through PureFTPd</td></tr>
<tr><td><span class="notranslate">enable_scan_modsec: true</span></td>
<td>#  enable (<span class="notranslate">true</span>) or disable (<span class="notranslate">false</span>) real-time scanning of all the files
that were uploaded via http/https. Note that it requires <a href="https://modsecurity.org" target="_blank">ModSecurity</a> to be installed</td></tr>
<tr><td><span class="notranslate">max_signature_size_to_scan: 1048576</span></td>
<td># max file size to scan in the standard mode; value is set in bytes</td></tr>
<tr><td><span class="notranslate">max_cloudscan_size_to_scan: 10485760</span></td>
<td># max file size to scan in the cloud-assisted (by hashes) mode; value is set in bytes</td></tr>
<tr><td><span class="notranslate">max_mrs_upload_file: 10485760</span></td>
<td># max file size to upload to CloudLinux malware research service; value is set in bytes</td></tr>
<tr><td><span class="notranslate">detect_elf: False</span></td>
<td># enable (<span class="notranslate">True</span>) or disable (<span class="notranslate">False</span>) (default value) binary (ELF) malware detection</td></tr>
<tr><td><span class="notranslate"><font color="Red">notify_on_detect: False</font></span></td>
<td><font color="Red"># notify (<span class="notranslate">True</span>) or not (<span class="notranslate">False</span>) (default value) an admin when malware is detected</font></td></tr>
<tr><td><span class="notranslate"><font color="Red">optimize_realtime_scan: False</font></span></td>
<td><font color="Red">Use optimized engine for realtime scan</font></td></tr>
<tr><td><span class="notranslate"><font color="Red">sends_file_for_analysis: True</font></span></td>
<td><font color="Red"># send (<span class="notranslate">True</span>) (default value) or not (<span class="notranslate">False</span>) malicious and suspicious files to the Imunify team for analysis</font></td></tr>
<tr><td><span class="notranslate"><font color="Red">i360_clamd: False</font></span></td>
<td><font color="Red">Obsolete (not used)</font></td></tr>
<tr><td><span class="notranslate"><font color="Red">show_clamav_results: False</font></span></td>
<td><font color="Red">Obsolete (not used)</font></td></tr>
<tr><td><span class="notranslate"><font color="Red">clamav_binary: True</font></span></td>
<td><font color="Red">Obsolete (not used)</font></td></tr>
<tr><td><span class="notranslate"><font color="Red">scan_modified_files: True</font></span></td>
<td><font color="Red"># enable (<span class="notranslate">True</span>) (default value) or disable (<span class="notranslate">False</span>) real-time scanning for modified files using inotify library. The Scanner searches for modified files in user’s DocumentRoot directories.</font></td></tr>
<tr><td><span class="notranslate"><font color="Red">cloud_assisted_scan: True</font></span></td>
<td><font color="Red"># need a description</font></td></tr>
<tr><td><span class="notranslate"><font color="Red">rapid_scan: False</font></span></td>
<td><font color="Red"># speeds up (<span class="notranslate">True</span>) ot not (<span class="notranslate">False</span>) (default value) repeated scans based on smart re-scan approach, local result caching and cloud-assisted scan.</font></td></tr>
<tr>
<th colspan="2" align="left"><span class="notranslate">CAPTCHA:</span></th></tr>
<tr><td><span class="notranslate">cert_refresh_timeout: 3600</span></td>
<td># set in seconds how often SSL certificate will be refreshed</td></tr>
<tr>
<th colspan="2" align="left"><span class="notranslate">ERROR_REPORTING:</span></th></tr>
<tr><td><span class="notranslate">enable: true</span></td>
<td># automatically report errors to imunify360 team</td></tr>
<tr>
<th colspan="2" align="left"><span class="notranslate">SEND_ADDITIONAL_DATA:</span></th></tr>
<tr><td><span class="notranslate">enable: true</span></td>
<td># send anonymized data from query string/post parameters and cookies.</td></tr>
<tr>
<th align="left"><span class="notranslate">NETWORK_INTERFACE:</span></th>
<th aligh="left"># manages for what network interfaces Imunify360 rules will be applied</th></td>
<tr>
<td><span class="notranslate">eth_device: null</span></td>
<td># by default, Imunify360 will auto-configure iptables to filter all traffic. 
If you want iptables rules to be applied to a specific NIC only, list them here (e.g. <span class="notranslate">eth1</span>)</td></tr>
<tr><td><span class="notranslate">eth6_device: null</span></td>
<td># it is the same as <span class="notranslate"><em>eth_device</em></span>, but configures ip6tables to use specific device</td></tr>
<tr><td><span class="notranslate">eth_device_skip: []</span></td>
<td># if you don't want iptables\ip6tables rules to be applied to specific NICs, list them here (e.g <span class="notranslate">[eth1, eth2]</span>)</td></tr>
<tr>
<th colspan="2" align="left"><span class="notranslate">BACKUP_RESTORE:</span></th></tr>
<tr><td><span class="notranslate">max_days_in_backup: 90</span></td>
<td># restore from backup files that are not older than <span class="notranslate"><em>max_days_in_backup</em></span></td></tr>
<tr><td><span class="notranslate">cl_backup_allowed: True</span></td>
<td># show <span class="notranslate">CloudLinux Backup</span> in the list of available backup system (<span class="notranslate">True</span>) or hide it (<span class="notranslate">False</span>)</td></tr>
<tr><td><span class="notranslate"><font color="Red">cl_on_premise_backup_allowed: False</font></span></td>
<td><font color="Red"># do not allow CloudLinux backup (<span class="notranslate">False</span>) or allow it (<span class="notranslate">True</span>)</font></td></tr>
<tr>
<th colspan="2" align="left"><span class="notranslate">CAPTCHA_DOS:</span></th></tr>
<tr><td><span class="notranslate">enabled: true</span></td>
<td># enable (<span class="notranslate">true</span>) or disable (<span class="notranslate">false</span>) CAPTCHA Dos protection</td></tr>
<tr><td><span class="notranslate">time_frame: 21600</span></td>
<td># set a period in seconds during which requests to CAPTCHA from the same IP
will be recorded as repeated</td></tr>
<tr><td><span class="notranslate">max_count: 100</span></td>
<td># set the maximum number of repeated CAPTCHA requests after which IP is moved
to the CAPTCHA Dos list without an ability to request CAPTCHA again</td></tr>
<tr><td><span class="notranslate">timeout: 864000</span></td>
<td># set in seconds the time on which to add the IP in CAPTCHA Dos list without an ability
to request CAPTCHA again</td></tr>
<tr>
<th colspan="2" align="left"><span class="notranslate">BLOCKED_PORTS:</span></th></tr>
<tr><td><span class="notranslate">default_mode: allowed</span></td>
<td># defines the default state of ports which is not explicitly set by user (<span class="notranslate"><em>denied</em></span> by default or <span class="notranslate"><em>allowed</em></span> by default). Currently only <span class="notranslate"><em>allowed</em></span> is supported</td></tr>
<tr>
<th colspan="2" align="left"><span class="notranslate">WEBSHIELD:</span></th></tr>
<tr><td><span class="notranslate">known_proxies_support: true</span></td>
<td># enable CDN support, treat IPs behind CDN as any other IPs</td></tr>
<tr><td><span class="notranslate">enable: true</span></td>
<td># enable (true) (default value) or disable (false) WebShield</td></tr>
<tr>
<th colspan="2" align="left"><span class="notranslate">PROACTIVE_DEFENСE:</span></th></tr>
<tr><td><span class="notranslate">blamer: false</span></td>
<td># enable (<span class="notranslate">true</span>) or disable (<span class="notranslate">false) Blamer</span></td></tr>
<tr><td><span class="notranslate">mode: KILL</span></td>
<td># available modes:<ul><li><span class="notranslate">KILL</span></li><li><span class="notranslate">DISABLED</span></li><li><span class="notranslate">LOG</span></li></ul></td></tr>
<tr>
<th colspan="2" align="left"><span class="notranslate">MALWARE_SCAN_INTENSITY:</span></th></tr>
<tr><td><span class="notranslate">cpu: 6</span></td>
<td># intensity level for CPU consumption. Can be set from 1 to 7, default is 2</td></tr>
<tr><td><span class="notranslate">io: 6</span></td>
<td># intensity level for file operations. Can be set from 1 to 7, default is 2</td></tr>
<tr><td><span class="notranslate"><font color="Red">ram: 1024</font></span></td>
<td><font color="Red"># intensity level for RAM consumption. Minimum value is 1024, default is 2048</font></td></tr>
<tr>
<th colspan="2" align="left"><span class="notranslate">MALWARE_SCAN_SCHEDULE:</span></th></tr>
<tr><td><span class="notranslate">day_of_month: 4</span></td>
<td># when the background scan shall start, day of the month. Can be from 1 to 31, the default value is the next day after the installation</td></tr>
<tr><td><span class="notranslate">day_of_week: 0</span></td>
<td># when the background scan shall start, day of the week. Can be from 0 to 7 (0 for Sunday, 1 for Monday..., 7 for Sunday (again)), the default value is 0</td></tr>
<tr><td><span class="notranslate">hour: 3</span></td>
<td># when the background scan shall start, hour. Can be from 0 to 23, the default value is 3</td></tr>
<tr><td><span class="notranslate">interval: none</span></td>
<td># interval of scan. Supported values: strings <span class="notranslate">`none`</span>, <span class="notranslate">`day`</span>, <span class="notranslate">`week`</span>, <span class="notranslate">`month`</span>, the default value is <span class="notranslate">`none`</span> (no scan)</td></tr>
<tr>
<th align="left"><span class="notranslate">PAM:</span></th>
<th align="left"># effective way to prevent brute-force attacks against FTP/SSH</th></tr>
<tr><td><span class="notranslate">enable: false</span></td>
<td># enable (<span class="notranslate">true</span>) or disable (<span class="notranslate">false</span>) (default value) PAM brute-force attack protection</td></tr>
<tr><td><span class="notranslate">PAM.exim_dovecot_protection: false</span></td>
<td># enable (<span class="notranslate">true</span>) or disable (<span class="notranslate">false</span>) (default value) Exim+Dovecot brute-force attack protection against Dovecot brute-force attacks.</td></tr>
<tr>
<th align="left"><span class="notranslate">KERNELCARE:</span></th>
<th align="left"># KernelCare extension for Imunify360 which allows tracing malicious invocations to detect privilege escalation attempts</th></tr>
<tr><td><span class="notranslate">edf: false</span></td>
<td># enable (<span class="notranslate">true</span>) or disable (<span class="notranslate">false</span>) (default value) exploit detection framework</td></tr>
<tr><th colspan="2" align="left"><span class="notranslate"><font color="Red">MALWARE_CLEANUP:</font></span></th></tr>
<tr><td><span class="notranslate"><font color="Red">trim_file_instead_of_removal: True</font></span></td>
<td><font color="Red"># do not remove infected file during cleanup but make the file zero-size (for malwares like web-shells) (<span class="notranslate">True</span>) (default value)</font></td></tr>
<tr><td><span class="notranslate"><font color="Red">keep_original_files_days: 14</font></span></td>
<td><font color="Red"># the original infected file is available for restore within the defined period. The default is 14 days. The minimum value is one day.</font></td></tr>
<tr><th colspan="2" align="left"><span class="notranslate"><font color="Red">OSSEC:</font></span></th></tr>
<tr><td><span class="notranslate"><font color="Red">active_response: False</font></span></td>
<td><font color="Red"># block (<span class="notranslate">True</span>) access to a specific server port being attacked. The default value is <span class="notranslate">False</span>.</font></td></tr>
<tr><th colspan="2" align="left"><span class="notranslate"><font color="Red">ADMIN_CONTACTS:</font></span></th></tr>
<tr><td><span class="notranslate"><font color="Red">emails: youremail@email.com</font></span></td>
<td><font color="Red"># your email to receive reports about critical issues, security alerts or system misconfigurations detected on your servers.</font></td></tr>
<tr><th colspan="2" align="left"><span class="notranslate"><font color="Red">SMTP_BLOCKING:</font></span></th></tr>
<tr><td><span class="notranslate"><font color="Red">enable: False</font></span></td>
<td><font color="Red"># enable (<span class="notranslate">True</span>) or disable (<span class="notranslate">False</span>) (default value) SMTP Traffic Management. When enabled, the outgoing SMTP traffic would be blocked according to the settings.</font></td></tr>
<tr><td><span class="notranslate"><font color="Red">ports: 25,587,465</font></span></td>
<td><font color="Red"># a list of the ports to be blocked. The defaults are: 25, 587,465.</font></td></tr>
<tr><td><span class="notranslate"><font color="Red">allow_users:</font></span></td>
<td><font color="Red"># a list of users to be ignored (not blocked). By default it is empty. Including Unix and cPanel users (if a process that sends an email has a UID of one of the `allow_users`, it will not be blocked).</font></td></tr>
<tr><td><span class="notranslate"><font color="Red">allow_groups: mail</font></span></td>
<td><font color="Red"># a list of the groups to be ignored (not blocked). By default it is empty. Including Unix and cPanel users (if a process that sends an email has a UID of one of the `allow_users`, it will not be blocked).</font></td></tr>
<tr><td><span class="notranslate"><font color="Red">allow_local: False</font></span></td>
<td><font color="Red"># block (<span class="notranslate">True</span>) all, except the local SMTP (localhost). <span class="notranslate">False</span> is the default value.</font></td></tr>
<tr><td><span class="notranslate"><font color="Red">redirect: False</font></span></td>
<td><font color="Red"># enable (<span class="notranslate">True</span>) or disable (<span class="notranslate">False</span>) (the default value) automatic redirection to the local ports for outgoing mail traffic.</font></td></tr>
<tr><th colspan="2" align="left"><span class="notranslate"><font color="Red">CSF_INTEGRATION:</font></span></th></tr>
<tr><td><span class="notranslate"><font color="Red">catch_lfd_events: True</font></span></td>
<td><font color="Red"># let (<span class="notranslate">True</span>) (the default value) Imunify360 use Login Failure Daemon (LFD) as a source for security events.</font></td></tr>
<tr><th colspan="2" align="left"><span class="notranslate"><font color="Red">PERMISSIONS:</font></span></th></tr>
<tr><td><span class="notranslate"><font color="Red">support_form: True</font></span></td>
<td><font color="Red"># show (<span class="notranslate">True</span>) (the default value) or hide (<span class="notranslate">False</span>) the Support icon in the Imunify360 UI.</font></td></tr>
<tr><td><span class="notranslate"><font color="Red">user_ignore_list: True</font></span></td>
<td><font color="Red"># show (<span class="notranslate">True</span>) (the default value) or hide (<span class="notranslate">False</span>) the Ignore List tab for end-users in the Imunify360 UI.</font></td></tr>
<tr><th colspan="2" align="left"><span class="notranslate"><font color="Red">STOP_MANAGING:</font></span></th></tr>
<tr><td><span class="notranslate"><font color="Red">modsec_directives: False</font></span></td>
<td><font color="Red">For internal use, do not edit</font></td></tr>
<tr><th colspan="2" align="left"><span class="notranslate"><font color="Red">WEB_SERVICES:</font></span></th></tr>
<tr><td><span class="notranslate"><font color="Red">http_ports: </font></span></td>
<td><font color="Red">Additional http ports for captcha</font></td></tr>
<tr><td><span class="notranslate"><font color="Red">https_ports: </font></span></td>
<td><font color="Red">Additional https ports for captcha</font></td></tr>
</table>

<span class="notranslate">Active Response</span> is an ossec-driven (IDS) feature of Imunify360 which has been re-engineered to make it capable of blocking access to a specific server port being attacked.

The purpose of the feature is significantly reducing false positive rate while increasing its capabilities to detect and block aggressive brute force requests.

In order to activate <span class="notranslate">Active Response, </span>the following lines should be added into <span class="notranslate">_/etc/sysconfig/imunify360/imunify360.config_</span>:
<div class="notranslate">

```
OSSEC:
  active_response: true
```

</div>
and then restart Imunify360 service:
<div class="notranslate">

```
systemctl restart imunify360
```

</div>

### How to apply changes from CLI

In order to apply changes via command-line interface (CLI), you can use the following command:

<div class="notranslate">

```
imunify360-agent config update ‘{"SECTION": {"parameter": value}}’ 
```
</div>

For example, if you want to set <span class="notranslate">`MALWARE_SCAN_INTENSITY.cpu = 5`</span> from a command line, then you should execute the following command:

<div class="notranslate">

```
imunify360-agent config update ‘{"MALWARE_SCAN_INTENSITY": {"cpu": 5}}’
```
</div>

It is also possible to apply several parameters at once. For example:

<div class="notranslate">

```
imunify360-agent config update '{"PAM": {"exim_dovecot_protection": false, "enable":true}}'
```
</div>
