# Guía de Implementación UI/UX: Landing Page "Bootcamp 5.0 by Devlights"

**Objetivo:** Replicar la identidad visual y estructura de la landing page del Bootcamp 5.0 de Devlights utilizando **exclusivamente un archivo `index.html`**. Todo el CSS y JavaScript deberá estar embebido en el archivo, utilizando CDNs para librerías externas.

---

## 1. Stack Tecnológico y Librerías (vía CDN)
Para mantener todo en un solo archivo y asegurar un desarrollo ágil y moderno, se recomienda el siguiente stack mediante CDN:

*   **Estilos y Layout:** [Tailwind CSS (Play CDN)](https://tailwindcss.com/docs/installation/play-cdn) - Ideal para construir la interfaz rápidamente sin escribir un archivo `.css` externo.
*   **Tipografía:** [Google Fonts](https://fonts.google.com/) (Inter o Poppins).
*   **Iconos:** [FontAwesome (CDN)](https://cdnjs.com/libraries/font-awesome) o [Phosphor Icons](https://phosphoricons.com/) para los iconos del footer y flechas.
*   **Animaciones de Scroll:** [AOS (Animate On Scroll)](https://michalsnik.github.io/aos/) - Para las apariciones fluidas de los elementos al hacer scroll.

---

## 2. Paleta de Colores
El diseño presenta un estilo moderno, combinando fondos neutros con acentos geométricos vibrantes (estilo neo-brutalismo suave/tech).

Definir estas variables en el bloque `<style>` o en la configuración de Tailwind:

*   **Color de Fondo Principal (Body):** `#F4F2EC` (Beige claro / Hueso) - *Basado en el contenedor principal.*
*   **Color Navbar / Header:** `#1C1C1C` (Gris muy oscuro / Casi negro).
*   **Texto Principal:** `#111827` (Gris oscuro para alta legibilidad sobre fondos claros).
*   **Texto Invertido (Header/Footer):** `#FFFFFF` (Blanco) y `#9CA3AF` (Gris claro para hovers).
*   **Acentos Geométricos (Formas abstractas y etiquetas):**
    *   🟣 Púrpura (Etiqueta "Sumate a esta edición"): `#A855F7` o `#9D4EDD`
    *   🔵 Azul: `#3B82F6` o `#2563EB`
    *   🔴 Rojo: `#EF4444` o `#DC2626`
    *   🟡 Amarillo: `#F59E0B` o `#FBBF24`

---

## 3. Tipografía
El diseño utiliza fuentes sans-serif muy limpias y geométricas.

*   **Títulos (h1, h2, h3):** `Poppins` o `Montserrat` (Pesos: 600, 700, 800).
*   **Cuerpo de Texto y Párrafos:** `Inter` o `Roboto` (Pesos: 400, 500).
*   **Contador (Countdown):** Utilizar una fuente monoespaciada o la misma fuente de títulos con un peso robusto (ej. 700) y tamaño XL.

---

## 4. Estructura de Componentes (Diseño)

### A. Header (Navegación)
*   **Estructura:** Contenedor Flexbox. Logo alineado a la izquierda (`justify-between`), enlaces centrados/derecha.
*   **Estilo:** Fondo oscuro (`bg-[#1C1C1C]`), texto blanco. Sticky top (`position: sticky; top: 0; z-index: 50;`).
*   **Enlaces:** "Acerca del Bootcamp", "Programa", "Mentores", "Preguntas frecuentes".
*   **Hover:** Cambio sutil a gris claro o subrayado.

### B. Hero Section & Countdown
*   **Fondo:** Beige claro.
*   **Composición:** Gráfico central 3D (las teclas "BOOT CAMP") superpuesto sobre formas geométricas (círculos y polígonos asimétricos de la paleta de acentos).
*   **Cinta/Badge:** Un div centrado con fondo púrpura y texto blanco ("Sumate a esta edición 5.0").
*   **Contador:** Estructura Flexbox/Grid mostrando `DÍAS : HORAS : MINUTOS : SEGUNDOS`. Números en tamaño gigante (ej. `text-6xl`), etiquetas en tamaño pequeño (`text-sm`).

### C. Tarjetas (Cards)
**Tarjetas de Mentores / Coaches:**
*   **Diseño:** Limpio, sin bordes pesados, posiblemente con un ligero sombreado (`shadow-md` o `shadow-lg` en hover).
*   **Estructura interna:** 
    *   Imagen (Retrato) en la parte superior, con bordes redondeados (`rounded-xl` o imagen circular).
    *   Nombre: Texto en negrita.
    *   Rol / Módulo: Texto destacado (usando un color de acento o fuente más pequeña).
    *   Descripción: Párrafo descriptivo breve.

**Tarjetas de Requisitos:**
*   Diseño minimalista numerado ("01", "02", etc.) con el número en grande y el texto descriptivo debajo.

### D. Acordeón (Preguntas Frecuentes)
*   Para implementarlo sin Javascript complejo, utilizar las etiquetas nativas de HTML5: `<details>` y `<summary>`.
*   Estilizar el tag `<summary>` con cursor pointer, fondo blanco o beige más oscuro, y padding. Ocultar la flecha por defecto y agregar una flecha personalizada rotatoria usando CSS.

### E. Footer
*   Fondo oscuro o neutro sólido.
*   Secciones: "By Devlights", "Trabajá con nosotros" (con mailto:`rrhh@devlights.com`), y enlaces a redes sociales (iconos alineados horizontalmente).

---

## 5. Animaciones e Interacciones
*   **El Contador (JS):** Crear un script al final del body que actualice el DOM cada 1000ms calculando la diferencia entre una fecha objetivo y la fecha actual.
*   **Hover States:** 
    *   Tarjetas de mentores: Translación ligera hacia arriba (`transform: translateY(-5px)`) y aumento de sombra.
    *   Botones/Enlaces: Cambio de color de opacidad (`opacity-80`).
*   **Scroll Reveal (Librería AOS):**
    *   Secciones ("¿Qué vas a aprender?", "Coaches"): `<div data-aos="fade-up" data-aos-duration="800">`.
    *   Tarjetas de requisitos: Animación escalonada (`data-aos-delay="100"`, `"200"`, etc.).

---

## 6. Esqueleto Base (Boilerplate `index.html`)
A continuación, la estructura inicial recomendada para el archivo único:

```html
<!DOCTYPE html>
<html lang="es" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bootcamp 5.0 by Devlights</title>
    
    <!-- Google Fonts -->
    <link href="[https://fonts.googleapis.com/css2?family=Inter:wght@400;500&family=Poppins:wght@600;700;800&display=swap](https://fonts.googleapis.com/css2?family=Inter:wght@400;500&family=Poppins:wght@600;700;800&display=swap)" rel="stylesheet">
    
    <!-- FontAwesome -->
    <link rel="stylesheet" href="[https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css](https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css)">
    
    <!-- AOS CSS -->
    <link href="[https://unpkg.com/aos@2.3.1/dist/aos.css](https://unpkg.com/aos@2.3.1/dist/aos.css)" rel="stylesheet">

    <!-- Tailwind CSS CDN -->
    <script src="[https://cdn.tailwindcss.com](https://cdn.tailwindcss.com)"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        brand: {
                            bg: '#F4F2EC',
                            dark: '#1C1C1C',
                            purple: '#9D4EDD',
                            blue: '#3B82F6',
                            red: '#EF4444',
                            yellow: '#FBBF24'
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                        heading: ['Poppins', 'sans-serif']
                    }
                }
            }
        }
    </script>

    <style>
        /* CSS Personalizado Embebido */
        body { background-color: theme('colors.brand.bg'); color: #111827; }
        h1, h2, h3 { font-family: theme('fontFamily.heading'); }
        
        /* Estilos para el Details/Summary del FAQ */
        details > summary { list-style: none; }
        details > summary::-webkit-details-marker { display: none; }
    </style>
</head>
<body class="antialiased">

    <!-- HEADER -->
    <header class="bg-brand-dark text-white sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 py-4 flex justify-between items-center">
            <div class="font-heading font-bold text-xl">D Devlights</div>
            <nav class="hidden md:flex gap-6 text-sm">
                <a href="#acerca" class="hover:text-gray-300 transition">Acerca del Bootcamp</a>
                <a href="#programa" class="hover:text-gray-300 transition">Programa</a>
                <a href="#mentores" class="hover:text-gray-300 transition">Mentores</a>
                <a href="#faq" class="hover:text-gray-300 transition">Preguntas frecuentes</a>
            </nav>
        </div>
    </header>

    <!-- HERO & COUNTDOWN -->
    <section class="min-h-screen flex flex-col items-center justify-center relative overflow-hidden pt-10">
        <!-- Reemplazar con imagen real o maquetado SVG de las formas y teclas -->
        <div class="w-full max-w-3xl h-64 bg-gray-200 rounded-lg flex items-center justify-center mb-8 shadow-inner" data-aos="zoom-in">
            [Gráfico Teclado 3D "BOOTCAMP" y Formas Geométricas]
        </div>

        <!-- Banner Edición -->
        <div class="bg-brand-purple text-white px-6 py-2 rounded-sm font-bold uppercase tracking-wider mb-8" data-aos="fade-up">
            Sumate a esta edición 5.0
        </div>

        <!-- Countdown -->
        <div class="flex gap-4 md:gap-8 text-center" data-aos="fade-up" data-aos-delay="200">
            <div>
                <span id="days" class="text-5xl md:text-7xl font-heading font-bold">00</span>
                <p class="text-xs font-bold mt-2">DAYS</p>
            </div>
            <span class="text-5xl md:text-7xl font-heading text-brand-purple">:</span>
            <!-- Repetir estructura para Hours, Minutes, Seconds -->
        </div>
    </section>

    <!-- EL RESTO DE LAS SECCIONES IRÁN AQUÍ (Requisitos, Módulos, Mentores, FAQs) -->

    <!-- FOOTER -->
    <footer class="bg-brand-dark text-white py-12 mt-20">
        <div class="max-w-7xl mx-auto px-4 grid grid-cols-1 md:grid-cols-3 gap-8">
            <div>
                <h3 class="font-heading font-bold mb-4">By Devlights</h3>
            </div>
            <div>
                <h3 class="font-bold mb-4">Trabajá con nosotros</h3>
                <a href="mailto:rrhh@devlights.com" class="text-gray-400 hover:text-white transition">rrhh@devlights.com</a>
            </div>
            <div class="flex gap-4 text-2xl">
                <a href="#" class="hover:text-brand-blue transition"><i class="fa-brands fa-facebook"></i></a>
                <a href="#" class="hover:text-pink-500 transition"><i class="fa-brands fa-instagram"></i></a>
                <a href="#" class="hover:text-brand-blue transition"><i class="fa-brands fa-linkedin"></i></a>
            </div>
        </div>
    </footer>

    <!-- AOS JS -->
    <script src="[https://unpkg.com/aos@2.3.1/dist/aos.js](https://unpkg.com/aos@2.3.1/dist/aos.js)"></script>
    <script>
        // Inicializar AOS
        AOS.init({ once: true });

        // Lógica del Contador (Ejemplo)
        const countDownDate = new Date("Nov 1, 2026 00:00:00").getTime();
        const x = setInterval(function() {
            const now = new Date().getTime();
            const distance = countDownDate - now;
            // Cálculos matemáticos aquí...
            // document.getElementById("days").innerHTML = days;
            // Si termina: clearInterval(x);
        }, 1000);
    </script>
</body>
</html>