---
layout: default
title: Generador de BibTeX
---

<form id="bibtexForm">
    <label for="author">Autor:</label>
    <input type="text" id="author" name="author" required>

    <label for="title">Título:</label>
    <input type="text" id="title" name="title" required>

    <label for="journal">Journal:</label>
    <input type="text" id="journal" name="journal">

    <label for="year">Año:</label>
    <input type="text" id="year" name="year" required>

    <label for="volume">Volumen:</label>
    <input type="text" id="volume" name="volume">

    <label for="number">Número:</label>
    <input type="text" id="number" name="number">

    <label for="pages">Páginas:</label>
    <input type="text" id="pages" name="pages">

    <label for="doi">URL:</label>
    <input type="text" id="url" name="url">

    <button type="submit">Generar BibTeX</button>
</form>

<div class="result" id="result">
    <!-- Aquí se mostrará el BibTeX generado -->
</div>

<button id="copyButton" style="display: none;">Copiar al portapapeles</button>

<script>
    document.getElementById('bibtexForm').addEventListener('submit', function(event) {
        event.preventDefault();
        
        const author = document.getElementById('author').value.trim();
        const title = document.getElementById('title').value.trim();
        const journal = document.getElementById('journal').value.trim();
        const year = document.getElementById('year').value.trim();
        const volume = document.getElementById('volume').value.trim();
        const number = document.getElementById('number').value.trim();
        const pages = document.getElementById('pages').value.trim();
        const url = document.getElementById('url').value.trim();

        if (!author || !title || !year) {
            alert("Por favor complete los campos obligatorios.");
            return;
        }

        if (isNaN(year)) {
            alert("El año debe ser un número.");
            return;
        }

        let bibtex = `@article{${author.split(' ').join('')}${year},
  author = {${author}},
  title = {${title}},
  journal = {${journal}},
  year = {${year}},
  volume = {${volume}},
  number = {${number}},
  pages = {${pages}},
  url = {${url}}
}`;

        const resultDiv = document.getElementById('result');
        resultDiv.textContent = bibtex;

        // Mostrar el botón para copiar
        document.getElementById('copyButton').style.display = 'block';
    });

    document.getElementById('copyButton').addEventListener('click', function() {
        const resultText = document.getElementById('result').textContent;
        navigator.clipboard.writeText(resultText).then(function() {
            alert('BibTeX copiado al portapapeles!');
        }, function(err) {
            console.error('Error al copiar al portapapeles:', err);
        });
    });
</script>

<style>
/* Estilos básicos para el sitio web */
body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    margin: 0;
    padding: 0;
    color: #333;
    background-color: #f4f4f4;
    padding-bottom: 60px; /* Ajuste para tener en cuenta el footer */
}

header {
    background: #333;
    color: #fff;
    padding: 10px 0;
    text-align: center;
}

nav ul {
    list-style: none;
    padding: 0;
}

nav ul li {
    display: inline;
    margin: 0 15px;
}

nav ul li a {
    color: #fff;
    text-decoration: none;
}

main {
    padding: 20px;
}

footer {
    background: #333;
    color: #fff;
    text-align: center;
    padding: 10px 0;
    position: fixed;
    width: 100%;
    bottom: 0;
}

/* Estilos adicionales para el formulario y el resultado */
form {
    display: flex;
    flex-direction: column;
    max-width: 400px;
    margin: auto;
    background: #fff;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

label {
    margin-top: 10px;
}

input {
    margin-bottom: 10px;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

button {
    padding: 10px;
    background-color: #007BFF;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

button:hover {
    background-color: #0056b3;
}

.result {
    margin-top: 20px;
    white-space: pre-wrap;
    background: #fff;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-family: 'Courier New', Courier, monospace;
}

#copyButton {
    display: block;
    margin: 20px auto;
    padding: 10px;
    background-color: #28a745;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

#copyButton:hover {
    background-color: #218838;
}
</style>
