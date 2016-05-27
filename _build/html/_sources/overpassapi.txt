.. Overpass API


Overpass API
============

Overpass API permite hacer consultas a la base de datos de OSM por distintos criterios de búsqueda. Tiene su propio lenguaje. El flujo de datos funciona a modo de tubería, el resultado de cada operación se envía al siguiente comando que lo procesa y vuelve a envíar al siguiente, y así sucesivamente.

El portal de Overpass-API ofrece información acerca del lenguaje yotras herramientas que seponen a disposición. La dirección del portal es: `http://overpass-api.de/index.html <http://overpass-api.de/index.html>`_

Las sentencias de Overpass API las podemos probar en el siguiente portal::
   `http://overpass-api.de/query_form.html <http://overpass-api.de/query_form.html>`_. 

En este portal podemos obtener ademas las salidas como programa OpenLayers.

También podemos probarlas y ver la salida gráfica en el portal::

  http://overpass-turbo.eu/#

También podemos utilizar el comando linux *wget* con la siguiente estrutura::

  wget -O file.osm "http://overpass-api.de/api/interpreter?data=sentencia_overpass_api"

Mediante peticiones GET o POST, podemos realizar las consultas desde cualquier lenguaje de programación.

El siguiente ejemplo es una query que genera un flujo de datos con todos los *Nodes* contenidos en un determinado *bounding box* y los envía a la salida estándar::

  node(41.9837,2.8243,41.9866,2.8307);out;

Veamos otro ejemplo. Vamos a filtrar los datos de la sentencia anterior de modo que nos quedemos solo con los nodos que tienen determinado valor en una etiqueta,por ejemplo, los nodos con la etiqueta *amenity=restaurant*::

  node(41.9837,2.8243,41.9866,2.8307)[amenity=restaurant];out;

El bounding box se especifica como: (minLat, minLon, maxLat, maxLon).

Otro ejemplo en el que solicitamos un Node con un Id determinado::

  node(4129698657);out;

También podríamos pedir los Nodes que se encuentran a una determinada distancia de un punto de coordenadas conocidas:

  node(around:100.0,41.9837,2.8243);out;

Podemos hacer la unión de dos queries poniéndolas entre paréntesis y separadas por ';'. Por ejemplo, la siguiente sentencia solicita los Nodes con 'amenity=restaurant' o 'amenity=pub'::

  (node(41.9837,2.8243,41.9866,2.8307)[amenity=restaurant];node(41.9837,2.8243,41.9866,2.8307)[amenity=pub]);out;

Hay multitud de combinaciones que permiten hacer todo tipo de consultas selectivas. Se puede consultar la documentación completa del lenguaje en el siguiente enlace:

`http://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_QL#By_element_id <http://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_QL#By_element_id>`_








