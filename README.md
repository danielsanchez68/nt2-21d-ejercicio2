# nt2-21d-ejercicio2
//Profe, no se porque no puedo pushear.. le copio el nuevo codigo del INDEX.html

<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>Ejemplo 1</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css"
        integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.min.js"></script>

</head>


<div class="container-fluid mt-3" id="app">
    <input type="text" class="form-control" v-model="nombreYApellido"
     placeholder="Ingresar nombre y apellido">
     
     <br>
     <input type="text" class="form-control" v-model="dniBuscado"
     placeholder="Ingresar dni">
     <br>

     <p v-if="calcCaracteres.cumple" class="alert alert-warning">
        Debe ingresar 3 carácteres.
    </p>
    <div class="container-fluid mt-3" id="app">
        <div class="card-deck m-0">
            <div class="row">
                <div class="col" v-for="persona in busqueda">
                    <div class="card mb-3">
                        <div class="card-body">
                            <h5 class="card-title">{{getNombreCompleto(persona)}}</h5>
                            <p class="card-text">dni {{persona.dni}}</p>
                            <a href="#" class="card-link">{{persona.correo}}</a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        
        
    </div>

</html>

<script>
    new Vue({
        el: '#app',
        data: {
            nombreYApellido: '',
            dniBuscado: '',
        
            //Aquí, en este array es donde tienen que agregar su información
            personas: [
                {
                    nombre: "Daniel",
                    apellido: "Sanchez",
                    correo: "danielsanchez68@hotmail.com",
                    dni: "20442873"
                },
                {
                    nombre: "Emanuel",
                    apellido: "Caputo",
                    correo: "e.caputoblason@gmail.com",
                    dni: "38916570"
                },
                {
                    nombre: "Francisco",
                    apellido: "Rolon",
                    correo: "f.rolon@gmail.com",
                    dni: "35687145"
                },
            ]

        },
        computed: {
            busqueda() {
                return this.personas.filter((persona) => {
                    let registroCompleto = `${persona.nombre} ${persona.apellido} ${persona.dni} ${persona.correo}`
                    return registroCompleto.toLowerCase().includes(this.nombreYApellido.toLowerCase() || this.dniBuscado)
                });
            
            },
            calcCaracteres(){
               let cantDniBuscado = this.dniBuscado.length
               let cantNombreYApellido = this.nombreYApellido.length
               let total = cantDniBuscado + cantNombreYApellido
                return {
                    cumple: total < 3
                }
            
            
        }

        },
        methods: {
            getNombreCompleto(persona) {
                return `${persona.nombre} ${persona.apellido}`
            }
            
        }
        
    });

    
</script>
