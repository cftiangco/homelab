# rAthena Configuration

## For Debian 10
Install all necessarry packages

```sh
# Update your server first
sudo apt-get update \
sudo apt-get upgrade
```

```sh
# Require packages
sudo apt-get install git make libmariadb-dev libmariadbclient-dev libmariadbclient-dev-compat gcc g++ zlib1g-dev libpcre3-dev

# Updated
sudo apt-get install git make libmariadb-dev libmariadb-dev libmariadbclient-dev-compat gcc g++ zlib1g-dev libpcre3-dev
```

```sh
# For editing a files, you can download vim (optional)
sudo apt-get install vim
```

```sh
# Clone the rAthena repository
git clone https://github.com/rathena/rathena.git ~/rAthena
```

### Compile the code

Configure script to make sure everything is working fine
```sh
./configure
```
To ensure caches are removed when compiling

```sh
make clean
```

Build the server code

```sh
make server
```

Optional - we may need to chmod our server file to make them **executable**
```sh
chmod a+x login-server && chmod a+x char-server && chmod a+x map-server && chmod a+x web-server
```

### Recompile the code

Recompiling the code after doing any changes 
```sh
./configure && make clean && make server
```

### Starting the server

```sh
# To Start:
./athena-start start

# To Stop:
./athena-stop stop

# To Restart:
./athena-restart
```