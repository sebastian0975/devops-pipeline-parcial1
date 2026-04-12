# Evaluación Parcial N°1 – Ingeniería DevOps

**Encargo:** Tu primer pipeline de despliegue  
**Integrante:** Sebastian Gonzalez  
**Asignatura:** DOY0101 Ingeniería DevOps  

---

## 1. Estrategia de Ramificación

Para este trabajo se utilizó el modelo **GitFlow**.

Ramas usadas:

- `main`
- `develop`
- `feature/<nombre>`
- `hotfix/<nombre>`

Se eligió GitFlow porque permite separar lo que está en desarrollo de lo que ya está listo, y así trabajar de forma más ordenada.

También existen otros modelos como GitHub Flow o trunk-based, pero GitFlow es más claro para este tipo de trabajo.

---

## 2. Flujo de Trabajo Colaborativo

Se simuló un trabajo colaborativo usando Git.

Pasos realizados:

```bash
git clone <url>
git checkout -b feature/login
git add .
git commit -m "feat: agregar login"
git push origin feature/login
```

Después se crea un pull request hacia `develop` y se hace el merge.

Para el hotfix:

```bash
git checkout -b hotfix/bug-login
git add .
git commit -m "fix: corregir error login"
git push origin hotfix/bug-login
```

Luego se hace pull request hacia `main`.

Cambios realizados:

- 2 features (`login`, `registro`)
- 1 hotfix (`bug-login`)

---

## 3. Flujo DevOps Inicial

Se configuró un flujo simple:

- Push a `develop` → se ejecuta el pipeline  
- Pull request a `main` → se valida antes de hacer merge  

Esto sirve para revisar cambios antes de dejarlos en la versión final.

---

## 4. Herramientas de Automatización (CI/CD)

Se utilizó GitHub Actions para crear un pipeline básico.

```yaml
name: CI Pipeline
on:
  push:
    branches: [develop]
  pull_request:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Validación
        run: echo "Pipeline ejecutado"
```

Esto permite que cada cambio se ejecute automáticamente.

---

## 5. Buenas prácticas

Naming de ramas:

- feature/login  
- feature/registro  
- hotfix/bug-login  

Commits:

- feat: nueva funcionalidad  
- fix: corrección de error  
- docs: cambios en documentación  
- ci: cambios en pipeline  

Ejemplos:

- feat: agregar login  
- fix: corregir error login  

Estructura del repositorio:

/src  
/docs  
/tests  
/.github/workflows  
README.md  

Flujo de trabajo:

- feature → develop  
- hotfix → main y develop  

Revisión:

- uso de pull request  
- revisar antes de hacer merge  
- validación automática  
