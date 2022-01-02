# KeePass. URL Overrides


[WINDOWS]

### SSH
--------------------------
- SCHEME NAME: `ssh`
- COMMAND [APPDIR]: 
```cmd
cmd://"{APPDIR}\putty\putty.exe" -ssh {USERNAME}@{URL:RMVSCM} -P {T-REPLACE-RX:/{URL:PORT}/^-1$/22/} -pw "{PASSWORD}"
```
- COMMAND [DEFULT]: 
```cmd
cmd://"{ENV_PROGRAMFILES_X86}\PuTTY\putty.exe" -ssh "{USERNAME}@{URL:HOST}" -P {URL:PORT} -pw "{PASSWORD}"
```


### RDP MSTSC
--------------------------
- SCHEME NAME: `rdp`
- COMMAND [DEFULT]: 
```cmd
cmd://cmd /c "cmdkey /generic:TERMSRV/{URL:HOST} /user:{USERNAME} /pass:{PASSWORD} && mstsc /v:{BASE:RMVSCM} && cmdkey /delete:TERMSRV/{URL:HOST}"
```



### VNC
--------------------------

### RealVNC
- SCHEME NAME: `vnc`
- COMMAND [APPDIR]: 
```cmd
cmd://java -jar "{APPDIR}\vnc\tightvnc-jviewer.jar" -user="{USERNAME}" -password="{PASSWORD}" {BASE:RMVSCM}
```
- COMMAND [DEFULT]: 
```cmd
cmd://java -jar "{ENV_PROGRAMFILES}\tightvnc-jviewer.jar" -user="{USERNAME}" -password="{PASSWORD}" {BASE:RMVSCM}
```
Сохраните tightvnc-jviewer.jar в .\vnc\tightvnc-jviewer.jar.



### SAMBA [Explorer]
--------------------------
- SCHEME NAME: `smb`
- COMMAND [DEFULT]: 
```cmd
cmd://cmd /c "net use "{BASE:RMVSCM}" /user:"{USERNAME}" "{PASSWORD}" && start \\{BASE:RMVSCM}"
```


### FTP [FileZilla FTP Client]
--------------------------
- SCHEME NAME: `ftp`
- COMMAND [APPDIR]: 
```cmd
cmd://"{APPDIR}\FileZilla\filezilla.exe" 'ftp://{USERNAME}:{PASSWORD}@{BASE:RMVSCM}'
```
- COMMAND [DEFULT]: 
```cmd
cmd://"{ENV_PROGRAMFILES_X86}\FileZilla FTP Client\filezilla.exe" 'ftp://{USERNAME}:{PASSWORD}@{BASE:RMVSCM}'
```



### FTP [Windows Explorer]
--------------------------
SCHEME NAME: `ftp`
- COMMAND [DEFULT]: 
```cmd
cmd://"explorer.exe" 'ftp://{USERNAME}:{PASSWORD}@{BASE:RMVSCM}'
```



### TeamViewer
--------------------------
- SCHEME NAME: `teamviewer`
- COMMAND [DEFULT]: 
```cmd
cmd://"{ENV_PROGRAMFILES_X86}\TeamViewer\TeamViewer.exe" -i "{USERNAME}" --Password "{PASSWORD}"
```
- COMMAND [APPDIR]: 
```cmd
cmd://"{APPDIR}\TeamViewer\TeamViewer.exe" -i "{USERNAME}" --Password "{PASSWORD}"
```



### Winbox
--------------------------

SCHEME NAME: `winbox`
- COMMAND [APPDIR]: 
```cmd
cmd://{APPDIR}\winbox\winbox.exe '{BASE:RMVSCM}' '{USERNAME}' '{PASSWORD}'
```
Сохраните winbox.exe в .\Winbox\winbox.exe.



### VSphere Client [VpxClient]
--------------------------
- SCHEME NAME: `vpx`
- COMMAND [DEFULT]: 
```cmd
cmd://"{ENV_PROGRAMFILES_X86}\VMware\Infrastructure\Virtual Infrastructure Client\Launcher\VpxClient.exe" -i -s {URL:RMVSCM} -u {USERNAME} -p {PASSWORD}`
```



### Cisco [PuTTY]
--------------------------
- SCHEME NAME: `cisco`
- COMMAND [APPDIR]: 
```cmd
cmd://{APPDIR}\scriptsdir\Connector_Cisco.vbs "{S:lan}" "{USERNAME}" "{PASSWORD}" "{S:enable}"
```
> Так же скачиваем сам [Connector_Cisco.vbs](https://raw.githubusercontent.com/numbnet/KeePass/master/UrlOverrides/lib/Connector_Cisco.vbs)
> И сохраняем его по пути: ``.\cisco\Connector_Cisco.vbs``

