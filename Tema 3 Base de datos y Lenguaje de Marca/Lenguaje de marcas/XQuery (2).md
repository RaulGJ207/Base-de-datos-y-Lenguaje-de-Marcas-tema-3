Ejercicio 1 \- Biblioteca  
Pregunta 1: Devuelve todos los títulos de los libros.  
for $libro in doc("biblioteca.xml")/biblioteca/libro  
return $libro/titulo

Pregunta 2: Devuelve los títulos de libros cuyo precio es mayor a 15\.  
for $libro in doc("biblioteca.xml")/biblioteca/libro  
where $libro/precio \> 15  
return $libro/titulo

Pregunta 3: Lista los autores y sus países de origen.  
for $libro in doc("biblioteca.xml")/biblioteca/libro  
return \<autor\>  
  \<nombre\>{$libro/autor/text()}\</nombre\>  
  \<pais\>{$libro/autor/@pais}\</pais\>  
\</autor\>

Pregunta 4: Calcula el precio promedio de los libros.  
let $precios := doc("biblioteca.xml")/biblioteca/libro/precio  
return avg($precios)

Pregunta 5: Devuelve los títulos ordenados alfabéticamente.  
for $libro in doc("biblioteca.xml")/biblioteca/libro  
order by $libro/titulo ascending  
return $libro/titulo

Pregunta 6: Devuelve los títulos y precios de los libros en formato XML.  
for $libro in doc("biblioteca.xml")/biblioteca/libro  
return \<libro\>  
  \<titulo\>{$libro/titulo}\</titulo\>  
  \<precio\>{$libro/precio}\</precio\>  
\</libro\>

Pregunta 7: Encuentra libros del género "Ficción".  
for $libro in doc("biblioteca.xml")/biblioteca/libro  
where $libro/@genero \= "Ficción"  
return $libro/titulo

Pregunta 8: Devuelve los libros cuyo autor sea de "EE.UU.".  
for $libro in doc("biblioteca.xml")/biblioteca/libro  
where $libro/autor/@pais \= "EE.UU."  
return $libro

Pregunta 9: Lista los libros y su precio total (precio \+ 5 USD de impuesto).  
for $libro in doc("biblioteca.xml")/biblioteca/libro  
let $total := $libro/precio \+ 5  
return \<libro\>  
  \<titulo\>{$libro/titulo}\</titulo\>  
  \<precioTotal\>{$total}\</precioTotal\>  
\</libro\>

Pregunta 10: Devuelve el libro más caro en el catálogo.  
let $max := max(doc("biblioteca.xml")/biblioteca/libro/precio)  
for $libro in doc("biblioteca.xml")/biblioteca/libro  
where $libro/precio \= $max  
return $libro

Ejercicio 2 \- Tienda  
Pregunta 1: Devuelve los nombres de todos los productos.  
for $producto in doc("tienda.xml")/tienda/producto  
return $producto/nombre

Pregunta 2: Devuelve los productos de la categoría "Accesorios".   
for $producto in doc("tienda.xml")/tienda/producto  
where $producto/@categoria \= "Accesorios"  
return $producto

Pregunta 3: Calcula el precio total de todos los productos.  
sum(doc("tienda.xml")/tienda/producto/precio)

Pregunta 4: Encuentra productos con un precio mayor a 500 USD.   
for $producto in doc("tienda.xml")/tienda/producto  
where $producto/precio \> 500  
return $producto

Pregunta 5: Devuelve los productos y sus precios con un descuento del 10%.  
for $producto in doc("tienda.xml")/tienda/producto  
let $descuento := $producto/precio \* 0.9  
return \<producto\>  
  \<nombre\>{$producto/nombre}\</nombre\>  
  \<precioDescuento\>{$descuento}\</precioDescuento\>  
\</producto\>

Pregunta 6: Lista los productos ordenados por precio de menor a mayor.  
for $producto in doc("tienda.xml")/tienda/producto  
order by $producto/precio ascending  
return $producto

Pregunta 7: Devuelve los productos de la marca "HP".  
for $producto in doc("tienda.xml")/tienda/producto  
where $producto/marca \= "HP"  
return $producto

Pregunta 8: Devuelve los nombres y categorías de los productos como elementos \<item\>.  
for $producto in doc("tienda.xml")/tienda/producto  
return \<item\>  
  \<nombre\>{$producto/nombre}\</nombre\>  
  \<categoria\>{$producto/@categoria}\</categoria\>  
\</item\>

Pregunta 9: Encuentra el producto más barato.  
let $min := min(doc("tienda.xml")/tienda/producto/precio)  
for $producto in doc("tienda.xml")/tienda/producto  
where $producto/precio \= $min  
return $producto

Pregunta 10: Calcula el precio promedio de los productos en la categoría "Computadoras".  
let $precios := doc("tienda.xml")/tienda/producto\[@categoria="Computadoras"\]/precio  
return avg($precios)

Ejercicio 4 \- Estudiantes  
Pregunta 1: Devuelve los nombres de los estudiantes.  
for $estudiante in doc("estudiantes.xml")/estudiantes/estudiante  
return $estudiante/nombre

Pregunta 2: Filtra los estudiantes con una nota mayor a 8\.  
for $estudiante in doc("estudiantes.xml")/estudiantes/estudiante  
where $estudiante/nota \> 8  
return $estudiante

Pregunta 3: Devuelve los nombres y las carreras de los estudiantes.  
for $estudiante in doc("estudiantes.xml")/estudiantes/estudiante  
return \<estudiante\>  
  \<nombre\>{$estudiante/nombre}\</nombre\>  
  \<carrera\>{$estudiante/@carrera}\</carrera\>  
\</estudiante\>

Pregunta 4: Calcula la nota promedio de los estudiantes.  
let $notas := doc("estudiantes.xml")/estudiantes/estudiante/nota  
return avg($notas)

Pregunta 5: Devuelve los estudiantes de la carrera "Ingeniería".  
for $estudiante in doc("estudiantes.xml")/estudiantes/estudiante  
where $estudiante/@carrera \= "Ingeniería"  
return $estudiante

Pregunta 6: Ordena a los estudiantes por edad.  
for $estudiante in doc("estudiantes.xml")/estudiantes/estudiante  
order by $estudiante/edad ascending  
return $estudiante

Pregunta 7: Devuelve el estudiante más joven.  
let $minEdad := min(doc("estudiantes.xml")/estudiantes/estudiante/edad)  
for $estudiante in doc("estudiantes.xml")/estudiantes/estudiante  
where $estudiante/edad \= $minEdad  
return $estudiante

Pregunta 8: Devuelve los nombres y las notas incrementadas en 0.5.  
for $estudiante in doc("estudiantes.xml")/estudiantes/estudiante  
let $notaIncrementada := $estudiante/nota \+ 0.5  
return \<estudiante\>  
  \<nombre\>{$estudiante/nombre}\</nombre\>  
  \<notaIncrementada\>{$notaIncrementada}\</notaIncrementada\>  
\</estudiante\>

Pregunta 9: Devuelve los estudiantes cuya nota es mayor a 8 y pertenecen a Ingeniería.  
for $estudiante in doc("estudiantes.xml")/estudiantes/estudiante  
where $estudiante/nota \> 8 and $estudiante/@carrera \= "Ingeniería"  
return $estudiante

Pregunta 10: Cuenta cuántos estudiantes hay en total.  
count(doc("estudiantes.xml")/estudiantes/estudiante)

Ejercicio 5 \- Pedidos  
Pregunta 1: Devuelve los nombres de los clientes.  
for $pedido in doc("pedidos.xml")/pedidos/pedido  
return $pedido/@cliente

Pregunta 2: Devuelve los productos con precio total (cantidad × precio).  
for $pedido in doc("pedidos.xml")/pedidos/pedido  
let $precioTotal := $pedido/cantidad \* $pedido/precio  
return \<producto\>  
  \<nombre\>{$pedido/producto}\</nombre\>  
  \<precioTotal\>{$precioTotal}\</precioTotal\>  
\</producto\>

Pregunta 3: Filtra los pedidos cuyo precio total sea mayor a 100\.  
for $pedido in doc("pedidos.xml")/pedidos/pedido  
let $precioTotal := $pedido/cantidad \* $pedido/precio  
where $precioTotal \> 100  
return $pedido

Pregunta 4: Calcula el precio promedio de todos los pedidos.  
let $preciosTotales := for $pedido in doc("pedidos.xml")/pedidos/pedido  
return $pedido/cantidad \* $pedido/precio  
return avg($preciosTotales)

Pregunta 5: Devuelve el pedido más caro.  
let $maxPrecio := max(for $pedido in doc("pedidos.xml")/pedidos/pedido  
return $pedido/cantidad \* $pedido/precio)  
for $pedido in doc("pedidos.xml")/pedidos/pedido  
where $pedido/cantidad \* $pedido/precio \= $maxPrecio  
return $pedido

Pregunta 6: Ordena los pedidos por cliente alfabéticamente.  
for $pedido in doc("pedidos.xml")/pedidos/pedido  
order by $pedido/@cliente ascending  
return $pedido

Pregunta 7: Calcula el precio total de todos los pedidos.  
sum(for $pedido in doc("pedidos.xml")/pedidos/pedido  
return $pedido/cantidad \* $pedido/precio)

Pregunta 8: Devuelve los nombres de los clientes que compraron más de 3 unidades.  
for $pedido in doc("pedidos.xml")/pedidos/pedido  
where $pedido/cantidad \> 3  
return $pedido/@cliente

Pregunta 9: Devuelve los productos y sus precios con un descuento del 15%.  
for $pedido in doc("pedidos.xml")/pedidos/pedido  
let $precioConDescuento := $pedido/precio \* 0.85  
return \<producto\>  
  \<nombre\>{$pedido/producto}\</nombre\>  
  \<precioDescuento\>{$precioConDescuento}\</precioDescuento\>  
\</producto\>

Pregunta 10: Cuenta el número total de pedidos.  
count(doc("pedidos.xml")/pedidos/pedido)
