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

    <label for="doi">DOI:</label>
    <input type="text" id="doi" name="doi">

    <button type="submit">Generar BibTeX</button>
</form>

<div class="result" id="result"></div>

<script>
    document.getElementById('bibtexForm').addEventListener('submit', function(event) {
        event.preventDefault();
        
        const author = document.getElementById('author').value;
        const title = document.getElementById('title').value;
        const journal = document.getElementById('journal').value;
        const year = document.getElementById('year').value;
        const volume = document.getElementById('volume').value;
        const number = document.getElementById('number').value;
        const pages = document.getElementById('pages').value;
        const doi = document.getElementById('doi').value;

        let bibtex = `@article{${author.split(' ').join('')}${year},
  author = {${author}},
  title = {${title}},
  journal = {${journal}},
  year = {${year}},
  volume = {${volume}},
  number = {${number}},
  pages = {${pages}},
  doi = {${doi}}
}`;

        document.getElementById('result').textContent = bibtex;
    });
</script>
