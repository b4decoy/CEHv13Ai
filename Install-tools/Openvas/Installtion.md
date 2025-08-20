## 🔧 OpenVAS Installation (Debian 11)

# ✅ **Simplified OpenVAS Installation & Setup Guide**

---

## 🔧 Step 1: Install Required Packages

Run the following to install the dependencies:

```
sudo apt-get update sudo apt-get install -y gcc cmake pkg-config bison flex \ libglib2.0-dev libgcrypt20-dev libgpgme-dev libjson-glib-dev \ libksba-dev libpcap-dev libssh-gcrypt-dev libgnutls28-dev \ libcurl4-gnutls-dev libsnmp-dev redis-server libbsd-dev \ krb5-multidev
```


---

## 📁 Step 2: Download & Build OpenVAS

1. Clone the repository (or download source):
    
    `git clone https://github.com/greenbone/openvas.git cd openvas`
    
2. Create and enter the build directory:
    
    `mkdir build cd build`
    
3. Configure build (default install path `/usr/local`):
    
    `cmake ..`
    
4. Compile the code:
    
    `make`
    
5. Install it (may require sudo):
    
    `sudo make install`
    

---

## ⚙️ Step 3: Redis Configuration

1. Copy the Redis config for OpenVAS:
    
    `sudo cp ../config/redis-openvas.conf /etc/redis/ sudo chown redis:redis /etc/redis/redis-openvas.conf`
    
2. Set OpenVAS to use this Redis socket:
    
    `echo "db_address = /run/redis-openvas/redis.sock" | sudo tee /etc/openvas/openvas.conf`
    
3. Start Redis with the OpenVAS config:
    
    `sudo systemctl enable redis-server@openvas.service sudo systemctl start redis-server@openvas.service`
    

---

## 🔄 Step 4: Feed Synchronization (Download Vulnerability Tests)

1. Install the feed sync tool:
    
    `git clone https://github.com/greenbone/greenbone-feed-sync.git cd greenbone-feed-sync sudo make install`
    
2. Run the sync:
    
    `greenbone-feed-sync --type nvt`
    

---

## 🧪 Step 5: Test OpenVAS

Upload NVTs into Redis:

`sudo openvas -u`

Run OpenVAS:

`sudo openvas`

---

## 🔐 Step 6: Sudo Permissions for ospd-openvas

Edit sudoers file:

`sudo visudo`

Add:

`yourusername ALL = NOPASSWD: /usr/local/sbin/openvas Defaults        secure_path="...:/usr/local/sbin"`

Replace `yourusername` with your actual user name.

---

## 🧾 Log Files

Check logs here if something goes wrong:

`/var/log/gvm/openvas.log`

---

## 🚀 Next Steps

- Install and configure **`ospd-openvas`** and **`gvmd`** if you want to use the full GVM stack.
    
- Use a web interface like **GSA** (Greenbone Security Assistant) or **GVM-Tools** for management and reporting.