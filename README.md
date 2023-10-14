# Anki-Dictionary-Helper
class CambridgeDictionary {
  constructor() {
    // Your code starting here ...
  }

  findTerm(word) {
    return new Promise((resolve, reject) => {
      const url = `https://dictionary.cambridge.org/search/english/direct/?q=${word}`;

      fetch(url)
        .then(response => response.text())
        .then(data => {
          // Use Element/CSS selector to extract the definition part you want
          const definition = data.querySelector('.def').innerText;

          resolve(definition);
        })
        .catch(error => {
          reject(error);
        });
    });
  }
}
