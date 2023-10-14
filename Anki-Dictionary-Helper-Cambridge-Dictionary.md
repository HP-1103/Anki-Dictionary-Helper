class CambridgeDictionary {
  constructor() {
    // Your code starting here ...
  }

  findTerm(word) {
    return new Promise((resolve, reject) => {
      const url = `https://dictionary.cambridge.org/search/english/direct/?q=${encodeURIComponent(word)}`;

      fetch(url)
        .then(response => response.text())
        .then(data => {
          // Use Element/CSS selector to get the definition part you want
          const definition = document.querySelector('.def.ddef_d.db').textContent;
          resolve(definition);
        })
        .catch(error => reject(error));
    });
  }
}

