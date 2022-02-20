# bid_data_2-taller-1-1

### **Point 2:**
- Data Dictionary:
  - app_user - shoping_cart relationship: permite asociar cada compra a un usuario único por medio de su identificador (número de documento).
  - shoping_cart - bill relationship: permite asociar una factura a uno o varios productos y al usuario que realizó el pago.
  - shoping_car - product: asocia cada producto a una intención de compra, que a su vez lo vincula al usuario que realizá dicha compra.
  - variant table: hace referencia a las variantes que tiene un producto, cada producto se asocio a una o muchas variantes, mientras que una variante se asocia a un solo producto, dado que estas variantes son únicas por productos (independientemente de que sean el mismo producto)

### **Point 3:**
- ¿Las vistas que decide crear a qué requerimiento no funcional obedecen? Seguridad o facilidad de consulta. ¿Deberían ser vistas materializadas? Argumente:
  - la primer vista, shopping_cart_state permite idenficiar el estado de los carritos de compras que fueron cancelados y poder ver que productos estabán en dicho carrito y que usuarios crearon dicho carrito, esto puede permitir identificar que productos son 'rechazados' o dejados con más frecuencia o que clientes tienden a cancelar sus compras para tomar medidas que permitan disminuir este tipo de comportamiendos, además brinda la facilidad de consulta para los administradores, como esta consulta dependerá de la cantidad de compras que se realizan por mes o día inicialmente se considerará crear la vista como no materializada.
  - la segunda vista, calification_user permite visualizar la calificación que tienen los usuarios de tipo 'proveedor' para así tomar la decisión de bloquearles la cuenta, con el fin de facilitar la consulta, se considera que debe ser una vista materializada dado que puede llegar a ser una consulta frecuente dependiendo de la cantidad de compras que se realizen por més o día.
- ¿Cuáles consultas a la base de datos, a partir de los requerimientos dados, pueden optimizarse mediante índices? ¿De qué tipos deben ser dichos índices? Argumente.
  - el primer indice, city_index, permite optimizar los tiempos de busqueda que se refieran a ciudades, esto con el fin de permite mayor agilidad a la hora de buscar nuevas bodegas en ciudades donde se realizan varios pedidos, con el fin de optimizar los tiempos de entre, como la tabla ciudades, una vez creada es poco probable que cambie, se utiliza un índice con función hash dada la ventaja que este dá en cuanto a tiempos de busqueda.
  - el segundo índice, calification_index, permite optimizar, por medio de un índice b+-tree, el tiempo de consulta donde la calificación de los usuarios sea deficiente o positiva para tomar decisiones frente si bloquear la cuenta a dicho o usuario o no.
  - el tercer índice, user_index, permite optimizar los tiempos de busqueda de usuarios, se plante que el indice sea una función hash dada su eficiencia en tiempos de consulta a pesar de significar un aumento en memoria, dado que se considera poder realizar las busquedas de usuario de manera efectiva para que los administradores puedan acceder a estas sin tiempos de demora largos.
