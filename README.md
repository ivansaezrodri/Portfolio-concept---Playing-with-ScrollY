# Portfolio de ejemplo usando ScrollY
![Imagen portfolio](https://i.ibb.co/SxH5rNn/imagen-2022-12-19-130809383.png)

En este portfolio he usado la propiedad _scrollY_ del objeto Window que retorna el número de píxeles que han sido desplazados en el documento mediante el scroll vertical.  He utilizado **JavaScript** puro sin ningún framework para tener mayor agilidad con el mismo.

## Como llegamos a esta animación
Existen diversas formas de conseguir estas "animaciones", por ejemplo en la página oficial de [**Apple**](https://www.apple.com/es/macbook-pro-14-and-16/) cuando se hace _scroll_ en alguno de sus portátiles, se puede ver como se abre el dispositivo a medida que bajamos en la página.

![Imagen ejemplo Apple](https://i.ibb.co/8mxn4SZ/Screenshot-20221219-181159.png)

Esto podríamos conseguirlo con una correlación de imágenes  dentro de un array y cuando detectemos que baja el usuario intercalaremos cada una de estas imágenes con un for.
```
var animacion=[
'portatil-1-frame.png',
'portatil-2-frame.png',
'portatil-3-frame.png',
'portatil-4-frame.png',
...]
```

Esto suele venir bien cuando tenemos un render del dispositivo a presentar, en mi caso no ha hecho falta ya que he jugado con tamaños absolutos de etiquetas propias del lenguaje de marcado.

## Como he cubierto mis necesidades sin ningún framework

Al no querer usar ningún framework para practicar mis conocimientos en JS me he inventado un sistema para _"fragmentar"_ esta transición entre una posición y otra, entre un tamaño y otro, entre un número y otro.

- Nos surge la necesidad de cambiar la opacidad de una etiqueta de **`opacity(0%)`** a **`opacity(100%)`** . 
- Disponemos de la propiedad _**ScrollY**_ del objeto **Window**.
- Cuando hacemos _scroll_ esta propiedad aumenta _(empieza en 0 y a medida que hacemos scroll esta propiedad se incrementa)_.
- Cuando hacemos scroll normalmente se aumenta de **100** en **100** el _**Window.ScrollY**_.

Teniendo esto en cuenta, las animaciones las he planteado de la siguiente manera:

**Cuando multiplicamos un numero _N_ por _0.Y_ sacamos el _Y%_ del total de _N_**

Sabiendo esto y teniendo en cuenta que jugamos con incrementos de _100_ en _100_, he ido restando a _**Window.ScrollY**_ la cantidad necesaria para que siempre nos posicionemos de 0 a 100.

### Ejemplo:
(_Situación: Hemos hecho scroll en la página y actualmente **Window.ScrollY** equivale a **400**_)
```
var value = Window.ScrollY;
var  yo  =  document.getElementById("yo")

if  (window.scrollY  >=  400  &&  window.scrollY  <  500)  {

	value  =  Math.round((window.scrollY)  -  400)  /  100;
	yo.style.filter  =  "opacity("  +  100  * value  +  "%)";

}

```

## [Resultado](https://ivansaezrodrigo.github.io/Portfolio-concept---Playing-with-ScrollY/)
