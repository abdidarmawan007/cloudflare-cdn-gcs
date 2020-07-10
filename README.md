# cdn static assets cloudflare + google cloud storage

### verification your domain in here
```
https://search.google.com/search-console
```
![alt text](https://i.imgur.com/lg0wqCI.png)

### add txt domain verification to cloudflare dns
![alt text](https://i.imgur.com/aUbAVse.png)

### after domain alredy verification by google create bucket with your domain for example cdn.yourdomain.id, create bucket with single region for example in singapore
![alt text](https://i.imgur.com/pusX8XZ.png)

### create permission bucket read only to public
![alt text](https://i.imgur.com/T1gelEV.png)

### create cname record in cloudflare for gcs storage for example we create cdn.yourdomain.id, 
### name=cdn target=c.storage.googleapis.com
![alt text](https://i.imgur.com/V9ZkW2l.png)



