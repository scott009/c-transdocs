# RemoteServers


Installed the openssh server
ssh keys in stored for ssh from cursorai  
##  DNS  
@                 A      72.60.119.218        ; TTL 5m
ic                A      72.60.26.118         ; TTL auto
inquirycircle     A      72.60.26.118         ; TTL auto
translations      A      72.60.119.218        ; TTL 5m

container1        CNAME  host.catbench.com.   ; TTL 5m
container2        CNAME  host.catbench.com.   ; TTL 5m
dev.icircle       CNAME  host.catbench.com.   ; TTL 5m
icgeneric         CNAME  host.catbench.com.   ; TTL 5m
icircle           CNAME  host.catbench.com.   ; TTL 5m
jitsi.icircle     CNAME  host.catbench.com.   ; TTL 5m
ssh               CNAME  host.catbench.com.   ; TTL 5m
trn               CNAME  translations.catbench.com. ; TTL 5m
www               CNAME  host.catbench.com.   ; TTL auto

## KVM2  
2 vCPU cores- 8 GB RAM - 100 GB NVMe disk space - 8 TB bandwidth
srv1197072.hstgr.cloud  
72.60.119.218
passwords are stored in bitwarden in the Hostinger KVM2 note

### Server locations
caddyfile location /etc/caddy/Caddyfile

### document loclations   
#### /var/www/catbench.com  
index.html   
  
#### /var/www/translations.catbench.com  
ada3.css  
submit-handler.js
RDGTranslations.html   - default file 
 - other html files including printmaster and tmaster files 



### Caddyfile   contents

```caddyfile
# Homepage
catbench.com {
        root * /var/www/catbench.com
        file_server
}

# Translations - static files
translations.catbench.com {
        root * /var/www/translations.catbench.com  
        try_files {path} /RDGTranslations.html  
        file_server
}

# Shortcut CNAME for translations
trn.catbench.com {
        root * /var/www/translations.catbench.com
        file_server
}

# Inquiry Circle - reverse proxy to Application Server
inquirycircle.catbench.com {
        reverse_proxy http://72.60.26.118:80
}

# IC - reverse proxy to Application Server
ic.catbench.com {
        reverse_proxy http://72.60.26.118:80
}  
```


## KVM4   
4 vCPU cores 16 GB RAM 200 GB NVMe disk space 16 TB bandwidth    
this is ip 72.60.26.118  
the server   is more powerful than the KVM2   
  runs Ubuntu 22.04 LTS Server  
  200 GB storage
  

