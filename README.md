# M-todo-clareza-para-come-ar-no-Marketing-Digital-
<!DOCTYPE html>
<html lang="pt">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Descobre a tua mina de ouro</title>

  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      padding: 24px;
      font-family: Arial, sans-serif;
      background: #f7f7f5;
      color: #181818;
    }

    .quiz {
      max-width: 650px;
      margin: 30px auto;
      padding: 28px;
      background: #ffffff;
      border: 1px solid #e8e8e8;
      border-radius: 16px;
    }

    h1 {
      margin-top: 0;
      font-size: 30px;
    }

    .intro {
      line-height: 1.6;
      color: #555;
    }

    fieldset {
      margin: 24px 0;
      padding: 18px;
      border: 1px solid #dddddd;
      border-radius: 12px;
    }

    legend {
      padding: 0 6px;
      font-weight: bold;
    }

    label {
      display: block;
      margin: 12px 0;
      padding: 12px;
      background: #f7f7f5;
      border-radius: 8px;
      cursor: pointer;
    }

    label:hover {
      background: #eeeeea;
    }

    input {
      margin-right: 8px;
    }

    button {
      padding: 14px 20px;
      border: 0;
      border-radius: 8px;
      background: #176b45;
      color: white;
      font-size: 16px;
      cursor: pointer;
    }

    button:hover {
      background: #105538;
    }

    #resultado {
      margin-top: 24px;
      padding: 20px;
      background: #eef6f0;
      border-radius: 12px;
      line-height: 1.6;
    }

    #resultado h2 {
      margin-top: 0;
    }

    .nota {
      margin-top: 20px;
      font-size: 13px;
      color: #666;
    }

    [hidden] {
      display: none;
    }

    @media (max-width: 480px) {
      body {
        padding: 12px;
      }

      .quiz {
        margin: 10px auto;
        padding: 20px;
      }

      h1 {
        font-size: 25px;
      }
    }
  </style>
</head>

<body>
  <main class="quiz">
    <h1>Descobre a tua mina de ouro</h1>

    <p class="intro">
      Responde a estas três perguntas para descobrires que tipo de
      oportunidade digital poderá combinar melhor contigo.
    </p>

    <form id="quiz">
      <fieldset>
        <legend>1. O que gostas mais de fazer?</legend>

        <label>
          <input type="radio" name="q1" value="servico" required>
          Ajudar alguém a resolver um problema
        </label>

        <label>
          <input type="radio" name="q1" value="conteudo">
          Criar e partilhar ideias ou conteúdos
        </label>

        <label>
          <input type="radio" name="q1" value="produto">
          Organizar informação num guia, modelo ou recurso
        </label>
      </fieldset>

      <fieldset>
        <legend>2. Pelo que é que as pessoas costumam pedir a tua ajuda?</legend>

        <label>
          <input type="radio" name="q2" value="servico" required>
          Conselhos ou ajuda para resolver algo
        </label>

        <label>
          <input type="radio" name="q2" value="conteudo">
          Ideias, recomendações ou explicações
        </label>

        <label>
          <input type="radio" name="q2" value="produto">
          Materiais, listas, planos ou instruções
        </label>
      </fieldset>

      <fieldset>
        <legend>3. Como preferias ajudar outras pessoas?</legend>

        <label>
          <input type="radio" name="q3" value="servico" required>
          Acompanhá-las diretamente, uma a uma
        </label>

        <label>
          <input type="radio" name="q3" value="conteudo">
          Partilhar conteúdos que muitas pessoas possam ver
        </label>

        <label>
          <input type="radio" name="q3" value="produto">
          Criar algo que possam usar ao seu próprio ritmo
        </label>
      </fieldset>

      <button type="submit">Ver o meu resultado</button>
    </form>

    <section id="resultado" hidden aria-live="polite"></section>

    <p class="nota">
      Este resultado é um ponto de partida para refletires — não é uma
      promessa de rendimento nem uma garantia de sucesso.
    </p>
  </main>

  <script>
    const formulario = document.getElementById("quiz");
    const caixaResultado = document.getElementById("resultado");

    const resultados = {
      servico: {
        titulo: "A tua pista: oferecer um serviço",
        texto: "Podes explorar uma competência que já tens e ajudar pessoas a resolver um problema concreto. Por exemplo: apoio, consultoria, aulas ou serviços digitais."
      },
      conteudo: {
        titulo: "A tua pista: criar conteúdo",
        texto: "Podes explorar temas que conheces e partilhar ideias úteis. Por exemplo: publicações, vídeos, tutoriais ou uma newsletter."
      },
      produto: {
        titulo: "A tua pista: criar um produto digital",
        texto: "Podes organizar aquilo que sabes num recurso que ajude outras pessoas. Por exemplo: um guia, um modelo, uma checklist ou um pequeno curso."
      }
    };

    formulario.addEventListener("submit", function(evento) {
      evento.preventDefault();

      const respostas = new FormData(formulario);
      const pontos = {
        servico: 0,
        conteudo: 0,
        produto: 0
      };

      for (const resposta of respostas.values()) {
        pontos[resposta]++;
      }

      const melhorOpcao = Object.keys(pontos).reduce((melhor, atual) =>
        pontos[atual] > pontos[melhor] ? atual : melhor
      );

      caixaResultado.innerHTML = `
        <h2>${resultados[melhorOpcao].titulo}</h2>
        <p>${resultados[melhorOpcao].texto}</p>
        <button type="button" id="refazer">Fazer novamente</button>
      `;

      caixaResultado.hidden = false;
      caixaResultado.scrollIntoView({ behavior: "smooth" });

      document.getElementById("refazer").addEventListener("click", function() {
        formulario.reset();
        caixaResultado.hidden = true;
        formulario.scrollIntoView({ behavior: "smooth" });
      });
    });
  </script>
</body>
</html>
