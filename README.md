<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Random Color Grid</title>
    <!-- Enlace a Google Fonts para cargar una fuente divertida -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Poppins', sans-serif; /* Fuente divertida */
            text-align: center;
            margin: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, #f5d0fe, #b3c4e7, #f0e5a6); /* Fondo pastel */
            background-size: cover;
            position: relative;
            flex-direction: column; /* Asegura que el contenido se apile verticalmente */
        }

        /* Fondo desenfocado */
        .background-blur {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            filter: blur(8px); /* Desenfoque en el fondo */
            z-index: -1; /* Mantenerlo detrás del contenido */
        }

        .container {
            display: grid;
            grid-template-columns: repeat(5, 80px); /* Aumentado el tamaño de los rectángulos */
            grid-gap: 5px;
            justify-content: center;
            margin: 20px auto;
            z-index: 1; /* Asegura que el grid esté por encima del fondo */
        }

        .box {
            width: 80px;  /* Aumentado el ancho del rectángulo */
            height: 60px; /* Mantener la altura del rectángulo */
            border: 2px solid black; /* Contorno negro */
        }

        .black {
            background-color: #808080; /* Gris más saturado */
        }

        .blue {
            background-color: #6ec6e0; /* Azul pastel más saturado */
        }

        .white {
            background-color: #ffffff; /* Blanco puro */
        }

        .red {
            background-color: #f28b82; /* Rojo pastel más saturado */
        }

        h1 {
            font-size: 36px;
            margin-bottom: 10px; /* Espacio entre el título y el botón */
            font-weight: 600; /* Fuente en negrita */
            color: #2e3d49; /* Color más oscuro para el texto */
        }

        button {
            padding: 12px 25px; /* Aumento del tamaño del botón */
            font-size: 18px; /* Aumento del tamaño de la fuente */
            cursor: pointer;
            border: none;
            background-color: #7dd3e8; /* Azul pastel más saturado */
            color: #ffffff;
            border-radius: 8px; /* Bordes redondeados */
            box-shadow: 0 4px 10px rgba(0, 123, 255, 0.3); /* Sombra suave */
            transition: all 0.3s ease; /* Transición suave */
        }

        button:hover {
            background-color: #66c0d8; /* Azul pastel aún más vivo */
            box-shadow: 0 6px 15px rgba(0, 123, 255, 0.4); /* Aumenta la sombra al pasar el cursor */
            transform: translateY(-4px); /* Efecto de desplazamiento hacia arriba */
        }

        button:active {
            background-color: #55a8c7; /* Azul más oscuro al hacer clic */
            transform: translateY(2px); /* Efecto de "presionar" hacia abajo */
            box-shadow: 0 2px 5px rgba(0, 123, 255, 0.2); /* Reduce la sombra al hacer clic */
        }

    </style>
</head>
<body>
    <h1>Genéra tu tablero de Juego</h1>
    <button onclick="generateGrid()">Generar</button>
    <div class="container" id="grid"></div>

    <!-- Fondo desenfocado -->
    <div class="background-blur"></div>

    <script>
        function generateGrid() {
            const gridContainer = document.getElementById('grid');
            gridContainer.innerHTML = ''; // Limpiar el grid anterior

            // Crear un array con los colores según la distribución
            const colors = Array(8).fill('black')
                .concat(Array(8).fill('blue'))
                .concat(Array(8).fill('white'))
                .concat('red');

            // Mezclar los colores de forma aleatoria
            for (let i = colors.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [colors[i], colors[j]] = [colors[j], colors[i]];
            }

            // Crear los 25 rectángulos
            colors.forEach(color => {
                const div = document.createElement('div');
                div.classList.add('box', color);
                gridContainer.appendChild(div);
            });
        }

        // Generar la cuadrícula al cargar la página
        generateGrid();
    </script>
</body>
</html>
