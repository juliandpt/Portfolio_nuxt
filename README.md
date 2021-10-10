Portfolio personal de Julián de Pablo Torremocha. En este se detalla su educación, sus proyectos, su carrera profesional, entre otras.

## Cofiguración del entorno

### Prerequisitos:

![Node + Npm](https://clientes.hostinglabs.net/images/kb/177_nodejsnpm.png)

- Instalación de Node.js:

[Node.js](https://nodejs.org/es/download/)

- Instalación de Npm:

```sh
npm install -g npm
```

### Tecnologías:

[![Nuxt](https://miro.medium.com/max/990/1*SlAgtr2Xlb6V2kL2uVu0DA.png)](https://nuxtjs.org)

Instalación de NuxtJS:
Realizada una vez se instala npm.

[![Vuetify](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT5P6I3201Fh16-Um-nS_BNYXQumigSw1I3h_nCw7K9k54Wtbx0gJx_XlIraVD768Zj3Hc&usqp=CAU)](https://vuetifyjs.com/en/)

Instalación de Vuetify:
Durante la creación del proyecto.

[![Firebase](https://i.ytimg.com/vi/rAcWLPQIL38/maxresdefault.jpg)](https://firebase.google.com)

Instalación de Firebase:

- En el ordenador personal:

```sh
npm install -g firebase-tools
```
Nota: Realizar la descarga en una terminal de administrador.

- En el servicio online:
  > Crear proyecto en [Firebase console](https://console.firebase.google.com)

  > Habilitar las opciones necesarias (para este proyecto, solo es necesario Hosting)

### Creación del proyecto

- Elegir uno de los dos siguientes métodos:
```sh
npm init nuxt-app <project-name>
```
```sh
npx create-nuxt-app <project-name>
```

- Elegir las opciones necesarias.

### Mantenimiento del proyecto

- Comandos de NPM:
```bash
# Instalación de paquetes y dependencias
$ npm install

# Compilar con recarga automatica en localhost:3000
$ npm run dev

# Compilar para producción y servidor de lanzamiento
$ npm run build
$ npm run start

# Generar versión estatica del proyecto
$ npm run generate
```

- Comandos de Firebase:
```bash
# Instalación de firebase en el proyecto (Nota: solo hacerlo la primera vez)
$ firebase init

# Actualizar versión de la web en el dominio
$ firebase deploy
```