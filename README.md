# docker-fuck

# How To
## Build docker container
```
docker build -t kaliprog .
```
or
```
docker build -t kaliwork .
```

## Stardup container
```
docker run --name kaliprog -d -t -i kaliprog:1.0 /bin/bash
```
or
```
docker run --name kaliwork -d -t -i kaliwork:1.0 /bin/bash
```

## Attach to container
```
docker exec -it kaliprog bash
```
or
```
docker exec -it kaliwork bash
```

# ToDo
- [x] Kali Prog version 1.0. Absolutely work version.
- [ ] Add more easier container startup.
- [ ] Add more tools in kaliwork.
- [ ] Try to more speedup container startup, specialy for kaliwork. 
- [ ] May be try to do images lower disk space usage.
