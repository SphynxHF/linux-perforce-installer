# Perforce Server Installer (Ubuntu 64-bit)

This script installs **Perforce Server 2015.1** on a 64-bit Linux host.  
It has been tested on **Ubuntu-based** systems.

If you need a host, I recommend the $20/month tier at [DigitalOcean](https://www.digitalocean.com/?refcode=070b959bc226).

---

## 🚀 Usage

Open a terminal on your Ubuntu server and run:

```bash
wget https://raw.githubusercontent.com/Allar/linux-perforce-installer/master/install-perforce
chmod +x install-perforce
./install-perforce
```

> ✅ No need to clone the repository — the script handles everything.

### During installation:
- A new **Linux system user** named `perforce` will be created.
- You'll be prompted to set a password for this user.
- This is **not** a Perforce account — it is only used to run the server process.

Once complete, reboot manually to ensure everything loads properly.

---

## 🔐 Security

By default, Perforce allows anyone to connect and create user accounts.  
To disable this and require manual account creation:

```bash
p4 configure set dm.user.noautocreate=2
```

This must be run **after** creating your first user with admin privileges.

---

## 📁 File Structure

- Depot files: `/perforce_depot`
- Logs: `/var/log/perforce`
- Binary location: `/usr/local/bin/p4d`
- Init script: `/etc/init.d/p4dservice`

---

## ⚙️ System Details

- The script installs `daemon` (if not already present).
- The Perforce server runs as a service via an `init.d` script.
- Compatible with Ubuntu 18.04–22.04.  
  For modern `systemd` support, open an issue or request a conversion.

---

## 🧰 Troubleshooting

- Check logs: `/var/log/perforce/`
- Is `p4d` running? Run:  
  ```bash
  ps aux | grep p4d
  ```
- Manually start service if needed:  
  ```bash
  sudo service p4dservice start
  ```

---

## 🛠 Contributing

PRs welcome to improve version targeting, Systemd compatibility, or UX!

---

## 📜 License

MIT — feel free to use and modify.
