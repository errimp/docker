# Usage

```
docker build -t naxsi-build ./
docker run --name naxsi-build naxsi-build true
docker cp naxsi-build:/home/builder/rpmbuild/RPMS/x86_64/nginx-1.8.0-1.el6.ngx.x86_64.rpm ./
docker rm naxsi-build
docker rmi naxsi-build
```
