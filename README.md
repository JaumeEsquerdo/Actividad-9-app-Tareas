# Actividad-9-app-Tareas

Aquí el código original que pasan de la tarea:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ToDo List</title>
</head>
<body>
    <h1>Lista de Tareas</h1>

    <div>
        <ul id="listaTareas">
            <li>Ingrese tareas en su lista...</li>
            <!-- <li>Tarea 1</li>
            <li>Tarea 2</li> -->
        </ul>
    </div>

    <form id="formTarea">
        <input id="txtTarea" type="text" name="tuTarea" placeholder="Ingrese una tarea" >
        <button type="submit">Agregar Tarea</button>
    </form>


    <script>
        // -----------------------------------------------
        // 0. Comentarios y documentación
        // -----------------------------------------------
        /* 
            Vamos a realizar un ToDo List para prácticar el uso de Objetos y Arrays.
            Link al manual: 
            Autor: El profe Tomi.
        */

        // -----------------------------------------------
        // 1. Constantes y Variables
        // -----------------------------------------------
        const formu = document.getElementById("formTarea");
        const txtTarea = document.getElementById("txtTarea");
        const boxTareas = document.getElementById("listaTareas");

        //const listaDeTareas = ["Ordenar el código JS", "Crear las Funciones", "Probar el programa"];

        const listaDeTareas = [
                { id: 1,    titulo: "Ordenar el código JS", isCompletada: true  },
                { id: 524,  titulo: "Crear las Funciones",  isCompletada: false },
                { id: 1056, titulo: "Probar el programa",   isCompletada: false }
        ];


        // -----------------------------------------------
        // 2. Funciones utilitarias (reutilizables)
        //      * esto también se suele hacer en un archivo aparte por ej: utils.js
        // -----------------------------------------------


        // -----------------------------------------------
        // 3. Funciones principales de nuestra web/programa/app
        // -----------------------------------------------
        function mostrarTareas(){

            // borrar todo el contenido de la caja antes de mostrar
            boxTareas.innerHTML = "";

            // cargamos las nuevas tareas
            listaDeTareas.forEach( (tarea)=> {
                console.log("Tarea es: ", tarea);
                // { id: 1,  titulo: "Ordenar el código JS", isCompletada: true  },

                const titulo = tarea.titulo;
                const id = tarea.id;

                // convertir esta linea para que isChecked sea igual a "checked" o a  ""
                const isChecked = tarea.isCompletada ? "checked" : "";

                // if(tarea.isCompletada){
                //     isChecked = "checked";
                // } else {
                //     isChecked = "";
                // }


                // boxTareas.innerHTML += `<li>${id} ${titulo}</li>`;
                boxTareas.innerHTML += `
                <li>
                    <input type="checkbox" id="${id}" name="chk_completada" ${isChecked} />
                    <label for="${id}">${titulo}</label>
                    <button onclick="eliminarTarea(${id})">X</button>
                    <button onclick="completarTarea(${id})">Completar</button>
                </li>
                `;
            });
        }

        function agregarTarea(){
            const nuevaTarea = txtTarea.value.trim(); // el texto del input
            console.log(nuevaTarea);

            // Tarea inválida (hacemos un return)
            if( nuevaTarea == ""){ 
                alert("Por Favor, ingresa una tarea válida"); 
                return; 
            } 
            
            // Tarea válida
            txtTarea.value = ""; // limpiar mi input
            listaDeTareas.push(nuevaTarea); // push() es para agregar nuevo item a la lista
            mostrarTareas();
        }

        function eliminarTarea(idTarea){
            alert("Eliminar tarea: "+idTarea);
            // Modificar mi lista, y eliminar la tarea idTarea

            mostrarTareas();
        }

        function completarTarea(idTarea){
            alert("Completando tarea: "+ idTarea);
            // modificar mi lista, y cambiar el booleano de true a false, o de false a true en la tarea específica
            
            mostrarTareas();
        }

        // -----------------------------------------------
        // 4. EventListeners
        // -----------------------------------------------

        // escuchamos al evento cuando se envía
        formu.addEventListener("submit", (event) => {
            // NO envíes el formulario porque quiero hacer cosas antes
            event.preventDefault();
            agregarTarea();
        });



        // -----------------------------------------------
        // 5. Inicializar nuestro programa
        // -----------------------------------------------

        mostrarTareas();

    </script>
</body>
</html>

```