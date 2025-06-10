# search.html
<!DOCTYPE html>
<html lang="bg">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Търсачка</title>
  <style>
    body {
      font-family: Georgia, serif;
      padding: 2rem;
      background-color: #fefefe;
    }
    input {
      width: 100%;
      padding: 1rem;
      font-size: 1rem;
      margin-bottom: 1rem;
    }
    ul {
      list-style: none;
      padding: 0;
    }
    li {
      margin-bottom: 1rem;
    }
    .result-title {
      font-weight: bold;
    }
  </style>
</head>
<body>
  <h1>🔎 Търсачка по ключови думи</h1>
  <input type="text" id="searchBox" placeholder="Въведете дума, автор, термин, място..." />

  <ul id="results"></ul>

  <script>
    const data = [
      {
        title: "Православна литература",
        content: "Книги на светите отци, жития, богословие, догматика, отци от IV век",
        url: "literature.html"
      },
      {
        title: "Петър Дънов и заблудите му",
        content: "Анализ на окултизма и противоположността му с православието",
        url: "articles.html"
      },
      {
        title: "Икони",
        content: "Византийски икони: Христос, Богородица, Свети Николай",
        url: "icons.html"
      },
      {
        title: "Симеон Александров",
        content: "Завършил Софийската духовна семинария и СУ, Богословски факултет",
        url: "author.html"
      }
    ];

    document.getElementById("searchBox").addEventListener("input", function() {
      const query = this.value.toLowerCase();
      const results = data.filter(item =>
        item.title.toLowerCase().includes(query) ||
        item.content.toLowerCase().includes(query)
      );

      const resultsList = document.getElementById("results");
      resultsList.innerHTML = "";

      results.forEach(result => {
        const li = document.createElement("li");
        li.innerHTML = `<a href="${result.url}" class="result-title">${result.title}</a><br>${result.content}`;
        resultsList.appendChild(li);
      });

      if (!results.length && query) {
        resultsList.innerHTML = "<li>Няма съвпадения.</li>";
      }
    });
  </script>
</body>
</html>
<a href="search.html">Търсачка</a>
