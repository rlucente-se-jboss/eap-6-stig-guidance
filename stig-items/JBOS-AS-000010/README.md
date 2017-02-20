These instructions adapt the STIG "Fix Text" for item JBOS-AS-000010
to work with EAP 6.4.

# Disclaimer
These instructions were confirmed to work correctly on RHEL 6.8 and
RHEL 7.x, where operating system matters, as well as EAP 6.4 CP13.
None of this guidance is certified or officially supported by Red
Hat.  You must confirm that this is correct within your environment
and with your configuration.

# Overview
The STIG "Fix Text" outlines the instructions in section 2.2 of the
vendor document [How to Configure Server
Security](https://access.redhat.com/documentation/en/red-hat-jboss-enterprise-application-platform/6.4/paged/how-to-configure-server-security/chapter-2-securing-the-server-and-its-interfaces).

You should also use an approved TLS version per
[JBOS-AS-000650](../JBOS-AS-000650/README.md) and also make sure
that all passwords are protected within a password vault per
[JBOS-AS-000295](../JBOSS-AS-000295/README.md).

Sample code for a FIPS 140-2 Level 1 compliant password vault is
available
[here](https://github.com/rlucente-se-jboss/fips-compliant-vault).  The
`master` branch provides instructions to secure passwords on RHEL
using NSS.  The `bcfips` branch provides instructions to secure
passwords on any operating system using the [Legion of the Bouncy
Castle's certified FIPS 140-2 Level 1 crytographic
module](https://www.bouncycastle.org/fips-java).

NB:  The FIPS vault code is provided as an example only and it is
not supported by Red Hat.

# Additional Fix Text Guidance

## RHEL 7.3 Instructions using NSS DB
Rather than using JKS keystores, you can also leverage the Mozilla
Network Security Services on RHEL to have FIPS 140-2 compliant
crypto used for TLS connections.  The specific steps follow.

### Configure SunPKCS11-NSS Provider
This can be done two ways, with each option described below.

#### Option 1 - Edit the JRE Files
First, determine where your java distribution is located.  To do
that, type the command:

    java -XshowSettings:properties -version &| grep java.home

The showSettings option has been available since JVM 1.7 and up.
It is not supported in 1.6 and below.  You should see output similar
to:

    java.home = /usr/lib/jvm/java-1.8.0-openjdk-1.8.0.121-0.b13.el7_3.x86_64/jre

Go to the `${java.home}/lib/security` folder:

    cd /usr/lib/jvm/java-1.8.0-openjdk-1.8.0.121-0.b13.el7_3.x86_64/jre
    cd lib/security
    sudo cp java.security java.security.bak

Edit the file `java.security` file so that the security provider
list looks like the following stanza.  The key changes are to add
the SunPKCS11 provider and configure the sun internal ssl provider
to refer to it.

    #
    # List of providers and their preference orders (see above):
    #
    security.provider.1=sun.security.pkcs11.SunPKCS11 ${java.home}/lib/security/nss.cfg
    security.provider.2=sun.security.provider.Sun
    security.provider.3=sun.security.rsa.SunRsaSign
    security.provider.4=sun.security.ec.SunEC
    security.provider.5=com.sun.net.ssl.internal.ssl.Provider SunPKCS11-NSS
    security.provider.6=com.sun.crypto.provider.SunJCE
    security.provider.7=sun.security.jgss.SunProvider
    security.provider.8=com.sun.security.sasl.Provider
    security.provider.9=org.jcp.xml.dsig.internal.dom.XMLDSigRI
    security.provider.10=sun.security.smartcardio.SunPCSC

Next, edit the nss.cfg file to point to where you want to store
your certificates.  This file should look like:

    name = NSS
    nssLibraryDirectory = /usr/lib64
    nssSecmodDirectory = /etc/nssdb
    nssModule = fips
    attributes = compatibility
    handleStartupErrors = ignoreMultipleInitialisation

The `nssSecmodDirectory` must match where you wish to store the NSS
database files.  This configuration makes one configuration for all
java users on the host.  If you'd like to tailor this to specific
users, you can change the `java.security` definition of the SunPKCS11
provider to match:

    security.provider.1=sun.security.pkcs11.SunPKCS11 ${user.home}/nss.cfg

Within the `nss.cfg` file you can then change `nssSecmodDirectory`
to point to a local file owned by the user.  For example,

    nssSecmodDirectory = /home/myuser/nssdb

This approach assumes each account running java has a defined home
directory.

#### Option 2 - Override the JRE Files
Rather than edit a system-wide setting, each user on a host can
have their own `java.security` policy using the java security
overrides feature.  To do this, define a user-specific
`$HOME/java.security.properties` file that contains only the following
content:

    #
    # List of providers and their preference orders (see above):
    #
    security.provider.1=sun.security.pkcs11.SunPKCS11 ${user.home}/nss.cfg
    security.provider.2=sun.security.provider.Sun
    security.provider.3=sun.security.rsa.SunRsaSign
    security.provider.4=sun.security.ec.SunEC
    security.provider.5=com.sun.net.ssl.internal.ssl.Provider SunPKCS11-NSS
    security.provider.6=com.sun.crypto.provider.SunJCE
    security.provider.7=sun.security.jgss.SunProvider
    security.provider.8=com.sun.security.sasl.Provider
    security.provider.9=org.jcp.xml.dsig.internal.dom.XMLDSigRI
    security.provider.10=sun.security.smartcardio.SunPCSC

You'll need to define the `nss.cfg` file as described in option 1,
but you can also locate the nssdb directory in the user's home
directory rather than a system-wide location.

To use the property overrides, add the following line to
`$EAP_HOME/bin/standalone.conf` or `$EAP_HOME/bin/domain.conf`
depending on whether you're running in standalone or domain mode:

    JAVA_OPTS="$JAVA_OPTS -Djava.security.properties=$HOME/java.security.properties"

This also assumes that each user has their own EAP installation.
