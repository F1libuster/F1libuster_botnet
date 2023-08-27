# how to use it?

Run a botnet.exe and build your build.




# Capabilities

+Perform DDoS Attack:

The malware is capable of performing DDoS attacks using several vectors:

DNS Amplification
TCP (SYN) Flood
UDP Flood
HTTP Flood

![Image alt](https://github.com/F1libuster/F1libuster-botnet/blob/main/botnet.png)

# Malware Behavior

The F1libuster-botnet malware has a quick and silent installation with almost no changes on the infected machine. To ensure persistence on the infected machine it will either create a new key under the registry path “RunOnce” or create a new service on the system:

+HKCU\Software\Microsoft\Windows\CurrentVersion\RunOnce\Registry Driver

+HKLM\System\CurrentControlSet\Services\Icon Codec Service\

# Proxy

The F1libuster-botnet malware can turn the infected machine to a SOCKS/HTTP proxy to route traffic through the infected machine to a remote server.

# Communication

When the F1libuster-botnet malware executes, it will generate an HTTP GET request to “/activation.php?key=” with a unique User-Agent string “2zAz.” The server will then respond with a “Fake 404 Not Found” message if there are no commands to execute on the infected machine.

![Image alt](https://github.com/F1libuster/F1libuster-botnet/blob/main/botnet2.png)

# Communication Obfuscation Example

The GET request param value is base64 encrypted.

![Image alt](https://github.com/F1libuster/F1libuster-botnet/blob/main/botnet3.jpg)

The final readable string contains infected machine information as well as user information. When a new command is sent from the server “200 OK,” a response return is executed with the request to download a file from the server or execute a DDoS attack (see Figure below).

# Evasion

When the F1libuster-botnet malware executes it will perform several anti-virtual machine checks:

VMware:
i) Dbghelp.dll
ii) Software\Microsoft\ProductId != 76487-644-3177037-23510
Vbox:
i) VBoxService.exe
ii) VBoxHook.dll
Sandboxie
i) SbieDll.dll
It will also look for the Syser kernel debugger presence searching for the following devices:

\\.\Syser
\\.\SyserDbgMsg
\\.\SyserBoot

![Image alt](https://github.com/F1libuster/F1libuster-botnet/blob/main/botnet4.jpg)

