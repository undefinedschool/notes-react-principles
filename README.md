> El siguiente contenido fue elaborado por [@_nhsz](https://twitter.com/_nhsz) como guía para las clases de [undefined school](https://twitter.com/undefinedSchool)
> Son bienvenidos los _issues_ y _PRs_ para mejorar el contenido, corregir errores, etc. 

> 👉 Si te resultó útil, **se agradece que lo compartas para que le llegue a más gente!**

# ![React: Principios](https://i.imgur.com/KpuNcbY.png)

## Notas sobre React

- [**Principios**](https://github.com/undefinedschool/notes-react-principles/)
- [**Conceptos Básicos**](https://github.com/undefinedschool/notes-react-basics)

## Contenido

- [Qué problema resuelve React?](https://github.com/undefinedschool/notes-react#qu%C3%A9-problema-resuelve-react)
- [Principios](https://github.com/undefinedschool/notes-react#principios)
  - [Declarativo](https://github.com/undefinedschool/notes-react#declarativo)
  - [Arquitectura basada en _componentes_](https://github.com/undefinedschool/notes-react#arquitectura-basada-en-componentes)
    - [Componente](https://github.com/undefinedschool/notes-react#componente)
  - [Flujo de datos unidireccional (one-way data flow)](https://github.com/undefinedschool/notes-react#flujo-de-datos-unidireccional-one-way-data-flow)
  - [Virtual DOM](https://github.com/undefinedschool/notes-react#virtual-dom)
  - [Sólo se encarga de la UI](https://github.com/undefinedschool/notes-react#s%C3%B3lo-se-encarga-de-la-ui)
- [Nuestra tarea como React devs](https://github.com/undefinedschool/notes-react#nuestra-tarea-como-react-devs)

---

## Qué problema resuelve React?

Antes de empezar a hablar sobre los diferentes conceptos, siempre es útil entender un poco la motivación, por qué existe, qué problema resuelve la herramienta que elegimos. En mi opinión, este proceso resulta además muy beneficioso para entender, tanto mejor como más rápido, los conceptos fundamentales detrás de cualquier tecnología que decidamos usar.

Con los años, la complejidad de las aplicaciones web fue creciendo. Al principio, sólo teníamos archivos HTML, CSS y algo de JS para proveer un mínimo de interacción con el DOM. El código JS que escribíamos no era compatible con todos los browsers por default, por lo que había que escribir diferentes versiones. _jQuery_ surge entonces como una solución a este problema, brindando una API unificada para escribir este código una vez y de forma más simple, garantizando compatibilidad con los diferentes browsers. 

Pero la complejidad de las bases de código seguía aumentando y los programas eran cada vez más difíciles de mantener. El framework _AngularJS_ aparece en el 2010 y se posiciona rápidamente como el nuevo standard para construir SPAs (single-page applications), aportando una estructura y el uso de ciertos patrones (MVC) para organizar mejor nuestras aplicaciones.

Más aún, en aplicaciones donde acciones en diferentes partes de la UI tenían efectos sobre otras<sup id="cite_ref-1"><a href="#cite_note-1">[1]</a></sup>, los problemas seguían estando y nos encontrábamos con aplicaciones escritas en _Angular_ donde era difícil entender el _flujo de los datos_ y qué parte del código afectaba a cuál otra. 

Facebook tenía este problema muy presente, por lo que decidieron desarrollar una alternativa. [En el 2013, Facebook libera _React_](https://www.youtube.com/watch?v=GW0rj4sNH2w), _una biblioteca de JavaScript para construir interfaces de usuario_, según definen en el [sitio oficial](https://reactjs.org/). 

## Principios

### Declarativo

La manipulación del DOM es uno de los principales cuellos de botella en la performance del front-end. React decide entonces tomar un enfoque más _declarativo_ y busca evitar que el browser esté continuamente realizando operaciones costosas.

Por lo tanto, sólo vamos a encargarnos de diseñar las _vistas_ para cada _estado_ de nuestra aplicación y **React va a actualizar y renderizar de manera eficiente los componentes correctos cuando los datos cambien** (estado), haciendo cambios mínimos en el DOM. **El código declarativo es más predecible y por lo tanto, más fácil de de razonar y debuggear**.

> 👉 **La vista pasa a ser entonces una función del estado** de la aplicación, es decir, cuando el estado de la aplicación cambia, la vista se vuelve a renderizar. Por lo tanto, **si queremos que la vista (UI) sea actualice, tenemos que modificar el estado de alguna forma**.

Ya no necesitamos preocuparnos por cómo manipular el DOM o manejar eventos del mismo, React se va a encargar de abstraernos de estos detalles.

### Arquitectura basada en _componentes_

Vamos a construir interfaces de usuario (UI) utilizando _componentes reutilizables_, que poseen y manejan un _estado_ propio. Usamos estos _componentes_ como si fueran bloques de Lego, para construir componentes más complejos y eventualmente una aplicación entera.

> 👉 **Llamamos _estado_ a las características propias de un componente**. Por ejemplo, cuando tenemos un componente que hace requests a un server, puede tener dos estados posibles, pendiente o finalizado.

La lógica de los componentes se escribe en JavaScript (y no utilizando _templates_, como es el caso de otras libs/frameworks de front), por lo que podemos pasar datos (_props_) de forma simple y mantener el estado fuera del DOM.

#### Componente

> 👉 **Un componente es un _bloque de código reutilizable_, una pieza de UI con contenido, estilos y comportamiento definidos: contiene todo el HTML, CSS y JS necesario para funcionar**. 

Por ejemplo, una barra de búsqueda es un componente, porque tiene una función independiente, una botón podría también a ser un componente, porque cumple una función. Básicamente, cualquier sección de la UI puede llegar a ser un componente.

Por lo tanto, **en React, cada parte de la UI es un componente y cada componente tiene un estado**.

Si el _estado_ de nuestra aplicación indica por ejemplo, que un usuario se encuentra logueado, crearemos los componentes correspondientes basados en esa información.

> 👉 **Los componentes entonces, no dejan de ser simples funciones de JavaScript** que reciben esta información a través de diferentes parámetros a los que llamaremos _props_ (por _propiedades_) y retornan el código necesario (usando [_JSX_](https://reactjs.org/docs/introducing-jsx.html)) para renderizar los componentes. **Las props son _inmutables_ y siempre se pasan de componentes superiores a componentes inferiores**.

### Flujo de datos unidireccional (_one-way data flow_)

> 👉 En React,  **los datos tienen 1 y sólo 1 forma (o dirección) de ser transferidos hacia otras partes de la aplicación**. Esto implica que los _componentes hijos_ (child components) no pueden actualizar los datos que provienen de un _componente padre_ (parent component). 

![one-way data flow](https://image.slidesharecdn.com/wjkqukgsqgm2vger5dnt-signature-2cf736e9b897e2aaaa6315f9d31d6951ba19fae7560fe278cefb4644ac0753c6-poli-170428114140/95/ndc17-unrealjs-ue4-35-638.jpg?cb=1493434725)

**Los datos que vienen de un _componente padre_ se conocen como _props_**. 

El principal beneficio de tomar este approach, en el que los datos _fluyen_ a través de nuestra aplicación en una única dirección, es que el código resulta más fácil de razonar y debuggear, porque sabemos qué datos provienen de dónde y por lo tanto menos propenso a errores.

> 👉 Cualquier cambio que se le realice al _state_ de un componente, sólo puede afectar a los componentes que están _debajo_ (los _child components_), que van a recibirlo como _props_ de sólo lectura. 

**Como los datos se mueven en una única dirección, modificar el estado de un componente no afecta a su componentes padre o hermanos: sólo los descendientes van a ser afectados**  (un _child component_ no puede modificar el _state_ de su _parent component_). Esta es la principal razón por la que [el _state_ suele _levantarse_](https://reactjs.org/docs/lifting-state-up.html) (lo movemos "hacia arriba" en el _árbol de componentes_), de manera tal que pueda compartirse y ser accedido entre los componentes que lo necesitan.

### Virtual DOM

**Actualizar y volver a renderizar el DOM en el browser cada vez que queremos realizar un cambio en la UI tiene un gran impacto en la performance de nuestra aplicación**, porque implica realizar operaciones costosas. Al hacer cambios en el DOM, el elemento modificado y sus descendientes (children) deben volver a renderizarse para que el cambio se vea reflejado en la UI. Realizar estas operaciones continuamente ([_re-rendering_, _re-painting_, etc](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-tree-construction)) es lo que vuelven lenta y poco eficiente a esta forma de trabajar.

React propone utilizar una alternativa, el _Virtual DOM_.

> 👉 **El [_Virtual DOM_](https://programmingwithmosh.com/react/react-virtual-dom-explained/) es una representación virtual del DOM, una "versión liviana" (un gran objeto JS) del DOM real que encontramos en el browser, que React utiliza para _mapear_ elementos del DOM real y poder realizar cambios en este de una forma mucho más rápida y eficiente**. Cada vez que el _state_ de nuestra aplicación cambia, se actualiza el _Virtual DOM_ y no el DOM real.

![React Virtual DOM](https://miro.medium.com/max/2048/1*wrh_lW6mpQHRsuGtw1FuqA.png)

> 👉 Básicamente, cada vez que agregamos nuevos elementos (componentes) a la UI, un nuevo _virtual DOM_ (representado como un árbol) es creado. Cada elemento es un _nodo_ de este árbol. React toma un _snapshot_ de los elementos de nuestra aplicación y lo carga en este árbol. Si el _state_ de alguno de estos elementos cambia, se genera un nuevo _virtual DOM_. Este DOM (virtual) es entonces comparado con el DOM (virtual) previo y se calculan las diferencias a través de un [_algoritmo de diffing_](https://medium.com/@gethylgeorge/how-virtual-dom-and-diffing-works-in-react-6fc805f9f84e). Utilizando esta información, **React calcula la forma más eficiente de realizar los cambios en el DOM real**, actualizando sólo los nodos que cambiaron, reduciendo el impacto en la _performance_ de nuestra aplicación.

Otra estrategia que utiliza React para mejorar la performance es enviar los cambios detectados en el virtual DOM por _lotes_ (batch), para luego realizar los cambios necesarios en el DOM real de una vez, en lugar de estar enviando continuamente updates al mismo por cada cambio del estado.

> 👉 **En resumen:**

> - realizar updates frecuentes del DOM (real) es costoso y tiene un gran impacto en la performance
> - el _Virtual DOM_ es una representación virtual del DOM real que React utiliza para mejorar la performance
> - cuando ocurre un cambio en el _state_, se genera un nuevo _virtual DOM_ y se compara con la versión anterior. Esto se conoce como _diffing_
> - los cambios a realizar en el DOM se envían por tandas, para actualizar la UI con menor frecuencia y por lo tanto, menor costo

### Sólo se encarga de la UI

> 👉 **React es una librería (o biblioteca) que sólo se encarga de resolver un problema: renderizar la _vista_ o UI de nuestra aplicación**. 

A diferencia de otros _frameworks_ de front-end, como Angular, Vue o Svelte, **React no es opinionado**, no asume nada sobre nuestro stack tecnológico ni sobre cómo resolver y conectar el resto de las partes; esas decisiones quedarán por nuestra cuenta. Gracias a esto, la _API_ de React resulta más concisa y simple en comparación y por lo tanto, más simple de aprender.

Además, **esta característica permite también que podamos reutilizar código React en diferentes plataformas**: por ejemplo, renderizando desde el servidor usando [Node](https://nodejs.org/) o en aplicaciones móviles, a través de [React Native](https://facebook.github.io/react-native/).

## Nuestra tarea como _React devs_

Como devs, tendremos que tomar varias decisiones relacionadas a la _arquitectura de la aplicación_, que podrían resumirse en los siguientes puntos:

- definir los **_React components_**
- definir qué datos forman parte del **_state_** y dónde (en qué componente) va a vivir
- decidir **qué cambios deben realizarse en la UI cuando el _state_ cambia**

---

<sup id="cite_note-1"><a href="#cite_ref-1">1</a></sup>Estos problemas existieron (y todavía existen) en las librerías que decidieron usar **[_2-way data binding_](https://medium.com/front-end-weekly/what-is-2-way-data-binding-44dd8082e48e) (o flujo de datos _bidireccional_)**. Es decir, los cambios en la UI afectan al objeto JS que la UI quiere representar y viceversa.
