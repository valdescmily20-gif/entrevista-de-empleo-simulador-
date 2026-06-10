# entrevista-de-empleo-simulador-
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Simulador de Entrevistas</title>

<style>
body{
    font-family: Arial, sans-serif;
    background:#f2f5f7;
    margin:0;
}

header{
    background:#1565c0;
    color:white;
    text-align:center;
    padding:20px;
}

.container{
    width:90%;
    max-width:900px;
    margin:20px auto;
    background:white;
    padding:20px;
    border-radius:10px;
    box-shadow:0 0 10px rgba(0,0,0,.2);
}

input, select, textarea{
    width:100%;
    padding:10px;
    margin:10px 0;
    border:1px solid #ccc;
    border-radius:5px;
}

button{
    background:#1565c0;
    color:white;
    border:none;
    padding:12px 20px;
    border-radius:5px;
    cursor:pointer;
}

button:hover{
    background:#0d47a1;
}

.pregunta{
    margin-bottom:20px;
}

#resultado{
    margin-top:20px;
    padding:15px;
    background:#e8f5e9;
    display:none;
    border-radius:5px;
}
</style>
</head>
<body>

<header>
<h1>Simulador de Entrevistas de Empleo</h1>
</header>

<div class="container">

<label>Nombre:</label>
<input type="text" id="nombre">

<label>Selecciona el puesto:</label>
<select id="puesto" onchange="cargarPreguntas()">
<option value="">Seleccione...</option>
<option value="docente">Docente</option>
<option value="administrativo">Administrativo</option>
<option value="ingeniero">Ingeniero</option>
<option value="vendedor">Vendedor</option>
<option value="atencion">Atención al Cliente</option>
</select>

<div id="preguntas"></div>

<button onclick="evaluar()">Finalizar Entrevista</button>

<div id="resultado"></div>

</div>

<script>

const preguntas = {

docente:[
"¿Por qué decidió ser docente?",
"¿Cómo motiva a sus estudiantes?",
"¿Cómo maneja la disciplina en el aula?",
"¿Qué metodología utiliza?",
"¿Cómo evalúa el aprendizaje?",
"¿Cómo trabaja con padres de familia?",
"¿Qué haría con un alumno desmotivado?",
"¿Cómo utiliza la tecnología educativa?",
"¿Cuál es su mayor fortaleza profesional?",
"¿Por qué deberíamos contratarlo?"
],

administrativo:[
"Hábleme de usted.",
"¿Cómo organiza su trabajo?",
"¿Cómo maneja la presión laboral?",
"¿Qué programas de oficina domina?",
"¿Cómo maneja documentos confidenciales?",
"¿Cómo resuelve conflictos?",
"¿Qué experiencia tiene?",
"¿Cómo prioriza tareas?",
"¿Cuál es su mayor logro?",
"¿Por qué desea este empleo?"
],

ingeniero:[
"Describa un proyecto exitoso.",
"¿Cómo resuelve problemas técnicos?",
"¿Qué software domina?",
"¿Cómo trabaja en equipo?",
"¿Cómo maneja plazos ajustados?",
"¿Qué innovación ha propuesto?",
"¿Cómo documenta procesos?",
"¿Cuál es su especialidad?",
"¿Qué habilidades técnicas posee?",
"¿Por qué deberíamos contratarlo?"
],

vendedor:[
"¿Cómo convencería a un cliente?",
"¿Cómo maneja objeciones?",
"¿Qué significa vender para usted?",
"¿Cómo alcanza metas?",
"¿Cómo fideliza clientes?",
"¿Cómo maneja el rechazo?",
"¿Cuál fue su mejor venta?",
"¿Cómo trabaja bajo presión?",
"¿Qué estrategias utiliza?",
"¿Por qué quiere trabajar aquí?"
],

atencion:[
"¿Cómo trata a clientes difíciles?",
"¿Qué es el servicio al cliente?",
"¿Cómo resuelve quejas?",
"¿Cómo maneja el estrés?",
"¿Qué haría con un cliente molesto?",
"¿Cómo se comunica eficazmente?",
"¿Cómo trabaja en equipo?",
"¿Qué experiencia tiene?",
"¿Qué habilidades posee?",
"¿Por qué deberíamos contratarlo?"
]

};

function cargarPreguntas(){

let puesto = document.getElementById("puesto").value;
let contenedor = document.getElementById("preguntas");

contenedor.innerHTML="";

if(!puesto) return;

preguntas[puesto].forEach((pregunta,index)=>{

contenedor.innerHTML += `
<div class="pregunta">
<label>${index+1}. ${pregunta}</label>
<textarea class="respuesta" rows="4"></textarea>
</div>
`;

});

}

function evaluar(){

let respuestas = document.querySelectorAll(".respuesta");

if(respuestas.length===0){
alert("Seleccione un puesto.");
return;
}

let puntaje=0;

respuestas.forEach(r=>{

if(r.value.length>=80){
puntaje+=10;
}
else if(r.value.length>=40){
puntaje+=5;
}

});

let porcentaje = puntaje;

let mensaje="";

if(porcentaje>=80){
mensaje="Excelente preparación para entrevistas.";
}
else if(porcentaje>=60){
mensaje="Buen desempeño, pero puede mejorar.";
}
else{
mensaje="Necesita practicar más sus respuestas.";
}

let resultado = document.getElementById("resultado");

resultado.style.display="block";

resultado.innerHTML=`
<h2>Resultado Final</h2>
<p><strong>Nombre:</strong> ${document.getElementById("nombre").value}</p>
<p><strong>Puesto:</strong> ${document.getElementById("puesto").options[document.getElementById("puesto").selectedIndex].text}</p>
<p><strong>Calificación:</strong> ${porcentaje}%</p>
<p><strong>Evaluación:</strong> ${mensaje}</p>
`;

}

</script>

</body>
</html>
