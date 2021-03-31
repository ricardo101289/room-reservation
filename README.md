# room-reservation
Para el problema de reserva de habitaciones de  hotel se ha creado un archivo json
el cual contiene información sobre los 3 hoteles mencionados en el documento hotel_reservation-2, este archivo nos servira para simular estos 3 hoteles y maquetar una
pagina web acorde a las indicaciones para la solución.

ParteTécnica:
    * Front Vue.js 3
Vue:
    * @vue/cli 4.5.11
Node:
    * v12.11.1

Componentes:

La solución se ha dividido en varios componentes comunicados entre si para asegurar
que la información se actualice correctamente:

Componente Home: Obtiene la información de los hoteles contenida en el archivo "Hotels.json" ubicado en la ruta "assets/json". A su vez invoca dos nuevos componentes "Menu"y "Card". De el componente Menu recibirá información sobre la fecha en de la reserva y si el usuario toma un precio de recompensas. en el componente card envía la información sobre el hotel, el día y si el preció es de recompensas.

Componente Menu: El componente menú emite eventos al componente Home para indicarle que se realizo un cambio en la fecha o si se activo las recomienzas.

Componente Card: El componente card renderiza la tarjeta del hotel con la información recibida desde el componente home este componente sera invocado de la cantidad de hoteles que existan en el caso del ejemplo existen 3 hoteles.
## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
