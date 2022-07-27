# smart-com-vue

A simple demo/showcase application built using Vue, TypeScript,
Bootstrap and native Drag and Drop APIs

## Project Setup - Local/Dev environment

Use commands below to install dependencies, build and run application for
development purposes.

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Type-Check, Compile and Minify for Production

```sh
npm run build
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```

## Project setup - Docker
Run the commands below to build and run production ready Docker container.
Use ```sudo``` if necessary. 

### Build the container
```sh
docker build -t smart-com-vue .
```

### Run the container
```sh
docker run -p 8080:80 smart-com-vue
```

Application will be running on [local port 8080](http://localhost:8080)