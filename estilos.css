<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Malla Curricular Desbloqueable - Biotecnología</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(to right, #f0f4c3, #a5d6a7);
      padding: 40px;
      margin: 0;
    }
    h1 {
      text-align: center;
      color: #2e7d32;
      font-size: 2.5em;
      margin-bottom: 40px;
    }
    h2 {
      color: #1b5e20;
      margin-top: 40px;
      border-bottom: 2px solid #66bb6a;
      padding-bottom: 5px;
    }
    .materia {
      display: block;
      background: #ffffff;
      border: 2px solid #4caf50;
      padding: 12px 16px;
      margin: 6px 0;
      border-radius: 10px;
      cursor: pointer;
      opacity: 1;
      transition: all 0.3s ease;
      box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    }
    .materia:hover {
      background-color: #e8f5e9;
      transform: scale(1.02);
    }
    .materia.bloqueada {
      opacity: 0.4;
      pointer-events: none;
      background-color: #eeeeee;
      border-color: #bdbdbd;
      color: #757575;
    }
    .materia.completada {
      text-decoration: line-through;
      background: #c8e6c9;
      border-color: #388e3c;
      color: #2e7d32;
    }
  </style>
</head>
<body>
  <h1>Malla Curricular Interactiva - Biotecnología</h1>

  <div id="contenedor"></div>

  <script>
    const materias = {
      "1° Año": [
        "topicos_algebra|Tópicos de álgebra",
        "intro_fisica|Introducción a la física",
        "quimica_general|Química general",
        "intro_biologia|Introducción a la biología molecular y celular",
        "pensamiento_critico|Pensamiento crítico",
        "calculo1|Cálculo I",
        "fisica_biociencias|Física aplicada a las biociencias",
        "calculo2|Cálculo II",
        "quimica_inorganica|Química general e inorgánica",
        "direccion_empresas|Dirección de empresas",
        "biologia_fisiologia|Biología y fisiología molecular"
      ],
      "2° Año": [
        "quimica_analitica|Química analítica",
        "quimica_organica|Química orgánica",
        "probabilidad|Probabilidad y estadística",
        "economia|Economía general y finanzas",
        "costos|Costos industriales",
        "genetica|Genética molecular",
        "microbiologia|Microbiología general",
        "ingles1|Inglés I",
        "quimica_bio1|Química biológica I",
        "analisis_instrumental|Análisis instrumental"
      ],
      "3° Año": [
        "tecnicas|Técnicas biotecnológicas",
        "fenomenos|Fenómenos de transporte",
        "bioestadistica|Bioestadística",
        "agrobiotecnologia|Agrobiotecnología",
        "quimica_bio2|Química biológica II",
        "ingenieria1|Ingeniería genética I",
        "fisicoquimica|Fisicoquímica",
        "comercializacion|Comercialización de productos biotecnológicos",
        "bioinformatica|Bioinformática",
        "inmunologia|Inmunología"
      ],
      "4° Año": [
        "derecho|Biotecnología y derecho",
        "ingenieria2|Ingeniería genética II",
        "biorreactores|Biorreactores",
        "cultivos|Cultivos celulares",
        "estrategias|Estrategias industriales",
        "proyecto|Proyecto final de licenciatura",
        "genomica|Genómica y proteómica",
        "industrias|Industrias y procesos biotecnológicos",
        "nano|Nanobiotecnología",
        "bioetica|Bioética",
        "negocios|Desarrollo de negocios biotecnológicos"
      ],
      "5° Año": [
        "opt1|Optativa I",
        "opt2|Optativa II",
        "sistemas|Biología de sistemas",
        "lab_bioprocesos|Laboratorio de bioprocesos",
        "lab_diagnostico|Laboratorio de diagnóstico y ciencias forenses"
      ]
    };

    const correlativas = {
      calculo2: ["calculo1"],
      probabilidad: ["calculo1"],
      fisica_biociencias: ["intro_fisica"],
      quimica_inorganica: ["quimica_general"],
      biologia_fisiologia: ["intro_biologia"],
      fenomenos: ["calculo2", "fisica_biociencias"],
      quimica_analitica: ["quimica_inorganica"],
      quimica_organica: ["quimica_inorganica"],
      genetica: ["biologia_fisiologia"],
      quimica_bio1: ["quimica_organica"],
      analisis_instrumental: ["quimica_analitica"],
      bioestadistica: ["probabilidad"],
      tecnicas: ["genetica"],
      inmunologia: ["biologia_fisiologia"],
      cultivos: ["quimica_bio1"],
      quimica_bio2: ["quimica_bio1"],
      ingenieria1: ["tecnicas"],
      ingenieria2: ["ingenieria1"],
      fisicoquimica: ["fisica_biociencias"],
      bioinformatica: ["genetica"],
      comercializacion: [],
      negocios: ["comercializacion"],
      biorreactores: ["fenomenos"],
      industrias: ["biorreactores"],
      lab_bioprocesos: ["biorreactores"],
      sistemas: ["quimica_bio2"],
      genomica: ["bioinformatica"],
      nano: ["tecnicas"],
      lab_diagnostico: ["tecnicas"],
      estrategias: ["direccion_empresas"],
      bioetica: ["biologia_fisiologia"],
      proyecto: ["tecnicas"]
    };

    const completadas = new Set();

    const contenedor = document.getElementById("contenedor");
    for (const [anio, materiasAnio] of Object.entries(materias)) {
      const h2 = document.createElement("h2");
      h2.textContent = anio;
      contenedor.appendChild(h2);

      for (const m of materiasAnio) {
        const [id, nombre] = m.split("|");
        const div = document.createElement("div");
        div.textContent = nombre;
        div.id = id;
        div.className = "materia" + (correlativas[id] ? " bloqueada" : "");
        if (!correlativas[id]) div.onclick = () => completar(id);
        contenedor.appendChild(div);
      }
    }

    function completar(id) {
      const div = document.getElementById(id);
      div.classList.add("completada");
      div.onclick = null;
      completadas.add(id);
      desbloquearMaterias();
    }

    function desbloquearMaterias() {
      for (const [materia, prereqs] of Object.entries(correlativas)) {
        if (!completadas.has(materia)) {
          const ok = prereqs.every(p => completadas.has(p));
          if (ok) {
            const div = document.getElementById(materia);
            div.classList.remove("bloqueada");
            div.onclick = () => completar(materia);
          }
        }
      }
    }
  </script>
</body>
</html>
