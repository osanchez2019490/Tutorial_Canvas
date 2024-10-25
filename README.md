# Manual de Uso de Canvas

El elemento `<canvas>` en HTML permite el dibujo de gráficos en el navegador, incluyendo figuras, gráficos y otros elementos visuales.

---

## Índice

1. [Introducción a Canvas](#1-introducción-a-canvas)
2. [Configuración Inicial](#2-configuración-inicial)
3. [Dibujar Figuras Básicas](#3-dibujar-figuras-básicas)
4. [Colores y Estilos](#4-colores-y-estilos)
5. [Dibujar Texto](#5-dibujar-texto)
6. [Imágenes en Canvas](#6-imágenes-en-canvas)
7. [Ejemplo Completo](#7-ejemplo-completo)
8. [Tutorial en SVG](#8-tutorial-en-svg)


---

### 1. Introducción a Canvas

El elemento `<canvas>` es parte de HTML5 y permite el dibujo de gráficos 2D mediante JavaScript.

```html
<canvas id="miCanvas" width="500" height="500"></canvas>
```
### 2. Configuración inicial

Antes de empezar a dibujar en el elemento <canvas>, es necesario configurar el contexto de renderizado. Este contexto es un objeto JavaScript que contiene todos los métodos y propiedades necesarias para dibujar en el canvas.

Para obtener el contexto, primero seleccionamos el elemento <canvas> en el DOM usando su id y luego llamamos al método .getContext('2d') en el elemento seleccionado. Este método especifica que queremos trabajar en 2D y devuelve un objeto CanvasRenderingContext2D que permite usar funciones como fillRect para dibujar figuras, fillText para escribir texto, y arc para crear círculos, entre muchas otras.

A continuación, el código para obtener el contexto de renderizado en 2D:
```javascript
const canvas = document.getElementById('miCanvas'); // Selecciona el elemento canvas por su id
const ctx = canvas.getContext('2d'); // Obtiene el contexto 2D del canvas
```

### 3. Dibujar figuras básicas

Una de las principales funcionalidades de Canvas es la posibilidad de dibujar formas geométricas básicas, como rectángulos y círculos. Estas figuras se pueden estilizar con diferentes colores, bordes y transparencias.

#### Dibujar un Rectángulo
Para dibujar un rectángulo en Canvas, podemos utilizar el método fillRect. Este método toma cuatro parámetros: las coordenadas x e y del punto inicial (esquina superior izquierda del rectángulo), el ancho, y la altura del rectángulo.

En el ejemplo a continuación, configuramos el color de relleno a azul utilizando fillStyle, y luego llamamos a fillRect para dibujar el rectángulo en las coordenadas especificadas.
```javascript
ctx.fillStyle = 'blue';               // Establece el color de relleno a azul
ctx.fillRect(50, 50, 150, 100);       // Dibuja un rectángulo en (50, 50) con ancho 150 y alto 100
```
#### Dibujar un Circulo

Para dibujar un círculo o arco en Canvas, usamos el método arc, el cual debe ser llamado después de beginPath para comenzar una nueva ruta de dibujo. El método arc toma seis parámetros:

1. x e y: las coordenadas del centro del círculo.
2. radio: el radio del círculo.
3. ángulo inicial: en radianes, desde donde comienza el arco.
4. ángulo final: en radianes, hasta donde llega el arco.
5. sentido antihorario: especifica si el arco debe dibujarse en sentido antihorario (true) o en sentido horario (false).

En el siguiente ejemplo, dibujamos un círculo completo en el centro de Canvas, de color rojo, con un radio de 50.
```javascript
ctx.beginPath();                       // Inicia una nueva ruta de dibujo
ctx.arc(200, 200, 50, 0, Math.PI * 2); // Dibuja un círculo completo: x, y, radio, ángulo inicial, ángulo final
ctx.fillStyle = 'red';                 // Establece el color de relleno a rojo
ctx.fill();                            // Rellena el círculo con el color especificado
```

### 4. Colores y Estilos 

El uso de colores y estilos en Canvas es esencial para mejorar la apariencia de las figuras que dibujamos. Puedes modificar el color de relleno, el color de línea, el grosor de la línea, y otros estilos visuales para hacer que tus gráficos sean más atractivos y claros.

#### Cambiar el Color de Relleno
El color de relleno determina el color que se usará al rellenar figuras como rectángulos, círculos y polígonos. Para cambiar el color de relleno, utilizamos la propiedad fillStyle del contexto.

Por ejemplo, en el siguiente código, establecemos el color de relleno a verde y dibujamos un rectángulo:
```javascript
ctx.fillStyle = 'green';               // Cambia el color de relleno a verde
ctx.fillRect(200, 50, 100, 100);       // Dibuja un rectángulo en (200, 50) con ancho 100 y alto 100
```

En este caso, el rectángulo se dibuja en las coordenadas especificadas, y el área dentro del rectángulo se rellena con el color verde. Puedes usar cualquier color CSS válido, incluyendo nombres de colores, códigos hexadecimales (#RRGGBB), o valores RGBA para colores con transparencia.

#### Cambiar el Color de Línea
Para dibujar contornos alrededor de las figuras, utilizamos el método strokeRect, que dibuja un rectángulo sin rellenarlo. Antes de llamar a este método, podemos modificar las propiedades de estilo de la línea, como el color y el grosor.

En el siguiente ejemplo, establecemos el color de la línea a púrpura y el grosor de la línea a 5 píxeles:
```javascript
ctx.strokeStyle = 'purple';            // Cambia el color de la línea a púrpura
ctx.lineWidth = 5;                     // Establece el grosor de la línea a 5 píxeles
ctx.strokeRect(350, 50, 100, 100);     // Dibuja un rectángulo contorno en (350, 50) con ancho 100 y alto 100
```
Aquí, el rectángulo se dibuja en las coordenadas especificadas con un contorno púrpura y un grosor de línea de 5 píxeles. Esto permite crear un efecto visual que destaca las figuras en el canvas.

###  5. Dibujar Texto
Dibujar texto en el canvas es una manera efectiva de agregar información y etiquetas a tus gráficos. El elemento <canvas> proporciona métodos para establecer el estilo del texto y dibujarlo en coordenadas específicas.

#### Establecer el Estilo del Texto
Antes de dibujar texto, es necesario definir su estilo. Esto incluye la fuente, el tamaño, y otros atributos como el estilo (normal, negrita, cursiva) y el alineamiento. Utilizamos la propiedad font del contexto para especificar el estilo de la fuente.

Por ejemplo, el siguiente código establece la fuente a Arial con un tamaño de 20 píxeles:
```javascript
ctx.font = '20px Arial';  // Establece la fuente a Arial con un tamaño de 20 píxeles
```

Puedes usar otras fuentes disponibles en CSS, así como combinaciones de tamaño y estilo, como 'bold 24px Verdana' para negrita.

#### Cambiar el Color del Texto
El color del texto se establece utilizando la propiedad fillStyle, similar a como se hace con las formas. En este caso, usamos negro como color de texto:
```javascript
ctx.fillStyle = 'black';  // Cambia el color del texto a negro
```
#### Dibujar el Texto
Una vez que has configurado la fuente y el color, puedes dibujar el texto en el canvas usando el método fillText(). Este método toma tres parámetros: el texto a dibujar, y las coordenadas x y y donde se ubicará el texto.

En el siguiente ejemplo, dibujamos el texto "Hola, Canvas!" en la posición (100, 300) del canvas:
```javascript
ctx.fillText('Hola, Canvas!', 100, 300);  // Dibuja el texto en las coordenadas (100, 300)
```
#### Alineación y Posicionamiento
Además de establecer la fuente y el color, puedes controlar la alineación del texto utilizando la propiedad textAlign, que puede tomar valores como 'left', 'center', o 'right'. También puedes utilizar textBaseline para definir la alineación vertical del texto, como 'top', 'middle', o 'bottom'.

Por ejemplo, si deseas centrar el texto horizontalmente:

```javascript
ctx.textAlign = 'center';        // Centra el texto horizontalmente
ctx.fillText('Hola, Canvas!', canvas.width / 2, 300);  // Dibuja el texto centrado en la parte superior
```
#### Ejemplo Completo de Texto
A continuación se muestra un código que combina todo lo anterior para dibujar texto en el canvas:
```javascript
const canvas = document.getElementById('miCanvas');
const ctx = canvas.getContext('2d');

// Establecer estilo de texto
ctx.font = '20px Arial';          // Fuente y tamaño
ctx.fillStyle = 'black';          // Color del texto
ctx.textAlign = 'center';         // Alineación horizontal

// Dibujar el texto
ctx.fillText('Hola, Canvas!', canvas.width / 2, 300);  // Dibuja el texto centrado
```

### 6. Imágenes en Canvas

Dibujar imágenes en el canvas es una característica poderosa que te permite agregar elementos visuales a tus gráficos. Puedes usar imágenes para mejorar la presentación de tus gráficos, agregar texturas o crear composiciones visuales más complejas.

Cargar una Imagen
Antes de poder dibujar una imagen, primero debes cargarla. Para esto, utilizamos el constructor Image de JavaScript. Este constructor crea un nuevo objeto de imagen que se puede manipular a través de su propiedad src. La imagen se carga de forma asíncrona, lo que significa que el código que intenta dibujar la imagen debe ejecutarse después de que la imagen se haya cargado completamente.

Aquí tienes un ejemplo de cómo se carga una imagen:

```javascript
const img = new Image();                    // Crea un nuevo objeto de imagen
img.src = 'ruta/a/imagen.png';              // Establece la ruta de la imagen
```

#### Usar el Método drawImage()
Una vez que la imagen se ha cargado, puedes dibujarla en el canvas utilizando el método drawImage(). Este método permite especificar las coordenadas x e y donde deseas colocar la imagen, así como el ancho y el alto a los que deseas que se dibuje.

El siguiente código muestra cómo dibujar una imagen una vez que se ha cargado:
```javascript
img.onload = () => {                         // Función que se ejecuta al cargar la imagen
    ctx.drawImage(img, 50, 350, 100, 100);  // Dibuja la imagen en las coordenadas (50, 350) con un tamaño de 100x100 píxeles
};
```

#### Escalar y Recortar Imágenes
El método drawImage() también se puede usar para escalar o recortar imágenes. Al especificar solo las coordenadas x e y, y el ancho y alto de la imagen, puedes cambiar el tamaño de la imagen al dibujarla. Por ejemplo, si tienes una imagen que mide 400x300 píxeles y deseas dibujarla a un tamaño de 200x150 píxeles, el código sería:
```javascript
ctx.drawImage(img, 50, 350, 200, 150);  // Dibuja la imagen escalada
```

Si deseas recortar una parte de la imagen antes de dibujarla, puedes utilizar la sobrecarga de drawImage() que permite especificar el área de recorte. Esta sobrecarga toma seis parámetros: las coordenadas del rectángulo de recorte y las coordenadas donde se dibujará la imagen.

Por ejemplo, si deseas recortar un área de 100x100 píxeles de la imagen original que comienza en (50, 50), y dibujarla en el canvas en (150, 200):
```javascript
ctx.drawImage(img, 50, 50, 100, 100, 150, 200, 100, 100);  // Recorta y dibuja la imagen
```

#### Ejemplo Completo de Imágenes
A continuación se presenta un ejemplo completo que combina la carga y el dibujo de imágenes en el canvas:
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Ejemplo de Imágenes en Canvas</title>
</head>
<body>
    <canvas id="miCanvas" width="500" height="500"></canvas>

    <script>
        const canvas = document.getElementById('miCanvas');
        const ctx = canvas.getContext('2d');

        const img = new Image();                    // Crea un nuevo objeto de imagen
        img.src = 'ruta/a/imagen.png';              // Establece la ruta de la imagen
        
        img.onload = () => {                         // Función que se ejecuta al cargar la imagen
            ctx.drawImage(img, 50, 350, 100, 100);  // Dibuja la imagen en las coordenadas (50, 350)
        };
    </script>
</body>
</html>
```

### 7. Ejemplo completo
[GitHub](https://github.com/osanchez2019490/Graficas_Canvas.git)

### 8. Tutorial en svg
[GitHub](https://github.com/dsuarez24/Manual_Explicativo.git)