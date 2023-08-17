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
docker run -d -it kaliprog 
```
or
```
docker run -d -it kaliwork
```

## Attach to container
```
docker attach kaliprog
```
or
```
docker attach kaliwork
```

# ToDo
- [x] Kali Prog version 1.0. Absolutely work version.
- [] Add more easier container startup.
- [] Add more tools in kaliwork.
- [] Try to more speedup container startup, specialy for kaliwork. 
- [] May be try to do images lower disk space usage.
