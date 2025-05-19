# Buffet-indicator
About indian market and global market valuation
<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Buffett Indicator Tracker</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f7f9fc;
      margin: 0;
      padding: 0;
      color: #333;
    }
    header {
      background-color: #0077cc;
      color: white;
      padding: 1rem;
      text-align: center;
    }
    main {
      padding: 2rem;
      max-width: 800px;
      margin: auto;
    }
    .country-data {
      background: white;
      margin-bottom: 1rem;
      padding: 1rem;
      border-radius: 8px;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    }
    .status {
      font-weight: bold;
    }
  </style>
</head>
<body>
  <header>
    <h1>Buffett Indicator Tracker</h1>
    <p>Live Market Cap to GDP Ratio - India & Global</p>
  </header>
  <main id="data-container">
    <p>Loading data...</p>
  </main>  <script>
    async function fetchBuffettData() {
      const container = document.getElementById("data-container");
      container.innerHTML = "";
      try {
        const response = await fetch("https://api.gurufocus.com/public/user/xxxxxx/buffett-indicator"); // Replace with valid API when available
        const data = await response.json();

        const countries = ["India", "United States", "China", "Japan", "Germany"];
        countries.forEach(country => {
          const val = data[country]; // Example structure
          if (val) {
            const status = val.ratio > 120 ? "Overvalued" : val.ratio > 90 ? "Fairly Valued" : "Undervalued";
            const div = document.createElement("div");
            div.className = "country-data";
            div.innerHTML = `
              <h2>${
