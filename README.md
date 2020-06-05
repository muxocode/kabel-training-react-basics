# kabel-training-react-basics

Curso de iniciación de REACT para KABEL

## 0. Requisitos iniciales

Este curso, como ya supones, es enteramente FRONT-END, por lo que vamos a necesitar las siguientes herramientas/frameworks:

### 0.1. Node

Dirigete a la siguiente url <https://nodejs.org> y descárgate la verisón recomended
![Node](imgs/node.png)

Para comprobar que se ha instado puede ejecutar lo siguiente

```powershell
node -v
```

Debe saliir la misma versión que acabas de instalarte

![Node2](imgs/node2.png)

### 0.2. npm

Con la instalación de Node debería ser suficiente, pero para comprobar que todo está listo ejecuta el siguiente comando

```powershell
npm -v
```

![Npm1](imgs/npm1.png)

### 0.3 Visual Studio Code

Se puede utilizar diferentes entornos de desarrollo, pero en este caso y para este curso utilizaremos Visual Studio Code, que se puede descargar de <https://code.visualstudio.com>
![V S](imgs/VS.png)

### 0.4 Prueba final

Vamos a crear un prpyecto de ejemplo de tal manera que comprobemos que todo está bien instalado.

Escoge una carpeta y ejecuta lo siguiente sobre la misma

```shell
npx create-react-app mydemo
```

![Npx2](imgs/npx2.png)

Una vez haya instalado todas las dependencias del proyecto nos metemos en la carpeta recien creada "mydemo"
Dentro de esa misma carpeta ejecutamos los siguiente

```shell
npm start
```

![Npx3](imgs/npx3.png)

Se nos abrirá de forma automática una ventana en nuestro navegador por defecto http://localhost:3000/ (en caso contrario podemos abrirlo nosotros)

![Npx](imgs/npx.png)

YA ESTAMOS PREPARADOS PARA EMPEZAR EL CURSO

## 1. Qué es REACT

React es una librería Javascript de interfaz de usuario, desarrollada por Facebook. Esta librería se basa en el paradigma de programación orientada a componentes. Esta librería nos permitirá realizar componentes reutilizables que se pueden combinar para crear componentes de un nivel superior, hasta conformar una web. Lo que permite desarrollar interfaces de usuario de una forma más escalable que simplemente con HTML, CSS y Javascript cada uno por su lado.

React se ha hecho inmensamente popular debido a: facilidad para el desarrollo,  rendimiento y flexibilidad. Además, ha surgido todo un ecosistema de librerías que enriquecen el entorno de React, como por ejemplo Redux, lo que hacen la elección de React una gran alternativa para el desarrollo de frontales web modernos.

### 1.1 Arquitectura basada en componentes

React se basa en el paradigma de programación orientada a componentes, ¿qué es esto? Este paradigma se basa en la modularización, buscando piezas de software reutilizables y que permitan la composición. Es decir, se busca dividir la interfaz de usuario en pequeñas "piezas" denominadas componentes, que combinadas crearán componentes mayores hasta conseguir la interfaz deseada.

![Components](imgs/thinking-in-react-components.png)

Todo ello hace que deba afrontarse el desarrollo de la interfaz con un enfoque de abajo hacia arriba. Comenzando por la identificación de los componentes más pequeños y acabando a nivel de página o pantalla. Con ello se obtienen además las siguientes ventajas:

* **Desarrollo más específico**: comenzar con componentes más pequeños permite centrarse en la funcionalidad específica que debe realizar.
* **Feedback más efectivo**: es más sencillo identificar los cambios y permite realizar una comunicación más eficiente.
* **Librerías de componentes**: la reutilización de componentes facilita la creación de librerías de componentes.
* **Trabajo en paralelo**: varios miembros del equipo pueden trabajar sobre la misma página de forma más eficiente, puesto que cada miembro puede centrarse en unos componentes sin pisar los componentes de otro.
* **Tests visuales**: se pueden crear exploradores de componentes que permitan ver cada componente y con los que se pueden conseguir automatizar test visuales del estilo de los componentes.

### 1.2 Crear una nueva aplicación

Para facilitarnos la tarea de comenzar una aplicación desde cero, Facebook nos proporciona un boilerplate con todo lo necesario para trabajar con React, permitiendonos incluso configurar aspectos como el uso de typescript en la aplicación.

Podemos ejecutar la creación de la aplicación de la siguiente forma:

```shell
npx create-react-app mydemo
```

o

```shell
npm init react-app my-app
```

Incluso si lo deseamos, con yarn:

```shell
yarn create react-app my-app
```

#### 1.2.1 Partes de la aplicación

Si el comando se ha ejecutado correctamente, en el directorio sobre el que se lanza el comando, se creará un directorio my-app con la siguiente estructura:

```bash
my-app
├── README.md
├── node_modules
├── package.json
├── .gitignore
├── public
│   ├── favicon.ico
│   ├── index.html
│   ├── logo192.png
│   ├── logo512.png
│   ├── manifest.json
│   └── robots.txt
└── src
    ├── App.css
    ├── App.js
    ├── App.test.js
    ├── index.css
    ├── index.js
    ├── logo.svg
    └── serviceWorker.js
```

Las diferentes partes que podemos encontrar son:

* readme.md: Archivo markdown con la descripción de los comandos disponibles.
* node_modules: Carpeta en la que se instalan todos los paquetes de los que depende la solución.
* package.json: Archivo de configuración de npm, en él se encuentra listadas las depencias y definidos los scripts de npm disponibles.
* public: en esta carpeta encontraremos ficheros que se publicaran con la aplicación. Por ejemplo, si la aplicación corre en localhost:3000, podremos encontrar <http://localhost:3000/robots.txt> el fichero que se encuentra en la carpeta public.
* src: este será el directorio en el que nos encontremos el código de la aplicación. Aunque en este boilerplate está todo en la raíz de src, lo más común es tener diferentes directorios para organizarlo, por ejemplo: directorio styes, directorio components.

### 1.3 Componentes

Los componentes, como ya se ha visto, son la piedra angular en torno a la que gira todo. No hay React sin componentes.

#### 1.3.1 Qué es un componente

Formalmente, ya se ha dado una definición de componente, son piezas de la interfaz de usuario con las características de ser independientes, reutilizables, combinables y aisladas. Sin embargo, qué es un componente cuando hablamos de React.

React ha simplificado mucho los componentes, estos pasan a ser funciones que aceptan unas entradas (denominadas props) y que devuelven unos elementos que describen qué es lo que debe mostrarse en pantalla.

Veamos un componente React muy sencillo:

```jsx
function Welcome() {
  return <h1>Hello, World!</h1>;
}
```

Como vemos, tenemos una función "Welcome", es decir, el componente Welcome, el cuál indica que debe mostrarse en pantalla una etiqueta H1 con el texto "Hello, World!".

Podemos complicar este componente un poco más para que cambie en base a una entrada en la función, sin entrar en detalles del paso de parámetros que se abordan en el punto 2.

```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}!</h1>;
}
```

Este componente estará renderizando una etiqueta H1 con un mensaje que variará en función de la entrada.

Los componentes, además de etiquetas y elementos de HTML, pueden representar otros componentes de React:

```jsx
function WelcomeFernando() {
  return <Welcome name="Fernando" />;
}
```

o

```jsx
const WelcomeFernando = <Welcome name="Fernando" />;
```

El componente WelcomeFernando está mostrando el componente Welcome de forma concreta, pasándole como name el string "Fernando".

#### 1.3.2 css + className

Si deseamos aplicar estilos en nuestros componentes o elementos de HTML, naturalmente nos sale escribir `class="cssClassName"`. Sin embargo, esto no ocurre en React, si utilizamos esto obtendremos un error.

La forma correcta de utilizarlo será la siguiente `className="cssClassName"`

```jsx
const element = <div className="div-styled" />;
```

Además, podemos incorporar archivos CSS con estilo a nuestros componentes. Es decir, podemos tener un archivo con las clases CSS necesarias e importarlo en el componente que se utilicen.

```jsx
import React from 'react';
import 'header.css'

function CustomHeader() {
    return (
        <header className="custom-header-style">
            <p>Custom header!</p>
        </header>
    );
}

export default CustomHeader;
```

De esta forma, estamos diciendo que este componente tiene una dependencia con "header.css".

#### 1.3.3 style

> **_IMPORTANTE:_**  El atributo **style** no se recomienda como medio para estilizar elementos, es mejor el uso de `className`. El atributo **style** se suele utilizar para añadir estilos calculados dinamicamente durante el tiempo de ejecución.

Los elementos DOM disponen de una propiedad `style` que permite la introducción de estilo. Esta forma de estilizar elementos es consistente con la propiedad `style` de cualquier elemento HTML, sin embargo, tiene una diferencia y es que en React la propiedad `style`admite un objeto Javascript, en estilo camelCase, en lugar de un string CSS.

```jsx
const h1Style = {
  color: 'blue',
  backgroundImage: 'url(' + imgUrl + ')',
};

function Welcome() {
  return <h1 style={h1Style}>Hello World!</h1>;
}
```

React adicionalmente añade el sufijo "px" a las propiedades numéricas que afecten a tamaños. Si se desea cambiar el tipo de unidad, el valor deberá representarse como un string con la unidad deseada.

```jsx
// Estilo resultante: '10px'
<div style={{ height: 10 }}>
  Hello World!
</div>

// Estilo resultante: '10%'
<div style={{ height: '10%' }}>
  Hello World!
</div>
```

#### 1.3.4 imágenes

Gracias a las utilidades webpack, incorporadas en el create-react-app, utilizar assets estáticos, como imagenes o fuentes, se realiza importando los ficheros como si eestos fuesen un módulo de Javascript. Al realizar la importación lo que obtenemos es un string con el path final a referenciar, ya sea en un atributo src o en un href.

```jsx
import React from 'react';
import logo from './logo.png';
console.log(logo); // /logo.84287d09.png
function Header() {
  // Import result is the URL of your image
  return <img src={logo} alt="Logo" />;
}
export default Header;
```

Además, en el create-react-app, tenemos una utilidad adicional que nos permite reducir el número de peticiones de imágenes al servidor. Para ello, todas las imagenes (bmp, gif, jpg, jpeg y png) menores de 10.000 bytes (por defecto) se convierten a formato [data URI](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Data_URIs).

Este efecto también funciona en CSS con las rutas relativas (las que empiezan por ./).

```css
.Logo {
  background-image: url(./logo.png);
}
```

### 1.4 Código en react

Con lo que se ha visto hasta ahora, se puede apreciar la curiosa sintaxis que tiene React. Se pueden apreciar etiquetas HTML (h1, por ejemplo) y también se puede ver código javascript (declaración de funciones). Esta sintaxis se denomina JSX y es una extensión de la sintaxis de Javascript para el renderizado de plantillas. A diferencia de otros frameworks y librerías que extienden el html con funcionalidad para el renderizado de plantillas, React lo hace al contrario, haciendo que no sea necesarío aprender nuevas funcionalidades y aportando toda la potencia de Javascript a nuestras plantillas.

JSX acopla ligeramente unidades que hasta ahora se encontraban separada (js y html), sin embargo se centra en la separación de interes lógicos. Haciendo componentes más específicos y más fácilmente mantenibles.

> **_IMPORTANTE:_** Debido a que JSX es una extensión de Javascript, la convención de nomenclatura es camelCase en los atributos HTML. Por ejemplo, `tabindex` pasa a ser `tabIndex`.

#### 1.4.1 Expresiones en JSX

La sintaxis JSX permite incorporar expresiones de Javascript si estas van entre llaves. Dentro de las llaves puede ir cualquier expresión, una suma, una variable o una llamada a una función.

```jsx
function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}

const user = {
  firstName: 'Harper',
  lastName: 'Perez'
};

const element = (
  <h1>
    Hello, {formatName(user)}!
  </h1>
);
```

Además, JSX es también una expresión por sí misma. Por lo tanto podremos utilizar expresiones de control (if, for, while), pueden asignarse a variables, pueden ser argumentos de otro función y pueden retornarse desde funciones.

```jsx
function GetGreeting(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;
  }
  return <h1>Hello, Stranger.</h1>;
}

function MyCustomList(props) {
  const contentList = props.contentList;
  return (
    <ul>{contentList.map(content => <li>{content}</li>)}<ul>
  );
}
```

### 1.5 Ejercicio1

## 2. Repetción de componentes

### 2.1 KEY

### 2.2 Paso de parámetros

#### 2.2.1 Parámetros del DOM

#### 2.2.2 Parámetros de componentes CUSTOM

#### 2.2.3 Componentes anidados (children)

#### 2.2.4 Parámetros opcionales y valor por defecto

### 2.3 Eventos

### 2.4 Ejercicio 2

## 3. State vs Props

### 3.1 El peligro de usar el state

### 3.2 Ejercicio 3

## 4. Routing

### 4.1 Montar el router

### 4.2 Cómo navegar

### 4.3 Paso de parámetros

### 4.4 RouterComponentProps

## 5. Ajax en react

## 6. Formularios en react

### 6.1 one-way-binding

### 6.2 Ejercicio 4

## 7. Propuesta final

## Refs

* TypeScript
* <https://es.reactjs.org/docs/thinking-in-react.html>
* Cómo meter librerías de terceros
