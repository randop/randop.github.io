---
layout: post
title:  "Add SSL functionality without any changes on application code"
date:   2018-10-22 10:00:00 +0800
categories: cybersecurity stunnel cloud
---
The [Stunnel](https://www.stunnel.org/) program is designed to work as an SSL encryption wrapper between remote client and local (inetd-startable) or remote server. It can be used to add SSL functionality to commonly used inetd daemons like POP2, POP3, and IMAP servers without any changes in the program’s code.

What [Stunnel](https://www.stunnel.org/) basically does is that it turns any insecure TCP port into a secure encrypted port using OpenSSL package for cryptography. It’s somehow like a small secure VPN that runs on specific ports.

More information on setting up Stunnel can be found here [https://www.digitalocean.com/community/tutorials/how-to-set-up-an-ssl-tunnel-using-stunnel-on-ubuntu](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-ssl-tunnel-using-stunnel-on-ubuntu)

An example configuration for stunnel.conf 
```
; Sample stunnel configuration file for Unix by Michal Trojnara 2002-2014
; Some options used here may be inadequate for your particular configuration
; This sample file does *not* represent stunnel.conf defaults
; Please consult the manual for detailed description of available options

; **************************************************************************
; * Global options                                                         *
; **************************************************************************

; A copy of some devices and system files is needed within the chroot jail
; Chroot conflicts with configuration file reload and many other features
; Remember also to update the logrotate configuration.
;chroot = /var/lib/stunnel4/
; Chroot jail can be escaped if setuid option is not used
;setuid = stunnel4
;setgid = stunnel4

; PID file is created inside the chroot jail (if enabled)
pid = /var/run/stunnel4.pid

; Debugging stuff (may be useful for troubleshooting)
;debug = 7
;output = /var/log/stunnel4/stunnel.log

; **************************************************************************
; * Service defaults may also be specified in individual service sections  *
; **************************************************************************

; Certificate/key is needed in server mode and optional in client mode
cert = /etc/stunnel/stunnel.pem
;key = /etc/stunnel/mail.pem

[ot1]
accept = 5061
connect = 5062
TIMEOUTclose = 0

[ot2]
accept = 444
connect = 5062
TIMEOUTclose = 0

; vim:ft=dosini
```