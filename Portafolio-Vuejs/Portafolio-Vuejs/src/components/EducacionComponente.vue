
<script setup>
import { ref } from 'vue';
const fechacolor = ref ([]);
fechacolor.value= [
    {color: "#41516c"},
    {color: "#707070"},
    {color: "#E24A68"},
    {color: "#1B5F8C"},
    {color: "#4CADAD"}
];
const educacion = ref ([]);
educacion.value = [
    {fecha: "2024", title: "Técnicatura Universitaria en Programacion", descripcion: "Incumbencias Profecionales: Operacion y programacion de computadoras, desarrollo de programa en distintos lenguajes, analisis y control de sistema informaticos", enlace:"https://www.youtube.com/"},
    {fecha: "2023", title:"Desarrollador full Stack", descripcion:"Trabaje en XYZ tech, donde diseñe y desarrollé aplicaciones web ", enlace: "http:www.direccion.com"},
   
]
</script>

<template>
    <ul>
        <li v-for="(item, index) in educacion" :key="index" :style="{'--fecha-color': fechacolor[index].color}">
            <div class="fecha">{{ item.fecha }}</div>
            <h3 class="title">{{ item.title }}</h3>
            <div class="descripcion">{{ item.descripcion }}</div>
            <!--Aqui vemos en el uso de b-vind (:) que bindeamos el atributo href de html en el item.enlace-->
            <a class="enlace" :href="item.enlace" target="_blank">saber más</a>
        </li>
    </ul>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Doto:wght@400;700&display=swap');

.fecha{
    font-family: 'Doto', sans-serif;
}
.title{
    font-family: 'Doto', sans-serif;
    font-size: 1.6rem;
    font-weight: 800;
}
/*Estilos generales*/
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap");
/*Reseteo de estilos basicos para todos los elementos y pseudo-elementos*/
*,
*::before,
*::after{
    margin: 0; /*Elimina el margen predeterminado */
    padding: 0; /*Elimina padding predeterminado*/
    box-sizing: border-box; /* Incluye el padding y el borde en el tamaño total del elemento*/
}
/* Estilo para el cuerpo de la página */
body {
    --color: rgba(30, 30, 30); /* Variable para el color de texto */
    --bgcolor: rgba(245, 245, 245); /* Variable para el color de fondo */
    min-height: 100vh; /*Asegura que el cuerpo ocupe al menoos el 100% de la altura de la vnetana */
    display:  grid; /* Uyiliza el modelo de caja de cuadricula */
    align-content: center; /* centra verticalmente el contenido dentro de la cuadricula */
    gap: 2rem; /* Espacio interno alrededor del cuerpo */
    font-family: "Poppins", sans-serif; /* Fuente para todo el texto en la pagina */
    color: var(--color); /* Aplica el color de texto definido en la variable */
    background: var(--bgcolor); /* Aplica el color de fondo definido en la variable */
}

/*Estilo apra la lista */
ul {
    margin-top: 2rem;
    --col-gap: 2rem; /* Espacio entre las columnas de la cuadricula */
    --row-gap: 2rem; /* Espacio entre la filas de la c uadricula */
    --line-w: 0.25rem; /* Ancho de la línea que conecta los elementos de la lista  */
    display: grid; /* Usa un leyout de caudricula */
    grid-template-columns: var(--line-w) 1fr; /* Define la culumna de la cuadricula: la primera es la linea y la segunda es el contenido */
    grid-auto-columns: max-content; /* Las columnas se ajustan automaticamente al contenido */
    column-gap: var(--col-gap); /* Espacio entre la columnas */
    list-style: none; /* Elimina las viñetas predeterminadas de la lista */
    width: min(60rem, 90%); /* Limita el ancho de la lista al mínimo entre 60 rem y el 90% del ancho de la ventana */
    margin-inline: auto; /* Centra la lista horizontalmente */
}

/* Estilo para la linea vertical de conecta los elemento de la lista */
ul::before {
    content: ""; /* Elemnto vacío para crear la linea */
    grid-column: 1; /* coloca la línea en la primera columna de la cuadricula */
    grid-row: 1/ span 20; /* La linea se extiende sobre varias filas */
    background: rgb(225, 225, 225); /* Color de la línea */
    border-radius: calc(var(--line-w) / 2); /* Bordes redondeador para la linea */
}

/* Estilo para los elementos de la lista que no son el último */
ul li:not(:last-child) {
    margin-bottom: var(--row-gap); /* Espacio entre los elementos de la lista */
}

/* Estilo apra cada ítem de la lista */
ul li {
    grid-column: 2; /* Coloca el contenido en la segunda columna de la cuadricula */
    --inlineP: 1.5rem; /* Espacio enterno horizonatal dentro de cada ítem */
    margin-inline: var(--inlineP); /* Margen horizontal para los ítems */
    grid-row: span 2; /* Cada ítem ocupa dos filas en la cuadricula */
    display: grid; /* Usa un leyout de cuadriculas dentro de cada ítem */
    grid-template-rows: min-content min-content min-content; /* Define tres filas de altura mínima */
}

/* Estilo para la fecha dentro de cada ítem */
ul li .fecha {
    --dateH: 3rem; /* Altura de la sección de la fecha */
    height: var(--dateH); /* Aplica la altura definida */
    margin-inline:  calc(var(--inlineP) * -1); /* Ajusta el margen horizontal para que la fecha sobresalga */
    text-align: center; /* Centra el texto dentro de la fecha */
    background-color:  var(--fecha-color); /* Color de fondo, usando una variable personalizada */
    color: white; /* Colo del texto en la decha */
    font-size: 1.25rem; /* Tamaño del texto */
    font-weight: 700; /* Hace el texto en negrita */
    display: grid; /* Usa un layout de cuadricula */
    place-content: center; /* Centra el contenido de la fecha */
    position: relative; /* Posicíona la fecha relativa a su contenedor */
    border-radius: calc(var(--dateH) / 2) 0 0 calc(var(--dateH) / 2); /* Bondes redondos para la fecha */
}

/* Estilo para la parte inferior de la fecha, que parece un triángulo */
ul li .fecha::before {
    content: ""; /* Elemento vacío para crear el triángul*/
    width: var(--inlineP); /* Ancho igual al espacio interno definido */
    aspect-ratio: 1; /* Mantiene una relación de aspecto 1:1 para crerar un cuadrado */
    background: var(--fecha-color); /* Usa el color de fondo de la fecha */
    background-image: linear-gradient(rgba(0, 0, 0, 0.2) 100%, transparent); /* Aplica un degradado sutil para dar un efecto de sombra */
    position: absolute; /* Posicion el triángulo respecto al contenedor de la fecha */
    top: 100%; /* Coloca el triángulo justo debajo de la fecha */
    clip-path: polygon(0 0,100% 0, 0 100%); /* Recorta el cuadrado para convertirlo en un triángulo */
    right: 0; /* Alinea el triángulo a la derecha */
}

/* Estilo para el circulo que coencta la fecha con la línea */
ul li.fecha::after {
    content: ""; /* Elemento vacío para crear el círculo */
    position: absolute; /* Posicíona el círculo respecto al contenedor de la fecha */
    width: 1rem; /* Ancho del círculo */
    aspect-ratio: 1; /* Matiene una relación de aspecto 1:1 para crear un círculo */
    background: var(--bgcolor); /* Colo de fondo, utilizando la variable definida */
    border: 0.3rem solid var(--fecha-color); /* Borde del círculom con el color de la fecha */
    border-radius: 50%; /* Hace que el elemento sea un círculo perfecto */
    top: 50%; /* Centra verticalmente el círculo dnetro del contenedor de la fecha */
    transform: translate(50%, -50%); /* Ajusta la posición del círculo para alínearlo correctamente */
    right: calc(100% + var(--col-gap) + var(--line-w) / 2); /* Colo el círculo a la izquierda de la línea */
}

/* Estilos para el título y la descripcion dentro de cada ítem */
ul li .title,
ul li .descripcion {
    background: var(--bgcolor); /* Fondo del título y la descripcion, usando la variable definida */
    position: relative; /* Posiciona los elementos relativos a su contenedor */
    padding-inline: 1.5rem; /* Espaciado interno horizontal */
}

ul li .title {
    overflow: hidden; /* Oculta cualquier contenido que se desborde */
    padding-block-start: 1.5rem; /* Espaciado interno superior */
    padding-block-end: 1rem; /* Espaciado interno inferior */
    font-weight: 500; /* Hace el texto del titulo un poco más grueso */
}

ul li .descripcion {
    padding-block-end: 1.5rem; /* Espaciado interno inferior */
    font-weight: 300; /* Hace el texto de la descripcion más degado */
}

/* Estilos para las sombras debajo del título y la decripción */
ul li .title::before,
ul li .descripcion::before {
    content: ""; /* Elemento vacío para crear la sombra */
    position: absolute; /* posiciona la sombra resprecto al contenedor del título o decripcion */
    width: 90%; /* Ancho de la sombra */
    height: 0.5rem; /* Altura de la sombra */
    background: rgba(0, 0, 0, 0.5); /* Color de ofndo oscuro para simular una sombra */
    left: 50%; /* Centra la sombra horizontalmente */
    border-radius: 50%; /* Bordes redondeador para la sombra */
    filter: blur(4px); /* Aplica un enfoque para hacer la sombra más suave */
    transform: translate(-50%, 50%); /* Ajusta la posicion para centrar la sombra */
}

ul li .title::before {
    bottom: calc(100% + 0.125rem); /* coloca la sombra debajo del título */
}

ul li .descripcion::before {
    z-index: -1; /* Coloca la sombra detrás del contenido */
    bottom: 0.25rem; /* Coloca la sombra justo */
}

/* Media query para pantalla anchas (40rem o mas) */
@media (min-width: 40rem) {
    ul {
        grid-template-columns: 1fr var(--line-w); /* Ajusta la cuadricula para tener tres columnas */
    }
    ul::before {
        grid-column: 2; /* Mueve la linea verticalmente a la segunda de la cuadricula */
    }
    ul li:nth-child(odd) {
        grid-column: 1; /* Coloca los ítems impares a la primera columna */
    }
    ul li:nth-child(even) {
        grid-column: 3; /* Coloca los ítems pares en la tercera columna */
    }

    /* Ajuste para que el segundo ítem abarque dos filas */
    ul li:nth-child(2) {
        grid-row: 2/4; /* El segundo item ocupará desde la segunda hasta la cuarta fila */
    }
    /* Ajustes especificos para los ítems impares */
    ul li:nth-child(odd) .fecha::before {
        clip-path: polygon(0 0, 100% 0, 100% 100%); /* Invierte el triángulo en los ítems impares */
        left: 0; /* Alinia el triángulo a la izquierda */
    }

    ul li:nth-child(odd) .fecha::after {
        transform: translate(-50%, -50%); /* Ajusta la posicion del circulo en los pitems impares */
        left: calc(100% + var(--col-gap) + var(--line-w) / 2); /* Coloca círculo a la derecha de la línea */
    }

    ul li:nth-child(odd) .fecha {
        border-radius: 0 calc(var(--dateH) / 2) calc(var(--dateH) / 2) 0; /* Ajusta los bordes redondeados para los ítems impares */
    }

    
}

/* Estilos par los créditos */
.credits {
    margin-top: 1rem; /* Espaciodo superios para los créditos */
    text-align: right; /* Alinea el texto de los creditos a la derecha */
}

.credits a {
    color: var(--color); /* Aplica el color de texto definido en la variable */
}
</style>