#FreeBSD DOD CAC Smart Card
###Tested on FreeBSD 13-RELEASE with 
###SCM Microsystems Inc. SCR 355 reader

**install:**
- opensc
- pcsc-lite
- pcsc-tools

**add line to /etc/rc.conf**
> pcscd_enable="YES"

**add lines to /etc/devd.conf**
> attach 100 {
>         device-name "ugen[0-9]+";
>         action "/usr/local/sbin/pcscd -H";
> };
> 
> detach 100 {
>         device-name "ugen[0-9]+";
>         action "/usr/local/sbin/pcscd -H";
> };

**start the service:**
> service pcscd onestart 

**check:**
> opensc-tool -l
> pcsc_scan

**Firefox** 
- about:preferences#privacy

*Add the certificates downloaded from:*
- https://militarycac.com/maccerts/AllCerts.zip

*Path to security module*
- /usr/local/lib/pkcs11/opensc-pkcs11.so

