
## Que se aprendió a lo largo de este curso
* Definir un template y crear áreas.
* Definir el tamaño de las columnas.
* Establecer el tamaño de las líneas.
* Colocar los elementos en sus áreas.
* Definir un template sin áreas.
* Establecer el número de columnas.
* Establecer el número de filas.
* Especifícar a los elementos dónde empezar y dónde terminar.
* Establecer el espacio entre filas y columnas con la propiedad `gap`.
* Definir una grid dentro de otra.
* Calcular el ancho.
* Utilizar media queries para que el sitio sea responsive.

**Comentarios**: 
* En el archivo `destacados.css` se hizo un calculo en la clase destaques en donde se va a calcular el 100% de nuestra pantalla y se adiciona que comience a partir de los 50px que tiene el encabezado 
* Como en la `section` con la clase `destaques` se tienen varios `divs` con la clase `destaques__secundario` a la hora de colocar la imagen de pubg se repite 4 veces, para esto se tiene que indicar que solo se va a mostrar en el primer `div`, esto se logra con la pseudo-clase `nth-child` y así de la misma manera se pueden especificar con los demás `divs`
* El siguiente código permite establecer estilos a las imagenes:
```
    background-image: url('../img/slack.png');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
``` 
Pero una forma de simplificar el código anterior sería de la siguiente manera:
```
    background: url('../img/slack.png') center / cover no-repeat;
```
* El siguiente código permite establecer desde que columna debe tomar (inicio) y hasta que columna debe terminar (fin):
```
    grid-column-start: 4;
    grid-column-end: 4;
```
Pero también se puede simplificar quedando de la siguiente manera:
```
    grid-column: 1 / 4;
```
Y así mismo funciona con las filas:
```
    grid-row: 1 / 4;
```
* Si definimos 5 cards por línea necesitamos calcular el tamaño de nuestras cards: `100% / 5 = 20%`, pero si también agregamos margen derecho de `1rem` para que entre una card y otra haya un espacio se necesita tener en cuenta este espacio al definir el tamaño de las cards. ¿Cómo se puede hacer esto? Con `width: cal(20%-1rem);` ya que se esta tomando el 20% que es el tamaño de nuestras tarjetas y tomando 1 de ellas. 
* Al emparejar `grid-column-start` y `grid-column-end` se podría asumir que el valor final tiene que ser mayor que el valor inicial, pero eso no es verdad.  Por ejemplo, podriamos definir que una `grid-column-star` empiece en la columna 5 y definir que termine en la columna 2 `grid-column-end: 2`.
* En lugar de definir un elemento en la cuadrícula basado en la posición inicial y final, se puede definir basado en la longitud de columnas deseada usando la palabra clave `span`. Hay que tener presentes que `span` solo funciona con valores positivos. Por ejemplo, si indicamos que un elemento empiece en la columna 2 definimos `grid-column-start: 2` y si queremos indicar que tome 2 columnas haríamos lo siguiente `grid-column-end: 4`, pero utilizando la palabra clave quedaría de la siguiente manera `grid-column-end: span 2`.
  * Otro ejemplo sería el siguiente: `grid-column: 2 / span 3`.
  * También se puede usar la clave `span`con `grid-column-start` para establecer la anchura del elemento en relación a la posición final, ejemplo:
    ```
    grid-column-start: span 3;
    grid-column-end: 6;
    ```
* Una forma de abreviar `grid-column` y `grid-row` sería de la siguiente manera `grid-area`, el cuál admite 4 valores separados por slash, el primero sería `grid-row-start`, el segundo `grid-column-start`, el tercero `grid-row-end` y el cuarto `grid-column-end`. Un ejemplo sería el siguiente `grid-area: 1 / 1 / 3 / 6`.
* Múltiples elementos se pueden superponer sin problemas.
* También se puede usar la propiedad `order`, por defecto el valor `order` de todos los elementos es igual a 0, pero puede ser establecido a cualquier valor positivo o negativo.
* Con `grid-template-columns` podemos definir el total de columnas, así como definir su tamaño, por ejemplo, si queremos 5 columnas y que cada una tenga un tamaño del 20% se haría lo siguiente: `grid-template-columns: 20% 20% 20% 20% 20%` y así mismo se pueden definir el total de las columnas con `grid-template-rows`.
  * Una forma corta o de simplificar cuantas columnas queremos tener sería usar la función `repeat`, siguiendo el ejemplo anterior donde se querían definir 5 columnas con un tamaño del 20% cada una se logría con `grid-template-columns: repeat(5, 20%)`, el primer parámetro define cuantas columnas se desean crear y el segundo parámetro su tamaño. La función `repeat` tambien funciona con `grid-template-rows`.
  * No solo acepta valores porcentuales, sino también otras unidades como px, ems, fr y también se pueden mezclar diferentes unidades a la vez `grid-template-columns: 100px 3em 40%`.
  * La unidad de medida `fr` (fracción) le asigna una porción del espacio disponible, por ejemplo, si dos elementos están establecidos a `1fr` y `3fr` respectivamente el espacio se divide en 4 porciones iguales o en mis palabras, declaramos que tenemos 4 columnas, donde el primer elemento ocupar 1/4 del espacio y el segundo elementos 3/4 restantes (el primero toma una columna y el segundo las 3 columnas restantes). Quedando de la siguiente manera `grid-template-columns: 1fr 3fr`.
  * `grid-template` es una propiedad abreviada que combina `grid-template-rows` y `grid-template-columns`. Por ejemplo, `grid-template: 50% 50% / 200px;` creará una cuadrícula con dos filas que ocuparán el 50% de alto cada una, y una columna que será 200 píxeles de ancho.