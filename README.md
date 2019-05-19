# AJAX-con-Jquery

[<img src="https://github.com/aledc7/PHP-Certification/blob/master/aledc-logo.png?raw=true">](https://aledc.com)


###### Ejemplo de AJAX con Jquery en donde se consulta a una API y se muestra en una tabla básica.

###### Todo el código está correctamente comentado.





- [x] Ale Dc






```javascript
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
    <title>AJAX usando la funcion $.ajax() de JQuery - AleDC </title>
</head>

<body>

    <button id="boton">Leer Api Andres</button>

    <!-- div principal en donde se dibujara los datos de la API -->
    <div id="lista-api"></div>


    <script>
        // asocia al evento click del boton la funcion leerApi 
        $("#boton").on("click", leerApi);


        function leerApi() {

            $.ajax({
                // guardo dentro de la variable url, la direccion web desde donde se lee la API.
                url: 'http://servicios.sartsoftware.com/api/DialogMessages',

                // si la conexion es exitosa, ejecutará la función "respuesta", definida allí mismo.
                success: function (respuesta) {

                    // imprimo el valor de respuesta en la consola, para debug.
                    console.log(respuesta);

                    // creo una variable "listaAPI y le asigno el DIV que definí arriba, con el "id:lista-api".
                    var listaAPI = $("#lista-api");

                    $.each(respuesta, function (index, elemento) {
                        listaAPI.append(
                            '<div>' +
                            '<p>' + 'Proyecto: ' + elemento.idProject + '<br>' +
                            'Cuenta: ' + elemento.numReceptor + '<br>' +
                            'Actor: ' + elemento.actor + '<br>' +
                            'Fecha y Hora: ' + elemento.time + '</p>' +
                            '<p>' + 'Mensaje: ' + elemento.message + '</p>' +
                            '<br>' + '______________________________________' +
                            '</div>'
                        );
                    });
                }, //fin function respuesta

                error: function () {
                    alert("Hubo un error");
                    console.log("No se ha podido consultar a la API de Andres");
                }

            });
        }
    </script>

</body>

</html>
```
