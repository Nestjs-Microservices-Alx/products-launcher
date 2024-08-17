## Dev

1. Clonar el repositorio
2. Crear un .env basado en el .env.template
3. Ejecutar el comando `git submodule update --init --recursive` para reconstruir los sub-módulos
4. Ejecutar el comando `docker compose up --build`


### Pasos para crear los Git Submodules

1. Crear un nuevo repositorio en GitHub
2. Clonar el repositorio en la máquina local
3. Añadir el submodule, donde `repository_url` es la url del repositorio y `directory_name` es el nombre de la carpeta donde quieres que se guarde el sub-módulo (no debe de existir en el proyecto)
```sh
git submodule add <repository_url> <directory_name>
```
4. Añadir los cambios al repositorio (git add, git commit, git push)
Ej:
```sh
git add .
git commit -m "Add submodule"
git push
```
5. Inicializar y actualizar Sub-módulos, cuando alguien `clona el repositorio por primera vez`, debe de ejecutar el siguiente comando para inicializar y actualizar los sub-módulos
```sh
git submodule update --init --recursive
```
6. Para actualizar las referencias de los sub-módulos
```sh
git submodule update --remote
```


## Importante
Si se trabaja en el repositorio que tiene los sub-módulos, **primero actualizar y hacer push** en el `sub-modulo` y **después** en el repositorio principal (launcher).

Si se hace al revés, se perderán las referencias de los sub-módulos en el repositorio principal y tendremos que resolver conflictos.

Pasos:
- --- Haces cambios dentro del repo del micro
  - -- Haces commit y lo pusheas
  - -- Al final, actualizas el launcher
    - Visual con VSCode, se tiene q ver el q tiene el mismo name del submodulo, si el commit al q va a actualizar coincide con el ultimo commit del microservice q se subio, estamos bien y ya solo hacemos commit
    - Si no aparece el ultimo commit: `git submodule update --remote`



# Prod

1. Clonar el repositorio
2. Crear un .env basado en el .env.template
3. Ejecutar el comando
```sh
docker compose -f docker-compose.prod.yml build
```