\# XPath (Ejercicios)

\_\_Ejercicio 1\_\_. Tienda de Libros

\`\`\`xml  
\<bookstore\>  
  \<book id="101"\>  
    \<title\>Clean Code\</title\>  
    \<author\>Robert C. Martin\</author\>  
    \<genre\>Programming\</genre\>  
    \<price currency="USD"\>32.99\</price\>  
    \<stock\>20\</stock\>  
  \</book\>  
  \<book id="102"\>  
    \<title\>The Pragmatic Programmer\</title\>  
    \<author\>Andrew Hunt\</author\>  
    \<genre\>Programming\</genre\>  
    \<price currency="USD"\>40.50\</price\>  
    \<stock\>15\</stock\>  
  \</book\>  
  \<book id="103"\>  
    \<title\>1984\</title\>  
    \<author\>George Orwell\</author\>  
    \<genre\>Fiction\</genre\>  
    \<price currency="USD"\>12.99\</price\>  
    \<stock\>50\</stock\>  
  \</book\>  
  \<book id="104"\>  
    \<title\>The Art of War\</title\>  
    \<author\>Sun Tzu\</author\>  
    \<genre\>Philosophy\</genre\>  
    \<price currency="USD"\>9.99\</price\>  
    \<stock\>30\</stock\>  
  \</book\>  
  \<book id="105"\>  
    \<title\>Thinking, Fast and Slow\</title\>  
    \<author\>Daniel Kahneman\</author\>  
    \<genre\>Psychology\</genre\>  
    \<price currency="USD"\>20.00\</price\>  
    \<stock\>10\</stock\>  
  \</book\>  
\</bookstore\>  
\`\`\`

\_Pregunta 1\_. Selecciona todos los títulos de los libros.  
//book/title  
\_Pregunta 2\_. Selecciona los autores de los libros en el género "Programming".  
//book\[genre="Programming"\]/author  
\_Pregunta 3\_. Selecciona el precio del libro "The Art of War".  
//book\[title="The Art of War"\]/price  
\_Pregunta 4\_. Cuenta cuántos libros tienen más de 20 en stock.  
count(//book\[stock \< 20\])  
\_Pregunta 5\_. Selecciona todos los géneros únicos disponibles en la tienda.  
distinct-values(//genre)  
\_Pregunta 6\_. Selecciona el autor cuyo libro cuesta más.  
//book\[price \= max(//book/price)\]/author  
\_Pregunta 7\_. Selecciona el título del libro más barato.  
//book\[price \= min(//book/price)\]/title  
\_Pregunta 8\_. Selecciona todos los libros cuyo precio esté entre 10 y 30\.  
//book\[price \> 10 and price \< 30\]  
\_Pregunta 9\_. Selecciona todos los libros que tengan menos de 20 unidades en stock.  
//book\[stock \< 20\]  
\_Pregunta 10\_. Selecciona el atributo id de todos los libros.  
//book/@id  
\_\_Ejercicio 2\_\_. Tienda de electrónica.

\`\`\`xml  
\<electronics\>  
  \<item id="201"\>  
    \<name\>Smartphone\</name\>  
    \<brand\>BrandX\</brand\>  
    \<price currency="USD"\>699.99\</price\>  
    \<stock\>50\</stock\>  
  \</item\>  
  \<item id="202"\>  
    \<name\>Laptop\</name\>  
    \<brand\>BrandY\</brand\>  
    \<price currency="USD"\>999.99\</price\>  
    \<stock\>10\</stock\>  
  \</item\>  
  \<item id="203"\>  
    \<name\>Tablet\</name\>  
    \<brand\>BrandX\</brand\>  
    \<price currency="USD"\>399.99\</price\>  
    \<stock\>25\</stock\>  
  \</item\>  
  \<item id="204"\>  
    \<name\>Headphones\</name\>  
    \<brand\>BrandZ\</brand\>  
    \<price currency="USD"\>199.99\</price\>  
    \<stock\>100\</stock\>  
  \</item\>  
\</electronics\>  
\`\`\`

\_\_Pregunta 1\_\_. Selecciona todos los nombres de productos.

\_\_Pregunta 2\_\_. Selecciona los productos de la marca "BrandX".  
//item/name  
\_\_Pregunta 3\_\_. Selecciona el producto más barato.  
//item\[price \= min(//price)\]  
\_\_Pregunta 4\_\_. Selecciona el producto más caro.  
//item\[price \= max(//price)\]  
\_\_Pregunta 5\_\_. Selecciona los nombres y precios de productos con más de 30 unidades en stock.  
//item\[stock \> 30 \]/name | //item\[stock \> 30 \]/price  
\_\_Pregunta 6\_\_. Selecciona el atributo currency de todos los precios.  
//price/@currency  
\_\_Pregunta 7\_\_. Cuenta cuántos productos hay en stock con menos de 20 unidades.  
count(//item\[stock \< 30 \])  
\_\_Pregunta 8\_\_. Selecciona los nombres de todos los productos cuyo precio sea mayor a 500\.  
//item\[price \> 500 \]/name  
\_\_Pregunta 9\_\_. Selecciona los nombres de productos con el atributo id mayor a 202\.  
//item\[@id \> 202 \]/name  
\_\_Pregunta 10\_\_. Selecciona todos los nodos completos de productos con "BrandZ".  
//item\[brand \= "BrandZ"\]

\_\_Ejercicio 3\_\_. Biblioteca digital.

\`\`\`xml  
\<library\>  
  \<book id="301"\>  
    \<title\>The Catcher in the Rye\</title\>  
    \<author\>J.D. Salinger\</author\>  
    \<genre\>Fiction\</genre\>  
    \<available\>true\</available\>  
  \</book\>  
  \<book id="302"\>  
    \<title\>To Kill a Mockingbird\</title\>  
    \<author\>Harper Lee\</author\>  
    \<genre\>Fiction\</genre\>  
    \<available\>false\</available\>  
  \</book\>  
  \<book id="303"\>  
    \<title\>The Great Gatsby\</title\>  
    \<author\>F. Scott Fitzgerald\</author\>  
    \<genre\>Fiction\</genre\>  
    \<available\>true\</available\>  
  \</book\>  
  \<book id="304"\>  
    \<title\>1984\</title\>  
    \<author\>George Orwell\</author\>  
    \<genre\>Dystopian\</genre\>  
    \<available\>true\</available\>  
  \</book\>  
  \<book id="305"\>  
    \<title\>Moby Dick\</title\>  
    \<author\>Herman Melville\</author\>  
    \<genre\>Adventure\</genre\>  
    \<available\>false\</available\>  
  \</book\>  
\</library\>  
\`\`\`

\_\_Pregunta 1\_\_. Selecciona todos los títulos de los libros.  
//book/title  
\_\_Pregunta 2\_\_. Selecciona todos los libros disponibles (con available="true").  
//book\[available= "true"\]  
\_\_Pregunta 3\_\_. Selecciona el autor del libro "1984".  
//book\[title= "1984"\]/author  
\_\_Pregunta 4\_\_. Selecciona todos los géneros de libros únicos.  
//book\[available= "true"\]/genre  
\_\_Pregunta 5\_\_. Cuenta cuántos libros están disponibles.  
count(//book\[available= "true"\])  
\_\_Pregunta 6\_\_. Selecciona los títulos de los libros que no están disponibles.  
//book\[available= "false"\]/title  
\_\_Pregunta 7\_\_. Selecciona los autores cuyos libros están disponibles.  
//book\[available= "true"\]/author	  
\_\_Pregunta 8\_\_. Selecciona el ID del libro "The Great Gatsby".  
//book\[title= "The Great Gatsby"\]/@id  
\_\_Pregunta 9\_\_. Selecciona todos los libros del género "Fiction".  
//book\[genre= "Fiction"\]  
\_\_Pregunta 10\_\_. Selecciona los títulos de los libros cuyo autor es "Herman Melville".  
//book\[author= "Herman Melville"\]  
\_\_Ejercicio 4\_\_. Catálogo de Música

\`\`\`xml  
\<musicCatalog\>  
  \<album id="101"\>  
    \<title\>Thriller\</title\>  
    \<artist\>Michael Jackson\</artist\>  
    \<genre\>Pop\</genre\>  
    \<price currency="USD"\>15.99\</price\>  
    \<stock\>50\</stock\>  
  \</album\>  
  \<album id="102"\>  
    \<title\>The Dark Side of the Moon\</title\>  
    \<artist\>Pink Floyd\</artist\>  
    \<genre\>Rock\</genre\>  
    \<price currency="USD"\>20.99\</price\>  
    \<stock\>30\</stock\>  
  \</album\>  
  \<album id="103"\>  
    \<title\>Back in Black\</title\>  
    \<artist\>AC/DC\</artist\>  
    \<genre\>Rock\</genre\>  
    \<price currency="USD"\>18.50\</price\>  
    \<stock\>25\</stock\>  
  \</album\>  
  \<album id="104"\>  
    \<title\>21\</title\>  
    \<artist\>Adele\</artist\>  
    \<genre\>Pop\</genre\>  
    \<price currency="USD"\>12.99\</price\>  
    \<stock\>100\</stock\>  
  \</album\>  
  \<album id="105"\>  
    \<title\>Abbey Road\</title\>  
    \<artist\>The Beatles\</artist\>  
    \<genre\>Rock\</genre\>  
    \<price currency="USD"\>19.99\</price\>  
    \<stock\>10\</stock\>  
  \</album\>  
\</musicCatalog\>  
\`\`\`

\_\_Pregunta 1\_\_. Selecciona todos los títulos de los álbumes.  
//album/title  
\_\_Pregunta 2\_\_. Selecciona los títulos de los álbumes del género "Rock".  
//album\[genre="Rock"\]/title  
\_\_Pregunta 3\_\_. Selecciona el precio del álbum "21".  
//album\[title="21"\]/price  
\_\_Pregunta 4\_\_. Cuenta cuántos álbumes tienen más de 20 en stock.  
count(//album\[stock \> 20\])  
\_\_Pregunta 5\_\_. Selecciona los nombres de los artistas cuyos álbumes cuestan más de 18 USD.  
//album\[price \> "18"\]/artist  
\_\_Pregunta 6\_\_. Selecciona el álbum más caro.  
//album\[price \= max(//price)  
\_\_Pregunta 7\_\_. Selecciona el género del álbum "Thriller".  
//album\[title \= "Thriller"\]/genre  
\_\_Pregunta 8\_\_. Selecciona el ID de todos los álbumes de la artista "Adele".  
//album\[artist \= "Adele"\]/@id  
\_\_Pregunta 9\_\_. Selecciona los álbumes con menos de 30 en stock.  
//album\[stock \< 30\]  
\_\_Pregunta 10\_\_. Selecciona todos los géneros únicos disponibles.  
distinct-values(//genre)  
\_\_Ejercicio 5\_\_. Inventario de Productos

\`\`\`xml  
\<inventory\>  
  \<product id="P001"\>  
    \<name\>Chair\</name\>  
    \<category\>Furniture\</category\>  
    \<price currency="USD"\>49.99\</price\>  
    \<stock\>200\</stock\>  
  \</product\>  
  \<product id="P002"\>  
    \<name\>Table\</name\>  
    \<category\>Furniture\</category\>  
    \<price currency="USD"\>129.99\</price\>  
    \<stock\>50\</stock\>  
  \</product\>  
  \<product id="P003"\>  
    \<name\>Lamp\</name\>  
    \<category\>Lighting\</category\>  
    \<price currency="USD"\>19.99\</price\>  
    \<stock\>100\</stock\>  
  \</product\>  
  \<product id="P004"\>  
    \<name\>Desk\</name\>  
    \<category\>Furniture\</category\>  
    \<price currency="USD"\>249.99\</price\>  
    \<stock\>20\</stock\>  
  \</product\>  
  \<product id="P005"\>  
    \<name\>Ceiling Light\</name\>  
    \<category\>Lighting\</category\>  
    \<price currency="USD"\>79.99\</price\>  
    \<stock\>30\</stock\>  
  \</product\>  
\</inventory\>  
\`\`\`

\_\_Pregunta 1\_\_. Selecciona los nombres de todos los productos.  
//product/name  
\_\_Pregunta 2\_\_. Selecciona todos los productos de la categoría "Furniture".  
//product\[ category \= "Furniture"\]  
\_\_Pregunta 3\_\_. Selecciona el precio del producto "Lamp".  
//product\[ name= "Lamp"\]/price  
\_\_Pregunta 4\_\_. Cuenta cuántos productos tienen más de 50 en stock.  
count(//product\[stock \< "50"\])  
\_\_Pregunta 5\_\_. Selecciona el producto más caro.  
//product\[price \= max(//price)\]  
\_\_Pregunta 6\_\_. Selecciona los nombres de los productos con menos de 30 en stock.  
//product\[stock \> "30"\]/name  
\_\_Pregunta 7\_\_. Selecciona todos los precios en USD.  
//price  
\_\_Pregunta 8\_\_. Selecciona el ID de todos los productos de la categoría "Lighting".  
//product\[category \= "Lighting"\]/@id  
\_\_Pregunta 9\_\_. Selecciona el precio del producto más barato.  
//product\[price \= min(//price)\]/price  
\_\_Pregunta 10\_\_. Selecciona los nombres y precios de todos los productos ordenados por precio.  
//product/(name | price)