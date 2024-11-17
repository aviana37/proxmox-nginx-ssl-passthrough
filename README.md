# Proxmox: Nginx SSL Passthrough
Configuration files for running Proxmox behind an Nginx reverse proxy. Connections via http are automatically redirected to https and handled by Proxmox.

## Requirements
+ Working Proxmox instance with GUI accessible through local port 8006 via https
+ Nginx version greater than 1.22.1
+ Nginx stream module enabled. If your missing it, you can install it with the following:
```bash
apt install libnginx-mod-stream
systemctl restart nginx
```


## Instructions
Include [pve-stream](pve-stream.conf) and [pve-site](pve-site.conf) in their respective stream and http blocks in the file ```/etc/nginx/nginx.conf```

```nginx
# Concise /etc/nginx/nginx.conf example

stream {
  include /etc/nginx/path/to/pve-stream.conf;
}

http {
  include /etc/nginx/path/to/pve-site.conf;
}
```

