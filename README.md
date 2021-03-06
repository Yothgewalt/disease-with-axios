<h1 align="center">Disease.sh with Axios (Javascript Library)</h1>

<p align="center">
  <img src="https://i.imgur.com/9bCRbMm.jpg" alt="result" /><br>
  <br>
  <i>We use the <a href="https://corona.lmao.ninja/">disease.sh</a> website API to display the COVID data on our own website.</i>
</p>

<hr>

## Example of Code
Sample code that uses the API on our website. (Axios)

```js
const vaccinated = document.getElementById('vaccinated');
const cases_today = document.getElementById('cases-today');
const deaths_today = document.getElementById('deaths-today');

(async function() {
    const [injected] = await Promise.all([
        axios.get('https://disease.sh/v3/covid-19/vaccine/coverage/countries/Thailand'),
        axios.get('https://disease.sh/v3/covid-19/countries/tha').then((response) => {
            cases_today.innerHTML = response.data.todayCases + "&nbsp;เคส";
            deaths_today.innerHTML = response.data.todayDeaths + "&nbsp;คน";
        })
    ]);
    
    let injected_amount = [];
    Object.keys(injected.data.timeline).forEach((value) => {
        injected_amount.push(injected.data.timeline[value])
    });

    vaccinated.innerHTML = injected_amount.slice(-1) + "&nbsp;โดส";
})();
```
