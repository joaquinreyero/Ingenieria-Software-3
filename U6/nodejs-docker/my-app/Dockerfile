# Etapa de construcción (build)
FROM node:13.12.0-alpine as build

WORKDIR /app

# Copiar archivos de configuración del proyecto y archivo package.json
COPY package*.json ./

# Instalar las dependencias
RUN npm install

# Copiar el resto de los archivos de la aplicación
COPY . .

# Etapa de producción
FROM node:13.12.0-alpine

WORKDIR /app

# Copiar los archivos y las dependencias de la etapa de construcción
COPY --from=build /app .

# Exponer el puerto 3000
EXPOSE 3000

# Comando para iniciar la aplicación
CMD [ "npm", "start" ]
