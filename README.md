# xval-decrypt-web

Hosted through github pages at https://www.mitchellwaite.ca/xval-decrypt-web/

Simple web app to decrypt Xbox 360 XVal data, and can be used to determine if any security events have been logged to the Xbox 360's flash memory. Logged events indicate a security violation of some sort and might be an indication of a future console ban. Xval also indicates whether the console is currently banned.

The X value and console serial number can be found under System Settings > Console Settings > System Info.

![system info screen](sysinfo.png)

Only CryptoJS is used here (because DES...) so there's minimal bloat. There are no CDN references or other libraries and the app can be downloaded and run locally without an internet connection.

Based on the python script originally written by Redline99.

- Originally posted at XboxHacker: http://www.xboxhacker.org/index.php?topic=16401.0

## Test Values

- Serial: 031897772807 / X: DA9C-DC84-43A9-BB4C should return a console ban flag (borrowed from https://github.com/landaire/xval)
- Serial: 457649714305 / X: 6286-1A08-2FF3-0F77 should be clean (borrowed from https://www.simplehelp.net/2020/06/19/how-to-format-xbox-360-hard-drives/)


## Event Flags

- FLAG_SSB_NONE                         = 0x0000
- FLAG_SSB_AUTH_EX_FAILURE_D            = 0x0001	# DEPRECATED
- FLAG_SSB_AUTH_EX_NO_TABLE_D           = 0x0002	# DEPRECATED
- FLAG_SSB_AUTH_EX_RESERVED             = 0x0004
- FLAG_SSB_INVALID_DVD_GEOMETRY         = 0x0008
- FLAG_SSB_INVALID_DVD_DMI              = 0x0010
- FLAG_SSB_DVD_KEYVAULT_PAIR_MISMATCH_D = 0x0020	# DEPRECATED
- FLAG_SSB_CRL_DATA_INVALID_D           = 0x0040	# DEPRECATED
- FLAG_SSB_CRL_CERTIFICATE_REVOKED      = 0x0080
- FLAG_SSB_UNAUTHORIZED_INSTALL         = 0x0100
- FLAG_SSB_KEYVAULT_POLICY_VIOLATION    = 0x0200
- FLAG_SSB_CONSOLE_BANNED_D             = 0x0400	# DEPRECATED
- FLAG_SSB_ODD_VIOLATION                = 0x0800
- FLAG_SSB_CIV_HASH_FAILURE             = 0x1000
- FLAG_SSB_AUTH_EX_NO_TABLE             = 0x2000
- FLAG_SSB_CRL_DATA_INVALID             = 0x4000
- FLAG_SSB_ODD_ENFORCE_THROUGHPUT_LOW   = 0x8000
- FLAG_SSB_ODD_ENFORCE_THROUGHPUT_HIGH  = 0x10000

Ref: https://github.com/GoobyCorp/Xbox-360-Crypto/blob/master/xval.py