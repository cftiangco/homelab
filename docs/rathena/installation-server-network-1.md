# Server Network Configuration

### Configure the connection and point to the server IP

Modify all fields and match with your server IP/LAN IP

- /conf/char_athena.conf
  - userid: ragnarok
  - passwd: ragnarok
  - server_name: YourRO_name
  - login_ip: LAN IP/Internal IP
  - bind_ip: LAN IP/Internal IP
  - char_ip: **WAN IP/External IP**
- /conf/login_athena.conf
  - bind_ip: LAN IP/Internal IP
  - login_port: 6900
- /conf/map_athena.conf
  - char_ip: LAN IP/Internal IP
  - bind_ip: LAN IP/Internal IP
  - userid: ragnarok
  - passwrd: ragnarok
- /conf/subnet_athena
  - subnet: 255.0.0.0:[LAN IP/Internal]:[LAN IP/Internal]

### Enable Port
Make sure all ports are exposed: 5121, 6121 and 6900.

```sh
# Install the ufw for firewall configuration
sudo apt-get install ufw

# Allow the SSH (required)
sudo ufw allow ssh

# Allow ports required by rAthena 
sudo ufw allow 5121
sudo ufw allow 6121
sudo ufw allow 6900
```