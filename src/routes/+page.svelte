<script>
import { onMount } from 'svelte';

let temp_c = 'Loading...';
let city = 'Loading...';

const url = 'https://weatherapi-com.p.rapidapi.com/current.json?q=-33.45%2C-70.67';
const options = {
	method: 'GET',
	headers: {
		'X-RapidAPI-Key': 'cdb5d2ff9dmshfe72d35c84fe24ep16d67fjsn65f10e26fcc1',
		'X-RapidAPI-Host': 'weatherapi-com.p.rapidapi.com'
	}
};


async function fetchWeather() {
    try {
      const response = await fetch(url, options);
      const result = await response.json();
      const current = result.current;
      const location = result.location;
      console.log(result);
        
        temp_c = current.temp_c
        city = location.name

      const {
        name, region, country
      } = location

      

      console.log(temp_c)


    }catch(error){
        console.log(error)
    }

    
  }

  // Call the async function to fetch the weather data
  //fetchWeather();


  onMount(fetchWeather)

</script>


<h1> Temp actual: {temp_c}</h1>

<h4>location: {city}</h4>

<p>hello</p>


<style>

    h1{
        font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    }
</style>


