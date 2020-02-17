> El siguiente contenido fue elaborado por [@_nhsz](https://twitter.com/_nhsz) como guía para las clases de [undefined school](https://twitter.com/undefinedSchool)

> Son bienvenidos los _issues_ y _PRs_ para mejorar el contenido, corregir errores, etc. 

👉 Si te resultó útil, se agradece que lo compartas para que le llegue a más gente!

# [WIP] Notas sobre React

## Qué problema resuelve React?

Antes de empezar a hablar sobre los diferentes conceptos, siempre es útil entender un poco la motivación, por qué existe, qué problema resuelve la herramienta que elegimos. En mi opinión, este proceso resulta además muy beneficioso para entender, tanto mejor como más rápido, los conceptos fundamentales detrás de cualquier tecnología que decidamos usar.

Con los años, la complejidad de las aplicaciones web fue creciendo. Al principio, sólo teníamos archivos HTML, CSS y algo de JS para proveer un mínimo de interacción con el DOM. El código JS que escribíamos no era compatible con todos los browsers por default, por lo que había que escribir diferentes versiones. _jQuery_ surge entonces como una solución a este problema, brindando una API unificada para escribir este código una vez y de forma más simple, garantizando compatibilidad con los diferentes browsers. 

Pero la complejidad de las bases de código seguía aumentando y los programas eran cada vez más difíciles de mantener. El framework _AngularJS_ aparece en el 2010 y se posiciona rápidamente como el nuevo standard para construir SPAs (single-page applications), aportando una estructura y el uso de ciertos patrones (MVC) para organizar mejor nuestras aplicaciones.

Pero en aplicaciones donde acciones en diferentes partes de la UI tenían efectos sobre otras, los problemas seguían estando y nos encontrábamos con aplicaciones de _Angular_ donde era difícil entender el _flujo de los datos_ y qué parte del código afectaba a cuál otra. 

Facebook tenía este problema presente en sus aplicaciones, por lo que decidieron desarrollar una alternativa. [En el 2013, Facebook libera _React_](https://www.youtube.com/watch?v=GW0rj4sNH2w), _una biblioteca de JavaScript para construir interfaces de usuario_, según definen en el [sitio oficial](https://reactjs.org/). 

## Principios

### Declarativo

La manipulación del DOM es uno de los principales cuellos de botella en la performance del front-end. React decide entonces tomar un enfoque más _declarativo_ y busca evitar que el browser esté continuamente realizando operaciones costosas.

Por lo tanto, sólo vamos a encargarnos de diseñar las _vistas_ para cada _estado_ de nuestra aplicación y **React va a actualizar y renderizar de manera eficiente los componentes correctos cuando los datos cambien** (estado), haciendo cambios mínimos en el DOM. **La vista pasa a ser una función del estado** de la aplicación.

El código declarativo es más predecible y por lo tanto, más fácil de de razonar y debuggear.

### Arquitectura basada en _componentes_
