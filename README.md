Overview
========
This guide represents my attempt to further flesh out and expand
upon the security configuration guidance in the approved Defense
Information Systems Agency Security Technical Implementation
Guidelines for Red Hat JBoss Enterprise Application Platform 6
hereafter referred to simply as the
[STIG](http://iasecontent.disa.mil/stigs/zip/U_JBOSS_EAP_6-3_STIG_V1R1_STIG.zip/README.md)
with its [release
memo](http://iasecontent.disa.mil/stigs/pdf/u_JBoss_EAP_6-3_stig_release_memo.pdf).
Those links are to the official released documents by DISA and they
should be the normative standard.  All of the content in this
repository will be shared with DISA for possible inclusion in future
releases of the STIG.

STIG Items
==========

* [JBOS-AS-000010 - HTTP management session traffic must be encrypted.](stig-items/JBOS-AS-000010/README.md)
* [JBOS-AS-000015 - HTTPS must be enabled for JBoss web interfaces.](stig-items/JBOS-AS-000015/README.md)
* [JBOS-AS-000025 - Java permissions must be set for hosted applications.](stig-items/JBOS-AS-000025/README.md)
* [JBOS-AS-000030 - The Java Security Manager must be enabled for the JBoss application server.](stig-items/JBOS-AS-000030/README.md)
* [JBOS-AS-000035 - The JBoss server must be configured with Role Based Access Controls.](stig-items/JBOS-AS-000035/README.md)
* [JBOS-AS-000040 - Users in JBoss Management Security Realms must be in the appropriate role.](stig-items/JBOS-AS-000040/README.md)
* [JBOS-AS-000045 - Silent Authentication must be removed from the Default Application Security Realm.](stig-items/JBOS-AS-000045/README.md)
* [JBOS-AS-000050 - Silent Authentication must be removed from the Default Management Security Realm.](stig-items/JBOS-AS-000050/README.md)
* [JBOS-AS-000075 - JBoss management interfaces must be secured.](stig-items/JBOS-AS-000045/README.md)
* [JBOS-AS-000080 - The JBoss server must generate log records for access and authentication events to the management interface.](stig-items/JBOS-AS-000080/README.md)
* [JBOS-AS-000085 - JBoss must be configured to allow only the ISSM (or individuals or roles appointed by the ISSM) to select which loggable events are to be logged.](stig-items/JBOS-AS-000085/README.md)
* [JBOS-AS-000095 - JBoss must be configured to initiate session logging upon startup.](stig-items/JBOS-AS-000095/README.md)
* [JBOS-AS-000105 - JBoss must be configured to log the IP address of the remote system connecting to the JBoss system/cluster.](stig-items/JBOS-AS-000105/README.md)
* [JBOS-AS-000110 - JBoss must be configured to produce log records containing information to establish what type of events occurred.](stig-items/JBOS-AS-000110/README.md)
* [JBOS-AS-000115 - JBoss Log Formatter must be configured to produce log records that establish the date and time the events occurred.](stig-items/JBOS-AS-000115/README.md)
* [JBOS-AS-000120 - JBoss must be configured to produce log records that establish which hosted application triggered the events.](stig-items/JBOS-AS-000120/README.md)
* [JBOS-AS-000125 - JBoss must be configured to record the IP address and port information used by management interface network traffic.](stig-items/JBOS-AS-000125/README.md)
* [JBOS-AS-000130 - The application server must produce log records that contain sufficient information to establish the outcome of events.](stig-items/JBOS-AS-000130/README.md)
* [JBOS-AS-000135 - JBoss ROOT logger must be configured to utilize the appropriate logging level.](stig-items/JBOS-AS-000135/README.md)
* [JBOS-AS-000165 - File permissions must be configured to protect log information from any type of unauthorized read access.](stig-items/JBOS-AS-000165/README.md)
* [JBOS-AS-000170 - File permissions must be configured to protect log information from unauthorized modification.](stig-items/JBOS-AS-000170/README.md)
* [JBOS-AS-000175 - File permissions must be configured to protect log information from unauthorized deletion.](stig-items/JBOS-AS-000175/README.md)
* [JBOS-AS-000195 - JBoss log records must be off-loaded onto a different system or system component a minimum of every seven days.](stig-items/JBOS-AS-000195/README.md)
* [JBOS-AS-000210 - mgmt-users.properties file permissions must be set to allow access to authorized users only.](stig-items/JBOS-AS-000210/README.md)
* [JBOS-AS-000220 - JBoss process owner interactive access must be restricted.](stig-items/JBOS-AS-000220/README.md)
* [JBOS-AS-000225 - Google Analytics must be disabled in EAP Console.](stig-items/JBOS-AS-000225/README.md)
* [JBOS-AS-000230 - JBoss process owner execution permissions must be limited.](stig-items/JBOS-AS-000230/README.md)
* [JBOS-AS-000235 - JBoss QuickStarts must be removed.](stig-items/JBOS-AS-000235/README.md)
* [JBOS-AS-000240 - Remote access to JMX subsystem must be disabled.](stig-items/JBOS-AS-000240/README.md)
* [JBOS-AS-000245 - Welcome Web Application must be disabled.](stig-items/JBOS-AS-000245/README.md)
* [JBOS-AS-000250 - Any unapproved applications must be removed.](stig-items/JBOS-AS-000250/README.md)
* [JBOS-AS-000255 - JBoss application and management ports must be approved by the PPSM CAL.](stig-items/JBOS-AS-000255/README.md)
* [JBOS-AS-000260 - The JBoss Server must be configured to utilize a centralized authentication mechanism such as AD or LDAP.](stig-items/JBOS-AS-000260/README.md)
* [JBOS-AS-000265 - The JBoss Server must be configured to use certificates to authenticate admins.](stig-items/JBOS-AS-000265/README.md)
* [JBOS-AS-000275 - The JBoss server must be configured to use individual accounts and not generic or shared accounts.](stig-items/JBOS-AS-000275/README.md)
* [JBOS-AS-000285 - The JBoss server must be configured to bind the management interfaces to only management networks.](stig-items/JBOS-AS-000285/README.md)
* [JBOS-AS-000290 - JBoss management Interfaces must be integrated with a centralized authentication mechanism that is configured to manage accounts according to DoD policy.](stig-items/JBOS-AS-000290/README.md)
* [JBOS-AS-000295 - The JBoss Password Vault must be used for storing passwords or other sensitive configuration information.](stig-items/JBOS-AS-000295/README.md)
* [JBOS-AS-000300 - JBoss KeyStore and Truststore passwords must not be stored in clear text.](stig-items/JBOS-AS-000300/README.md)
* [JBOS-AS-000305 - LDAP enabled security realm value allow-empty-passwords must be set to false.](stig-items/JBOS-AS-000305/README.md)
* [JBOS-AS-000310 - JBoss must utilize encryption when using LDAP for authentication.](stig-items/JBOS-AS-000310/README.md)
* [JBOS-AS-000320 - The JBoss server must be configured to restrict access to the web servers private key to authenticated system administrators.](stig-items/JBOS-AS-000320/README.md)
* [JBOS-AS-000355 - The JBoss server must separate hosted application functionality from application server management functionality.](stig-items/JBOS-AS-000355/README.md)
* [JBOS-AS-000400 - JBoss file permissions must be configured to protect the confidentiality and integrity of application files.](stig-items/JBOS-AS-000400/README.md)
* [JBOS-AS-000425 - Access to JBoss log files must be restricted to authorized users.](stig-items/JBOS-AS-000425/README.md)
* [JBOS-AS-000470 - Network access to HTTP management must be disabled on domain-enabled application servers not designated as the domain controller.](stig-items/JBOS-AS-000470/README.md)
* [JBOS-AS-000475 - The application server must prevent non-privileged users from executing privileged functions to include disabling, circumventing, or altering implemented security safeguards/countermeasures.](stig-items/JBOS-AS-000475/README.md)
* [JBOS-AS-000480 - The JBoss server must be configured to log all admin activity.](stig-items/JBOS-AS-000480/README.md)
* [JBOS-AS-000505 - The JBoss server must be configured to utilize syslog logging.](stig-items/JBOS-AS-000505/README.md)
* [JBOS-AS-000545 - Production JBoss servers must not allow automatic application deployment.](stig-items/JBOS-AS-000545/README.md)
* [JBOS-AS-000550 - Production JBoss servers must log when failed application deployments occur.](stig-items/JBOS-AS-000550/README.md)
* [JBOS-AS-000555 - Production JBoss servers must log when successful application deployments occur.](stig-items/JBOS-AS-000555/README.md)
* [JBOS-AS-000625 - JBoss must be configured to use DoD PKI-established certificate authorities for verification of the establishment of protected sessions.](stig-items/JBOS-AS-000625/README.md)
* [JBOS-AS-000640 - The JBoss server, when hosting mission critical applications, must be in a high-availability (HA) cluster.](stig-items/JBOS-AS-000640/README.md)
* [JBOS-AS-000650 - JBoss must be configured to use an approved TLS version.](stig-items/JBOS-AS-000650/README.md)
* [JBOS-AS-000655 - JBoss must be configured to use an approved cryptographic algorithm in conjunction with TLS.](stig-items/JBOS-AS-000655/README.md)
* [JBOS-AS-000680 - Production JBoss servers must be supported by the vendor.](stig-items/JBOS-AS-000680/README.md)
* [JBOS-AS-000685 - The JRE installed on the JBoss server must be kept up to date.](stig-items/JBOS-AS-000685/README.md)
* [JBOS-AS-000690 - JBoss must be configured to generate log records when successful/unsuccessful attempts to modify privileges occur.](stig-items/JBOS-AS-000690/README.md)
* [JBOS-AS-000695 - JBoss must be configured to generate log records when successful/unsuccessful attempts to delete privileges occur.](stig-items/JBOS-AS-000695/README.md)
* [JBOS-AS-000700 - JBoss must be configured to generate log records when successful/unsuccessful logon attempts occur.](stig-items/JBOS-AS-000700/README.md)
* [JBOS-AS-000705 - JBoss must be configured to generate log records for privileged activities.](stig-items/JBOS-AS-000705/README.md)
* [JBOS-AS-000710 - JBoss must be configured to generate log records that show starting and ending times for access to the application server management interface.](stig-items/JBOS-AS-000710/README.md)
* [JBOS-AS-000715 - JBoss must be configured to generate log records when concurrent logons from different workstations occur to the application server management interface.](stig-items/JBOS-AS-000715/README.md)
* [JBOS-AS-000720 - JBoss must be configured to generate log records for all account creations, modifications, disabling, and termination events.](stig-items/JBOS-AS-000720/README.md)
* [JBOS-AS-000730 - The JBoss server must be configured to use DoD- or CNSS-approved PKI Class 3 or Class 4 certificates.](stig-items/JBOS-AS-000730/README.md)
* [JBOS-AS-000735 - JBoss servers must be configured to roll over and transfer logs on a minimum weekly basis.](stig-items/JBOS-AS-000735/README.md)
