XQuery  
\# Ejercicio 1\. Biblioteca

\<library\>  
  \<book\>  
    \<title\>Clean Code\</title\>  
    \<author\>Robert C. Martin\</author\>  
    \<genre\>Programming\</genre\>  
    \<price currency="USD"\>32.99\</price\>  
    \<stock\>20\</stock\>  
  \</book\>  
  ...  
\</library\>  
Pregunta 1\. Selecciona todos los títulos de los libros.  
//library/book/title

Pregunta 2\. Selecciona los títulos de libros cuyo precio sea mayor a 15\.  
//library/book\[price \> 15\]/title

Pregunta 3\. Selecciona los autores y sus países de origen.  
//library/book/(author | author/@pais)

Pregunta 4\. Calcula el precio promedio de los libros.  
avg(//library/book/price)

Pregunta 5\. Selecciona los títulos de los libros ordenados alfabéticamente.  
//library/book/title\[order by . ascending\]

Pregunta 6\. Devuelve los títulos y precios de los libros en formato XML.

\<book\>  
  \<title\>{//library/book/title}\</title\>  
  \<price\>{//library/book/price}\</price\>  
\</book\>  
Pregunta 7\. Selecciona los libros del género "Ficción".  
//library/book\[@genre="Ficción"\]

Pregunta 8\. Devuelve los libros cuyo autor sea de "EE.UU.".  
//library/book\[author/@pais="EE.UU."\]

Pregunta 9\. Lista los libros y su precio total (precio \+ 5 USD de impuesto).

\<book\>  
  \<title\>{//library/book/title}\</title\>  
  \<total\>{//library/book/price \+ 5}\</total\>  
\</book\>  
Pregunta 10\. Devuelve el libro más caro en el catálogo.  
//library/book\[price \= max(//library/book/price)\]/(title | price)

Ejercicio 2\. Tienda

\<store\>  
  \<product\>  
    \<name\>Smartphone\</name\>  
    \<brand\>BrandX\</brand\>  
    \<price currency="USD"\>699.99\</price\>  
    \<stock\>50\</stock\>  
  \</product\>  
  ...  
\</store\>  
Pregunta 1\. Selecciona todos los nombres de productos.  
//store/product/name

Pregunta 2\. Selecciona los productos de la marca "BrandX".  
//store/product\[brand="BrandX"\]

Pregunta 3\. Selecciona el producto más barato.  
//store/product\[price \= min(//store/product/price)\]

Pregunta 4\. Selecciona el producto más caro.  
//store/product\[price \= max(//store/product/price)\]

Pregunta 5\. Selecciona los nombres y precios de productos con más de 30 unidades en stock.  
//store/product\[stock \> 30\]/(name | price)

Pregunta 6\. Selecciona el atributo currency de todos los precios.  
//store/product/price/@currency

Pregunta 7\. Cuenta cuántos productos hay en stock con menos de 20 unidades.  
count(//store/product\[stock \< 20\])

Pregunta 8\. Selecciona los nombres de todos los productos cuyo precio sea mayor a 500\.  
//store/product\[price \> 500\]/name

Pregunta 9\. Selecciona los nombres de productos con el atributo id mayor a 202\.  
//store/product\[@id \> 202\]/name

Pregunta 10\. Selecciona todos los nodos completos de productos con "BrandZ".  
//store/product\[brand="BrandZ"\]

Ejercicio 3\. Música  
\<musicCatalog\>  
  \<album\>  
    \<title\>Thriller\</title\>  
    \<artist\>Michael Jackson\</artist\>  
    \<genre\>Pop\</genre\>  
    \<price currency="USD"\>15.99\</price\>  
    \<stock\>50\</stock\>  
  \</album\>  
  ...  
\</musicCatalog\>  
Pregunta 1\. Selecciona todos los títulos de los álbumes.  
//musicCatalog/album/title

Pregunta 2\. Selecciona los títulos de los álbumes del género "Rock".  
//musicCatalog/album\[genre="Rock"\]/title

Pregunta 3\. Selecciona el precio del álbum "21".  
//musicCatalog/album\[title="21"\]/price

Pregunta 4\. Cuenta cuántos álbumes tienen más de 20 en stock.  
count(//musicCatalog/album\[stock \> 20\])

Pregunta 5\. Selecciona los nombres de los artistas cuyos álbumes cuestan más de 18 USD.  
//musicCatalog/album\[price \> 18\]/artist

Pregunta 6\. Selecciona el álbum más caro.  
//musicCatalog/album\[price \= max(//musicCatalog/album/price)\]

Pregunta 7\. Selecciona el género del álbum "Thriller".  
//musicCatalog/album\[title="Thriller"\]/genre

Pregunta 8\. Selecciona el ID de todos los álbumes de la artista "Adele".  
//musicCatalog/album\[artist="Adele"\]/@id

Pregunta 9\. Selecciona los álbumes con menos de 30 en stock.  
//musicCatalog/album\[stock \< 30\]

Pregunta 10\. Selecciona todos los géneros únicos disponibles.  
distinct-values(//musicCatalog/album/genre)

Ejercicio 4\. Estudiantes

\<students\>  
  \<student\>  
    \<name\>John Doe\</name\>  
    \<age\>22\</age\>  
    \<grade\>9.0\</grade\>  
    \<career\>Engineering\</career\>  
  \</student\>  
  ...  
\</students\>  
Pregunta 1\. Selecciona los nombres de los estudiantes.  
//students/student/name

Pregunta 2\. Filtra los estudiantes con una nota mayor a 8\.  
//students/student\[grade \> 8\]

Pregunta 3\. Devuelve los nombres y las carreras de los estudiantes.  
//students/student/(name | career)

Pregunta 4\. Calcula la nota promedio de los estudiantes.  
avg(//students/student/grade)

Pregunta 5\. Devuelve los estudiantes de la carrera "Ingeniería".  
//students/student\[career="Engineering"\]

Pregunta 6\. Ordena a los estudiantes por edad.  
//students/student\[order by age ascending\]

Pregunta 7\. Devuelve el estudiante más joven.  
//students/student\[age \= min(//students/student/age)\]

Pregunta 8\. Devuelve los nombres y las notas incrementadas en 0.5.

\<student\>  
  \<name\>{//students/student/name}\</name\>  
  \<grade\>{//students/student/grade \+ 0.5}\</grade\>  
\</student\>  
Pregunta 9\. Devuelve los estudiantes cuya nota es mayor a 8 y pertenecen a Ingeniería.  
//students/student\[grade \> 8 and career="Engineering"\]

Pregunta 10\. Cuenta cuántos estudiantes hay en total.  
count(//students/student)

Ejercicio 5\. Pedidos  
\<orders\>  
  \<order\>  
    \<client\>Client A\</client\>  
    \<product\>Product 1\</product\>  
    \<quantity\>3\</quantity\>  
    \<price currency="USD"\>30.0\</price\>  
  \</order\>  
  ...  
\</orders\>  
Pregunta 1\. Devuelve los nombres de los clientes.  
//orders/order/client

Pregunta 2\. Devuelve los productos con precio total (cantidad × precio).

\<order\>  
  \<product\>{//orders/order/product}\</product\>  
  \<total\>{//orders/order/quantity \* //orders/order/price}\</total\>  
\</order\>  
Pregunta 3\. Filtra los pedidos cuyo precio total sea mayor a 100\.  
//orders/order\[quantity \* price \> 100\]

Pregunta 4\. Calcula el precio promedio de todos los pedidos.  
avg(//orders/order/price)

Pregunta 5\. Devuelve el pedido más caro.  
//orders/order\[price \= max(//orders/order/price)\]

Pregunta 6\. Ordena los pedidos por cliente alfabéticamente.  
//orders/order\[order by client ascending\]

Pregunta 7\. Calcula el precio total de todos los pedidos.  
sum(//orders/order/price)

Pregunta 8\. Devuelve los nombres de los clientes que compraron más de 3 unidades.  
//orders/order\[quantity \> 3\]/client

Pregunta 9\. Devuelve los productos y sus precios con un descuento del 15%.

\<order\>  
  \<product\>{//orders/order/product}\</product\>  
  \<discountedPrice\>{//orders/order/price \* 0.85}\</discountedPrice\>  
\</order\>  
Pregunta 10\. Cuenta el número total de pedidos.  
count(//orders/order)  
