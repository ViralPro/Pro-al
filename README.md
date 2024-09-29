
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Generador de Contraseñas Avanzado - ViralPro</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        :root {
            --primary-color: #00c3ff;
            --secondary-color: #ff6b6b;
            --tertiary-color: #4caf50;
            --background-color: #1a1a1a;
            --text-color: #e0e0e0;
            --highlight-color: #ffeb3b;
        }

        body {
            font-family: 'Arial', sans-serif;
            background-color: var(--background-color);
            color: var(--text-color);
            margin: 0;
            padding: 0;
            transition: background-color 0.3s ease;
        }

        .encabezado {
            background: linear-gradient(45deg, var(--primary-color), var(--secondary-color), var(--tertiary-color));
            color: white;
            padding: 20px;
            text-align: center;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
        }

        .contenedor {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            box-shadow: 0 0 30px rgba(0, 0, 0, 0.5);
            padding: 30px;
            text-align: center;
            max-width: 800px;
            width: 90%;
            margin: 50px auto;
            backdrop-filter: blur(15px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        h1, h2 {
            color: var(--primary-color);
            margin-bottom: 20px;
            font-size: 2.5em;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }

        .opciones {
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
            margin-bottom: 20px;
        }

        .opcion {
            margin: 10px;
        }

        label {
            font-weight: bold;
            display: block;
            margin-bottom: 10px;
            color: var(--highlight-color);
        }

        input[type="number"], input[type="range"], select {
            width: 150px;
            padding: 10px;
            border-radius: 5px;
            border: 1px solid var(--primary-color);
            margin-bottom: 10px;
            font-size: 1em;
            text-align: center;
            background-color: #2b2b2b;
            color: var(--text-color);
        }

        button {
            background-color: var(--primary-color);
            color: white;
            padding: 12px 24px;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-size: 1.1em;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
            margin: 10px;
        }

        button:hover {
            background-color: var(--secondary-color);
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.4);
        }

        #contraseña {
            margin-top: 20px;
            font-weight: bold;
            color: var(--highlight-color);
            font-size: 1.5em;
            background: rgba(255, 255, 255, 0.1);
            padding: 15px;
            border-radius: 10px;
            word-break: break-all;
        }

        .fortaleza {
            margin-top: 20px;
            font-size: 1.2em;
        }

        #fortalezaIndicador {
            width: 100%;
            height: 10px;
            background-color: #ddd;
            border-radius: 5px;
            margin-top: 10px;
        }

        #fortalezaIndicador div {
            height: 100%;
            border-radius: 5px;
            transition: width 0.5s ease-in-out;
        }

        .tema-toggle {
            position: fixed;
            top: 20px;
            right: 20px;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            font-size: 1.5em;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
        }

        .tema-toggle:hover {
            transform: rotate(180deg);
            background-color: var(--secondary-color);
        }

        .dark-theme {
            --background-color: #121212;
            --text-color: #ffffff;
        }

        .empresa-info {
            background-color: rgba(255, 255, 255, 0.1);
            padding: 20px;
            border-radius: 10px;
            margin-top: 30px;
        }

        .empresa-info h2 {
            color: var(--tertiary-color);
        }

        @media (max-width: 600px) {
            .contenedor {
                width: 95%;
                padding: 20px;
            }

            .opciones {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <button class="tema-toggle" onclick="cambiarTema()"><i class="fas fa-adjust"></i></button>

    <div class="encabezado">
        <h2>ViralPro</h2>
        <p>Servicios Líderes en Generación Remota de Contraseñas y Ciberseguridad</p>
    </div>

    <div class="contenedor">
        <h1>Generador de Contraseñas Avanzado</h1>
        <div class="opciones">
            <div class="opcion">
                <label for="longitud">Longitud de la contraseña:</label>
                <input type="range" id="longitud" name="longitud" min="4" max="50" value="12" oninput="actualizarLongitud()">
                <span id="longitudValor">12</span>
            </div>
            <div class="opcion">
                <label for="complejidad">Nivel de Complejidad:</label>
                <select id="complejidad">
                    <option value="bajo">Bajo (Solo letras)</option>
                    <option value="medio">Medio (Letras y números)</option>
                    <option value="alto" selected>Alto (Letras, números y símbolos)</option>
                    <option value="personalizado">Personalizado</option>
                </select>
            </div>
        </div>
        <div id="opcionesPersonalizadas" style="display: none;">
            <label><input type="checkbox" id="incluirMayusculas" checked> Mayúsculas</label>
            <label><input type="checkbox" id="incluirMinusculas" checked> Minúsculas</label>
            <label><input type="checkbox" id="incluirNumeros" checked> Números</label>
            <label><input type="checkbox" id="incluirSimbolos" checked> Símbolos</label>
        </div>
        <button onclick="generarContraseña()">Generar Contraseña</button>
        <div id="contraseña"></div>
        <button onclick="copiarContraseña()">Copiar Contraseña</button>
        <div class="fortaleza">
            <p>Fortaleza de la contraseña: <span id="fortalezaTexto"></span></p>
            <div id="fortalezaIndicador"><div></div></div>
        </div>
        <button onclick="generarContraseñaGPT()">Generar Contraseña con IA</button>
        <div class="empresa-info">
            <h2>Sobre ViralPro</h2>
            <p>ViralPro es líder en soluciones de ciberseguridad y generación de contraseñas seguras. Nuestro sistema utiliza algoritmos avanzados y tecnología de IA para crear contraseñas únicas y robustas.</p>
            <p>Contáctenos: <a href="mailto:info@viralpro.com">sviralpro@gmail.com</a></p>
            
        </div>
    </div>

    <script>
        function actualizarLongitud() {
            document.getElementById('longitudValor').textContent = document.getElementById('longitud').value;
        }

        function generarContraseña() {
            const longitud = parseInt(document.getElementById('longitud').value, 10);
            const complejidad = document.getElementById('complejidad').value;
            let charset = "";

            if (complejidad === "personalizado") {
                if (document.getElementById('incluirMayusculas').checked) charset += "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
                if (document.getElementById('incluirMinusculas').checked) charset += "abcdefghijklmnopqrstuvwxyz";
                if (document.getElementById('incluirNumeros').checked) charset += "0123456789";
                if (document.getElementById('incluirSimbolos').checked) charset += "!@#$%^&*()_+~`|}{[]:;?><,./-=";
            } else if (complejidad === "bajo") {
                charset = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ";
            } else if (complejidad === "medio") {
                charset = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
            } else if (complejidad === "alto") {
                charset = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%^&*()_+~`|}{[]:;?><,./-=";
            }

            let contraseña = "";
            for (let i = 0; i < longitud; i++) {
                const randomIndex = Math.floor(Math.random() * charset.length);
                contraseña += charset[randomIndex];
            }
            document.getElementById('contraseña').innerText = contraseña;
            evaluarFortaleza(contraseña);
        }

        function copiarContraseña() {
            const contraseña = document.getElementById('contraseña').innerText;
            navigator.clipboard.writeText(contraseña).then(function() {
                alert("Contraseña copiada al portapapeles");
            }, function(err) {
                alert("Error al copiar la contraseña: ", err);
            });
        }

        function evaluarFortaleza(contraseña) {
            let puntuacion = 0;
            if (contraseña.length >= 8) puntuacion += 1;
            if (contraseña.length >= 12) puntuacion += 1;
            if (/[A-Z]/.test(contraseña)) puntuacion += 1;
            if (/[a-z]/.test(contraseña)) puntuacion += 1;
            if (/[0-9]/.test(contraseña)) puntuacion += 1;
            if (/[^A-Za-z0-9]/.test(contraseña)) puntuacion += 1;

            let fortalezaTexto = "";
            let color = "";
            switch (puntuacion) {
                case 0:
                case 1:
                case 2:
                    fortalezaTexto = "Débil";
                    color = "#ff4d4d";
                    break;
                case 3:
                case 4:
                    fortalezaTexto = "Moderada";
                    color = "#ffa64d";
                    break;
                case 5:
                    fortalezaTexto = "Fuerte";
                    color = "#4dff4d";
                    break;
                case 6:
                    fortalezaTexto = "Muy Fuerte";
                    color = "#4d4dff";
                    break;
            }

            document.getElementById('fortalezaTexto').innerText = fortalezaTexto;
            const indicador = document.getElementById('fortalezaIndicador').firstElementChild;
            indicador.style.width = ((puntuacion / 6) * 100) + "%";
            indicador.style.backgroundColor = color;
        }

        function cambiarTema() {
            document.body.classList.toggle('dark-theme');
        }

        function generarContraseñaGPT() {
            // Simulación de generación de contraseña con IA
            const palabras = ["Seguro", "Fuerte", "Viral", "Pro", "Cyber", "Tech"];
            const numeros = Math.floor(Math.random() * 1000).toString().padStart(3, '0');
            const simbolos = "!@#$%^&*";
            let contraseña = palabras[Math.floor(Math.random() * palabras.length)] +
                             palabras[Math.floor(Math.random() * palabras.length)] +
                             numeros +
                             simbolos[Math.floor(Math.random() * simbolos.length)] +
                             simbolos[Math.floor(Math.random() * simbolos.length)];
            document.getElementById('contraseña').innerText = contraseña;
            evaluarFortaleza(contraseña);
        }

        document.getElementById('complejidad').addEventListener('change', function() {
            const opcionesPersonalizadas = document.getElementById('opcionesPersonalizadas');
            opcionesPersonalizadas.style.display = this.value === 'personalizado' ? 'block' : 'none';
        });

        // Generar una contraseña inicial al cargar la página
        window.onload = generarContraseña;
    </script>
</body>
</html>
