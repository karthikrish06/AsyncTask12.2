// Function to fetch data using promises
function fetchData(url) {
    return new Promise((resolve, reject) => {
        fetch(url)
            .then(response => {
                if (!response.ok) {
                    throw new Error(`Network response was not ok: ${response.status}`);
                }
                return response.json();
            })
            .then(data => resolve(data))
            .catch(error => reject(error));
    });
}

// Function to update Chuck Norris joke
function updateChuckNorrisJoke() {
    fetchData('https://api.chucknorris.io/jokes/random')
        .then(data => {
            document.getElementById('chuckJoke').innerText = data.value;
        })
        .catch(error => console.error(error));
}