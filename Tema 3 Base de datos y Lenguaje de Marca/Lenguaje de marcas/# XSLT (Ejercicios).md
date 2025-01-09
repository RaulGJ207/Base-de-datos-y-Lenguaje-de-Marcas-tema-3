\# XSLT (Ejercicios)

\_\_Ejercicio 1\_\_. Generar mediante XSLT una lista HTML desordenada \`\<ul\>\` con los nombres de las frutas. a partir del siguiente HTML.

XML de entrada:

\`\`\`xml  
\<fruits\>  
  \<fruit\>Apple\</fruit\>  
  \<fruit\>Banana\</fruit\>  
  \<fruit\>Cherry\</fruit\>  
\</fruits\>  
\`\`\`  
\<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0"\>  
  \<xsl:template match="/"\>  
    \<ul\>  
      \<xsl:for-each select="fruits/fruit"\>  
        \<li\>\<xsl:value-of select="."/\>\</li\>  
      \</xsl:for-each\>  
    \</ul\>  
  \</xsl:template\>  
\</xsl:stylesheet\>

Salida:

\`\`\`html  
\<ul\>  
  \<li\>Apple\</li\>  
  \<li\>Banana\</li\>  
  \<li\>Cherry\</li\>  
\</ul\>  
\`\`\`

\_\_Ejercicio 2\_\_. Crear una tabla HTML de libros con las columnas "Título" y "Autor".

XML de entrada:

\`\`\`xml  
\<library\>  
  \<book\>  
    \<title\>1984\</title\>  
    \<author\>George Orwell\</author\>  
  \</book\>  
  \<book\>  
    \<title\>Brave New World\</title\>  
    \<author\>Aldous Huxley\</author\>  
  \</book\>  
\</library\>  
\`\`\`  
\<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0"\>  
  \<xsl:template match="/"\>  
    \<table border="1"\>  
      \<tr\>  
        \<th\>Title\</th\>  
        \<th\>Author\</th\>  
      \</tr\>  
      \<xsl:for-each select="library/book"\>  
        \<tr\>  
          \<td\>\<xsl:value-of select="title"/\>\</td\>  
          \<td\>\<xsl:value-of select="author"/\>\</td\>  
        \</tr\>  
      \</xsl:for-each\>  
    \</table\>  
  \</xsl:template\>  
\</xsl:stylesheet\>

Salida:

\`\`\`html  
\<table border="1"\>  
  \<tr\>  
    \<th\>Title\</th\>  
    \<th\>Author\</th\>  
  \</tr\>  
  \<tr\>  
    \<td\>1984\</td\>  
    \<td\>George Orwell\</td\>  
  \</tr\>  
  \<tr\>  
    \<td\>Brave New World\</td\>  
    \<td\>Aldous Huxley\</td\>  
  \</tr\>  
\</table\>  
\`\`\`

\_\_Ejercicio 3\_\_. Crear un fichero HTML con un encabezado en cada sección. Generar encabezados \`\<h2\>\` y párrafos \`\<p\>\` para cada sección.

XML de entrada:

\`\`\`xml  
\<sections\>  
  \<section\>  
    \<title\>Introduction\</title\>  
    \<content\>Welcome to the tutorial.\</content\>  
  \</section\>  
  \<section\>  
    \<title\>Chapter 1\</title\>  
    \<content\>This is the first chapter.\</content\>  
  \</section\>  
\</sections\>  
\`\`\`  
\<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0"\>  
  \<xsl:template match="/"\>  
    \<xsl:for-each select="sections/section"\>  
      \<h2\>\<xsl:value-of select="title"/\>\</h2\>  
      \<p\>\<xsl:value-of select="content"/\>\</p\>  
    \</xsl:for-each\>  
  \</xsl:template\>  
\</xsl:stylesheet\>

Salida:

\`\`\`html  
\<h2\>Introduction\</h2\>  
\<p\>Welcome to the tutorial.\</p\>  
\<h2\>Chapter 1\</h2\>  
\<p\>This is the first chapter.\</p\>  
\`\`\`

\_\_Ejercicio 4\_\_. Generar un fichero HTML donde se resalten los productos con precio mayor a 500 en negrita \`\<b\>\`.

XML de entrada:

\`\`\`xml  
\<products\>  
  \<product\>  
    \<name\>Laptop\</name\>  
    \<price\>1000\</price\>  
  \</product\>  
  \<product\>  
    \<name\>Mouse\</name\>  
    \<price\>25\</price\>  
  \</product\>  
\</products\>  
\`\`\`  
\<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0"\>  
  \<xsl:template match="/"\>  
    \<xsl:for-each select="products/product"\>  
      \<p\>  
        \<xsl:choose\>  
          \<xsl:when test="price \&gt; 500"\>  
            \<b\>\<xsl:value-of select="name"/\>\</b\>  
          \</xsl:when\>  
          \<xsl:otherwise\>  
            \<xsl:value-of select="name"/\>  
          \</xsl:otherwise\>  
        \</xsl:choose\>  
        \- $\<xsl:value-of select="price"/\>  
      \</p\>  
    \</xsl:for-each\>  
  \</xsl:template\>  
\</xsl:stylesheet\>

Salida:

\`\`\`html  
\<p\>\<b\>Laptop\</b\> \- $1000\</p\>  
\<p\>Mouse \- $25\</p\>  
\`\`\`

\_\_Ejercicio 5\_\_. Generar un fichero HTML con una lista de navegación \`\<nav\>\`.

XML de entrada:

\`\`\`  
\<menu\>  
  \<item\>Home\</item\>  
  \<item\>About\</item\>  
  \<item\>Contact\</item\>  
\</menu\>  
\`\`\`  
\<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0"\>  
  \<xsl:template match="/"\>  
    \<nav\>  
      \<ul\>  
        \<xsl:for-each select="menu/item"\>  
          \<li\>\<xsl:value-of select="."/\>\</li\>  
        \</xsl:for-each\>  
      \</ul\>  
    \</nav\>  
  \</xsl:template\>  
\</xsl:stylesheet\>

Salida:

\`\`\`html  
\<nav\>  
  \<ul\>  
    \<li\>Home\</li\>  
    \<li\>About\</li\>  
    \<li\>Contact\</li\>  
  \</ul\>  
\</nav\>  
\`\`\`

\_\_Ejercicio 6\_\_. Generar un fichero JSON con la lista de frutas.

XML de entrada:

\`\`\`xml  
\<fruits\>  
  \<fruit\>Apple\</fruit\>  
  \<fruit\>Banana\</fruit\>  
  \<fruit\>Cherry\</fruit\>  
\</fruits\>  
\`\`\`  
\<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0"\>  
  \<xsl:output method="text"/\>  
  \<xsl:template match="/"\>  
    \[  
    \<xsl:for-each select="fruits/fruit"\>  
      "\<xsl:value-of select="."/\>"\<xsl:if test="position()\!=last()"\>, \</xsl:if\>  
    \</xsl:for-each\>  
    \]  
  \</xsl:template\>  
\</xsl:stylesheet\>

Salida:

\`\`\`json  
\[  
  "Apple",  
  "Banana",  
  "Cherry"  
\]  
\`\`\`

\_\_Ejercicio 7\_\_. Crear un fichero JSON con los productos y sus respectivos precios.

XML de entrada:

\`\`\`xml  
\<products\>  
  \<product\>  
    \<name\>Laptop\</name\>  
    \<price\>1000\</price\>  
  \</product\>  
  \<product\>  
    \<name\>Mouse\</name\>  
    \<price\>25\</price\>  
  \</product\>  
\</products\>  
\`\`\`  
\<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0"\>  
  \<xsl:output method="text"/\>  
  \<xsl:template match="/"\>  
    \[  
    \<xsl:for-each select="products/product"\>  
      {  
        "name": "\<xsl:value-of select="name"/\>",  
        "price": \<xsl:value-of select="price"/\>  
      }\<xsl:if test="position()\!=last()"\>, \</xsl:if\>  
    \</xsl:for-each\>  
    \]  
  \</xsl:template\>  
\</xsl:stylesheet\>

Salida:

\`\`\`json  
\[  
  {  
    "name": "Laptop",  
    "price": 1000  
  },  
  {  
    "name": "Mouse",  
    "price": 25  
  }  
\]  
\`\`\`

\_\_Ejercicio 8\_\_. Crear un Objeto JSON con los nombres de usuarios.

XML de entrada:

\`\`\`xml  
\<users\>  
  \<user\>  
    \<id\>1\</id\>  
    \<name\>John Doe\</name\>  
    \<email\>john@example.com\</email\>  
  \</user\>  
  \<user\>  
    \<id\>2\</id\>  
    \<name\>Jane Smith\</name\>  
    \<email\>jane@example.com\</email\>  
  \</user\>  
\</users\>  
\`\`\`  
\<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0"\>  
  \<xsl:output method="text"/\>  
  \<xsl:template match="/"\>  
    \[  
    \<xsl:for-each select="users/user"\>  
      {  
        "id": "\<xsl:value-of select="id"/\>",  
        "name": "\<xsl:value-of select="name"/\>",  
        "email": "\<xsl:value-of select="email"/\>"  
      }\<xsl:if test="position()\!=last()"\>, \</xsl:if\>  
    \</xsl:for-each\>  
    \]  
  \</xsl:template\>  
\</xsl:stylesheet\>

Salida: 

\`\`\`json  
\[  
  {  
    "id": "1",  
    "name": "John Doe",  
    "email": "john@example.com"  
  },  
  {  
    "id": "2",  
    "name": "Jane Smith",  
    "email": "jane@example.com"  
  }  
\]  
\`\`\`

\_\_Ejercicio 9\_\_. Crear un fichero JSON con las categorías y los productos:

XML de entrada:

\`\`\`xml  
\<store\>  
  \<category name="Electronics"\>  
    \<product\>  
      \<name\>Laptop\</name\>  
      \<price\>1000\</price\>  
    \</product\>  
    \<product\>  
      \<name\>Smartphone\</name\>  
      \<price\>700\</price\>  
    \</product\>  
  \</category\>  
  \<category name="Books"\>  
    \<product\>  
      \<name\>1984\</name\>  
      \<price\>15.99\</price\>  
    \</product\>  
    \<product\>  
      \<name\>Brave New World\</name\>  
      \<price\>12.49\</price\>  
    \</product\>  
  \</category\>  
\</store\>  
\`\`\`  
\<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0"\>  
  \<xsl:output method="text"/\>  
  \<xsl:template match="/"\>  
    {  
    \<xsl:for-each select="store/category"\>  
      "\<xsl:value-of select="@name"/\>": \[  
        \<xsl:for-each select="product"\>  
          {  
            "name": "\<xsl:value-of select="name"/\>",  
            "price": \<xsl:value-of select="price"/\>  
          }\<xsl:if test="position()\!=last()"\>, \</xsl:if\>  
        \</xsl:for-each\>  
      \]\<xsl:if test="position()\!=last()"\>, \</xsl:if\>  
    \</xsl:for-each\>  
    }  
  \</xsl:template\>  
\</xsl:stylesheet\>

Salida: 

\`\`\`json  
{  
  "Electronics": \[  
    {  
      "name": "Laptop",  
      "price": 1000  
    },  
    {  
      "name": "Smartphone",  
      "price": 700  
    }  
  \],  
  "Books": \[  
    {  
      "name": "1984",  
      "price": 15.99  
    },  
    {  
      "name": "Brave New World",  
      "price": 12.49  
    }  
  \]  
}  
\`\`\`

\_\_Ejercicio 10\_\_. Crear un fichero JSON con los titulos de secciones y su contenido.

XML de entrada:

\`\`\`xml  
\<document\>  
  \<section\>  
    \<title\>Introduction\</title\>  
    \<content\>Welcome to this tutorial.\</content\>  
  \</section\>  
  \<section\>  
    \<title\>Chapter 1\</title\>  
    \<content\>This is the first chapter.\</content\>  
  \</section\>  
\</document\>  
\`\`\`  
\<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0"\>  
  \<xsl:output method="text"/\>  
  \<xsl:template match="/"\>  
    \[  
    \<xsl:for-each select="document/section"\>  
      {  
        "title": "\<xsl:value-of select="title"/\>",  
        "content": "\<xsl:value-of select="content"/\>"  
      }\<xsl:if test="position()\!=last()"\>, \</xsl:if\>  
    \</xsl:for-each\>  
    \]  
  \</xsl:template\>  
\</xsl:stylesheet\>

Salida: 

\`\`\`json  
\[  
  {  
    "title": "Introduction",  
    "content": "Welcome to this tutorial."  
  },  
  {  
    "title": "Chapter 1",  
    "content": "This is the first chapter."  
  }  
\]  
\`\`\`  
