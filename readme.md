# SMA

## MAVEN

### Compilar el proyecto

```bash
mvn package
```

## DOCKER

### Generar la Imagen

el **tag** es el nombre de la nueva **imagen**

**"muy importante no olvidar el punto del final"**

```bash
docker build --tag sma .
```

### Correr un Container

```bash
docker run --rm sma
```

### Crear una red para los containers de SMA

```bash
docker network create --driver bridge sma-net
```

#### inspeccionar red

```bash
docker network inspect sma-net
```


### Correr un Container con nombre en la red creada

**--name** es el nombre de cada uno de los container que se generará

**--network** en nombre la de la red creada anteriormente

```bash
docker run --rm --name sma01 --network sma-net sma

docker run --rm --name sma02 --network sma-net sma

docker run --rm --name sma03 --network sma-net sma
```

#### Correr un Container con nombre en la red creada pero en backgound

**-dit** es un conjunto de opciones

**-d** corre el container en background e imprime el id

**-i** Mantiene STDIN abierto incluso si no está conectado

**-t** Asigna un pseudo tty

```bash
docker run -dit --name sma01 --network sma-net sma

docker run -dit --name sma02 --network sma-net sma

docker run -dit --name sma03 --network sma-net sma
```

#### Si corre en background es necesario asociar el container con attach

```bash
docker container attach sma02
```