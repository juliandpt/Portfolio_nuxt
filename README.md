# Julian's Portfolio

Julian's personal portfolio. It details his education, his projects, his professional career, among others.

## Built with 🛠️

- [Nuxt](https://nuxtjs.org) - The web framework used
- [Vuetify](https://vuetifyjs.com) - The UI framework used
- [Firebase](https://firebase.google.com) - The hosting service used

## Requirements 📋

*Nuxt installation:*

during the installation of [NodeJS](https://nodejs.org)

*Firebase instalation:*

>
```sh
npm install firebase-tools
```

> Crear proyecto en [Firebase console](https://console.firebase.google.com)

> Habilitar las opciones necesarias (para este proyecto, solo es necesario Hosting)

## Environment configuration ⚙️

*Project creation:*

```sh
npm init nuxt-app <project-name>
```

*Install dependencies:*

```sh
npm install
```

*Install Typescript:*

```sh
node scripts/setupTypeScript.js
```

## Deployment 📦

*Execute project in development mode:*

```bash
npm run dev
```

*Building and running in production mode:*

```bash
npm run build
npm run start
```

*Generate static version of the project:*

```bash
npm run dev
```

*Installation of firebase in the project (Note: only do it the first time):*

```bash
firebase init
```

*Update version of the web in the domain:*

```bash
firebase deploy
```