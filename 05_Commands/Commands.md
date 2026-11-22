## DNS and network checks
resolvectl status                      Show which DNS server the machine uses
nslookup google.com 10.20.20.1         Ask a specific DNS server for a name
ip a                                   Show IP addresses
ping -c 3 <ip>                         Send 3 ping requests

## Port and web tests
nc -zv -w 3 <ip> <port>                Test a TCP port (3 second timeout)
curl -sI https://google.com | head -1  Fetch headers, show first line

## Remote access
ssh labadmain@10.20.20.10              Log in to the server (no space before @)

## Network config
sudo cat /etc/netplan/00-installer-config.yaml
sudo nano /etc/netplan/00-installer-config.yaml
sudo netplan apply

## Services and packages
systemctl status ssh
sudo systemctl enable --now ssh
sudo apt update
sudo apt install -y curl
