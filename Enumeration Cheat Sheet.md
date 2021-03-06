
# NMAP Scan

## AUTOMATED IN SCRIPT SECTION
/boot2root/script/

**Single Host TCP Scan**
```
nmap -Pn -sS --stats-every 3m --max-retries 1 --max-scan-delay 20 --defeat-rst-ratelimit -T4 -p1-65535 -oA <$IP>T <$IP>
```
**Detailed Single Host Intense TCP Port Scan**
```
nmap -T1 -Pn -nvv -sSV --version-intensity 9 -p$(cat <$IP>T.xml | grep portid | grep protocol=\"tcp\" | cut -d'"' -f4 | paste -sd "," -)  -A -oA <$IP>T_DETAILED <$IP>
```


**Hidden Scan *[Top 1000 Ports]* - IF You think some ports are not showing up**
```
nmap -sT -Pn <$IP> -vv 
```
**Hidden - All Port Scan**
```
nmap -sT -Pn <$IP> -vv  -p1-65535
```
**Fast All Ports Scan**
```
nmap -Pn -sS --stats-every 3m --max-retries 1 --max-scan-delay 20 --defeat-rst-ratelimit -T4 -p1-65535 -o fastportScan.txt <$IP>
```
**Accurate Port Scan**
```
nmap -Pn -n -sT -sV -O -vv <$IP> -p0-65535 
```
**UDP Scan *[Top 1000 Ports]***
```
nmap -Pn  -sU -p1-65535 -o udpScan.txt --max-retries 1 --max-scan-delay 20 -T4 <$IP>
```

**UNICORN UDP Scan**
```
unicornscan -i tap0 -I -mU $IP:a
```
**UNICORN TCP Scan**
```
unicornscan -i tap0 -I -mT $IP:a
```


# HTTP Web Scans

#### NIKTO
#### DIRBUSTER
```
  /usr/share/dirbuster/wordlists/directory-list-2.3-small.txt
  /usr/share/wordlists/dirb/common.txt
  /usr/share/seclists/Discovery/Web_Content/big.txt
```

# SMB Scans

#### ENUM4LINUX
#### SMBCLIENT
```
smbclient -L <IPADDRESS> -N
```
##### Accessing Shares
```
smbclient //<IPADDRESS>/wwwroot/ -I <IPADDRESS -N
```

# FTP 

#### Anonymous Login
```
    user: anonymous
    pass: anon@anon
```
# NMAP NSE Scripts

```
nmap --script vuln <IPADDRESS> -p <PORT>
nmap --script default <IPADDRESS> -p <PORT>
nmap --script auth <IPADDRESS> -p <PORT>
```
