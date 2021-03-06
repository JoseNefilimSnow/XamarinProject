# *Tienda_Informatica_OldSolutions*
*Aplicación piloto con Xamarin - node - mysql*

Autor
:  *Adán José Gómez Hernández*

Contacto
: AdanJoGoHe@gmail.com

*El objetivo del proyecto será la creación de un sistema de gestión  reparaciones para una tienda física de informática. La aplicación tendrá numerosas funcionalidades relacionadas con reparar productos.*

## Descripción de la idea

El cliente me ha solicitado la creación de un programa para la gestión de reparaciones que realizan en la tienda creando una aplicación que sean capaz de manejar a través del móvil. 

Las reparaciones se realizaran sobre equipos informáticos como ordenadores o servidores.

Cuando un cliente solicite una reparación y haya sido tramitada se le dará un ticket con un numero, este numero a través de la web podrá ver el estado del producto, las reparaciones tendrán varios estados que serán explicados a continuación.

Las reparaciones se podrán crear, donde se le dará un tiempo estimado para la reparación el cual sera genérico de 2 días.

Las reparaciones se podrán posponer, donde se podrá alargar el plazo del tiempo estimado para la reparación en caso de que se complique la reparación.

Las reparaciones se podrán suspender, donde se suspenderá la reparación en caso de que haya sido reparado y nadie lo haya recogido a las 2 semanas.

Las reparaciones se podrán terminar, este caso ocurrirá cuando el producto a reparar haya sido reparado y este listo para entregar, se guardara la fecha de reparación.

Las reparaciones se podrán entregar, el producto ha sido reparado y entregado al cliente se guardara la fecha de entrega.

Las reparaciones se podrán eliminar, el producto ha sido devuelto sin reparar por circunstancias varias.

## Descripción de la aplicación

La aplicación contara con un CRUD desde la aplicación a el servicio web.

El estado **Crear reparación** constara de un create que creara una tupla en la base de datos con los respectivos datos introducidos en la aplicación.

Al crear la reparación el campo estado se pondrá en el **estado** "en proceso" sin ninguna acción por parte del operario.

El estado **posponer reparación** constara de un put que modificara el campo "fecha estimada" que aumentara el plazo de la reparación del producto, el producto se pondra en el **estado** "en proceso" si no lo estaba ya.

El estado **terminar reparación** constara de un put que modificara el campo "fecha de reparación" con la fecha dada por el operador, el estado pasara a "Terminado".

El estado **suspender reparación** constara de un put que modificara el **estado** por "Suspendido".

El estado **reparación terminada** constara de un put del campo "fecha de entrega" por la fecha dada por el operador y el campo **estado** se pondrá en "terminado".

     

# OldSolutions Database

## Especificación

En la base de datos almacenaremos ***CLIENTE***, el ***cliente*** *compra* ***reparacion***. El cliente sera almacenado por cada reparación prestada y contendrá un **nombre**, en caso de no ser dado por alguna razón se le pondrá "cliente físico", también tendremos un **telefono_contacto** donde almacenaremos el teléfono del cliente en caso de ser dado y un **id_cliente**.

También almacenaremos el ***OPERADOR***, el ***operador*** *realiza* ***reparación***. El operador tendrá un, **nombre** un **apellido**, un **dni** y un **id_operador**.

***PRODUCTO***, el ***producto*** es *utilizado* en ***reparacion***,  almacenaremos el **nombre** del producto, una **descripcion** del mismo y una **id_producto**. También existirán productos específicos que heredaran de esta tabla los cuales son: 

 - ***CPU_FAN*** : **socket**, **tipo** e **id_cpu_fan**
 - ***GPU*** : **memoria**, **fec_reloj** e **id_gpu**
 - ***CPU*** : **socket**, **fec_reloj** e  **id_cpu**
 - ***RAM*** : **capacidad_memoria** , **velocidad_memoria**, **tipo_memoria** e **id_memoria**
 - ***PSU*** : **energia** e **id_psu**
 - ***PLACA_BASE*** : **socket**,**chipset** e **id_placa_base**.

De la ***REPARACION*** guardaremos **estado** de la reparación que estará limitado a 5 estados que serán "En proceso","Reparado","Entregado", "Suspendido" y "Detenida", **descripcion** que puede ser la idea aproximada del problema, **fecha_estimada** que sera por defecto dos días después de recoger el pedido aunque puede ser aplazada manualmente por un operador, **fecha_reparacion** que sera la fecha en la que se ha reparado el producto. **fecha_entrega** que sera la fecha en la que se ha entregado e **id_reparacion**.
  


## Diagrama entidad relación
<img src="https://i.imgur.com/wg27Re6.png" alt="hola" style="float: left; margin-right: 100px; 
width: 850px; height: 700px; "/>
[Link a la imagen](https://i.imgur.com/wg27Re6.png).

## Diagrama Entidad-Relación físico
<img src="https://i.imgur.com/paGlP24.png" alt="hola" style="float: left; margin-right: 100px; 
width: 950px; height: 700px; "/>
[Link a la imagen](https://i.imgur.com/paGlP24.png)




