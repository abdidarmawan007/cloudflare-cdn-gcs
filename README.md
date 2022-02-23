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

### create iam role for get object only for public (no permission list object for public users)
![alt text](https://i.imgur.com/OKTkiea.png)

### create permission bucket read only to public
![alt text](https://i.imgur.com/ff91hso.png)

### create cname record in cloudflare for gcs storage for example we create cdn.yourdomain.id
### name: cdn target: c.storage.googleapis.com
![alt text](https://i.imgur.com/V9ZkW2l.png)

### set always https
![alt text](https://i.imgur.com/eiR59Yp.png)

### set ssl/tls full
![alt text](https://i.imgur.com/GhikuKR.png)

### create pagerules for our domain static asset
![alt text](https://i.imgur.com/lzTZ4hN.png)


### remove GCS header via cf header modification
![alt text](https://i.imgur.com/S0A6BQI.png)
![alt text](https://i.imgur.com/Fc7aZhr.png)


### test our cdn
```
curl -I https://cdn.yourdomain.id/maxresdefault.jpg
```
```
HTTP/2 200 
date: Fri, 10 Jul 2020 08:51:12 GMT
content-type: image/jpeg
last-modified: Thu, 09 Jul 2020 04:26:20 GMT
etag: "4536048b5dca0206b51482cf67b66a77"
cache-control: public, max-age=31536000
age: 1290
cf-cache-status: HIT
expect-ct: max-age=604800, report-uri="https://report-uri.cloudflare.com/cdn-cgi/beacon/expect-ct"
server: cloudflare
cf-ray: 5b090aa3a898dd3e-SIN
```
### header
```
cache-control: public, max-age=31536000 = cache ttl
age: 1290 = cache age in pop cdn
cf-cache-status: HIT = cache hit from pop cdn
cf-ray: 5b0944f75b83e237-SIN = cache hit from pop cdn singapore
```
```
cloudflare cdn pop location and code name
https://www.cloudflarestatus.com/
```

### Use Cloudlfare Enterprise for Cache HIT from POP/Edge Jakarta/Indonesia
```
cf-cache-status: HIT
server: cloudflare
cf-ray: 640a0d191ff0354f-CGK
```

#### Tips
```
Use GCP Loadbalander + Public IP if you already bucket with another name (not domain name) and set A Record in Cloudflare
Set Cloudflare Browser Cache TTL 1 year
Make Code backend upload with set metadata to object " cache-control: public, max-age=31536000 "
```
