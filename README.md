
## Manual para Gestionar Múltiples Cuentas de GitHub con SSH

### Introducción

En este manual, aprenderás cómo gestionar múltiples cuentas de GitHub en un mismo equipo utilizando SSH y cómo realizar commits firmados por diferentes usuarios en repositorios separados.

### Requisitos Previos

Asegúrate de tener lo siguiente:

- Acceso a dos cuentas de GitHub (una personal y otra de trabajo).
- Git instalado en tu equipo.
- Conocimiento básico de la línea de comandos.

### Paso 1: Generar Claves SSH

#### 1.1 Generar Claves SSH para la Cuenta Personal

```shell
ssh-keygen -t rsa -C "tu_email_personal@gmail.com" -f ~/.ssh/id_rsa_personal
```

#### 1.2 Generar Claves SSH para la Cuenta de Trabajo

```shell
ssh-keygen -t rsa -C "tu_email_trabajo@empresa.com" -f ~/.ssh/id_rsa_trabajo
```

### Paso 2: Iniciar el Agente SSH

```shell
eval "$(ssh-agent -s)"
```

### Paso 3: Agregar las Claves al Agente SSH

#### 3.1 Clave Personal

```shell
ssh-add ~/.ssh/id_rsa_personal
```

#### 3.2 Clave de Trabajo

```shell
ssh-add ~/.ssh/id_rsa_trabajo
```

### Paso 4: Agregar las Claves Públicas a GitHub

- Para la Cuenta Personal:
  - Copia el contenido de `~/.ssh/id_rsa_personal.pub`.
  - En GitHub, ve a Configuración > SSH y GPG keys > New SSH key y pega la clave.

- Para la Cuenta de Trabajo:
  - Copia el contenido de `~/.ssh/id_rsa_trabajo.pub`.
  - En GitHub, ve a Configuración > SSH y GPG keys > New SSH key y pega la clave.

### Paso 5: Configurar los Repositorios

#### 5.1 Clonar Repositorio Personal

```shell
git clone git@github.com:TU_USUARIO_PERSONAL/REPO_PERSONAL.git
```

#### 5.2 Clonar Repositorio de Trabajo

```shell
git clone git@github.com:TU_USUARIO_TRABAJO/REPO_TRABAJO.git
```

### Paso 6: Configurar el Usuario para los Commits

#### 6.1 Para el Repositorio Personal

```shell
cd REPO_PERSONAL
git config user.email "tu_email_personal@gmail.com"
git config user.name "Tu Nombre Personal"
```

#### 6.2 Para el Repositorio de Trabajo

```shell
cd REPO_TRABAJO
git config user.email "tu_email_trabajo@empresa.com"
git config user.name "Tu Nombre de Trabajo"
```

### Paso 7: Realizar Commits y Push

Realiza tus cambios en cada repositorio y realiza los commits correspondientes. Los commits se firmarán automáticamente con los usuarios configurados en cada repositorio.

### Conclusiones

En este manual, has aprendido a gestionar múltiples cuentas de GitHub con SSH y a realizar commits firmados por diferentes usuarios en repositorios separados. Este enfoque te permitirá mantener tus proyectos personales y de trabajo de manera organizada y segura.

