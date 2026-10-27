# Práctica 5: Ramas y conflictos en Git

**Proyecto:** WebNova
**Autor:** Miguel García

---

## 1. Preparar el proyecto

Creamos la carpeta, ponemos `main` como rama por defecto e iniciamos el repositorio.

```bash
mkdir webnova-remoto
cd webnova-remoto
git config --global init.defaultBranch main
git init
```

![Creacion del proyecto](capturas/creacion-de-directorio.png)

Dentro creamos un `equipo.md` muy simple:

```bash
- # Equipo de Desarrollo WebNova
- Project Manager: Ana Torres
```
![vista de archivo](capturas/vista_archivo.png)


Y hacemos el primer commit:

```bash
git add equipo.md
git commit -m "C1:Creación del archivo de equipo"
```

![primer add y commit](capturas/add-y%20-commit.png)

Copiamos la URL SSH del respositorio y vinculamos a nuestro terminal:

```bash
git remote add origin git@github.com:gsmiguel8webnova-remoto.git
git push -u origin main
```
![push origin](capturas/push-origin.png)


---

## 2. El compañero virtual

Vamos a simular que un compañero de trabajo actualiza el repositorio en `GitHub` mientras seguimos trabajando

```bash
- # Equipo de Desarrollo WebNova
- Project Manager: Ana Torres
- Frontend Developer: Carlos Gómez (Añadido por el compañero)
- C2: Añadido Frontend Developer"
```

---

## 3. Creacion del conflicto

Mientras nuestro compañero realzia el anterior commit desde  `GituHub` nosotros realizamos lo siguiente:


```bash
- # Equipo de Desarrollo WebNova
- Project Manager: Ana Torres
- Backend Developer: [Miguel] (Añadido en local)
- git commit -a -m "C3: Añadido Backend Developer"
- git push
```

Conflicto generado: 

![Creamos conflicto](capturas/creacion-de-conflicto.png)


| palabra | sirve | 
|------|------|
| `rejected` | Palabra para denerjar la subida |
| `hint` | Recomienda integrar actualizar cambios remotos |


---


## 4. Rescate y solución

Descubierto cual era el problema vamos a rescatar el proyecto:

```bash
git pull --rebase
```

git detiene el proceso y nos informara del conflicto en nuestro archivo `equipo.md`

![revision de conflicto en archivo](capturas/marcas-de-conflicto.png)

borramos las marcas de git:  

```bash
- # Equipo de Desarrollo WebNova
- Project Manager: Ana Torres
- Frontend Developer: Carlos Gómez (Añadido por el compañero)
- Backend Developer: [Miguel] (Añadido en local)
```


guardamos el archivo e indicamos que esta solucionado y volvemos a intentar subirlo:

```bash
git add equipo.md
git rebase --continue
```

![rescate del proyecto](capturas/rebase-y-push.png)


```bash
git push
```


Comprobamos en `Github`  esta actualizado:


![Salida de git branch con las tres ramas creadas](capturas/resultadofinal.png)





