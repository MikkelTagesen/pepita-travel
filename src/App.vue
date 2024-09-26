<template>
  <!-- Her er vores dom elementer -->
  
  <!--indsat billede fra nettet-->
  <img
    src="https://chirpforbirds.com/wp-content/uploads/2021/02/Blog-featured-image-2-Kingfisher.jpg"
    alt="Kingfisher"
    width="400"
  />

  <h1>Pepita's energy: {{ pepita.energy }}</h1>
  <h2>Pepita's current locaction: {{ pepita.location }}</h1>
    <h2>Pepita's visited cities: {{ pepita.visitedCities }}</h1>

  <input type="number" v-model="gramsToEat" placeholder="Grams" />
  <button @click="eat">Eat</button>

  <input type="number" v-model="kmsToFly" placeholder="Kilometers" />
  <button @click="fly">Fly</button>
  <div v-for="city in cityInfo.cityNames">

  <button @click="goToPlace('New York)">New York</button>
  </div>
</template>

<script>
import { ref, reactive } from 'vue'; 

export default { 
  setup() { 
    // Mine variabler
    const gramsToEat = ref(0);
    const kmsToFly = ref(0);

    //mine objekter
    const pepita = reactive({
      energy: 0,
      location: 'Aarhus'
      visitedCities: ['Aarhus']
    });

    const cityInfo = reactive({
      cityNames: ['Aarhus', 'Copenhagen','Nuuk','New York', 'The Moon'],
      cityLocation: [0, 300, 4500, 7500, 250000]
    });

    // mine funktioner
    function eat() {
      pepita.energy += gramsToEat.value * 4;
    }

    function fly() {
      pepita.energy -= kmsToFly.value * 2 + 10;
    }

    function goToPlace(placeToGo){
      let cityFromIndex = cityInfo.cityNames.indexOf(pepita.location)
      let cityToIndex = cityInfo.cityNames.indexOf(placeToGo)
      let cityToLocation = cityInfo.cityLocation[cityToIndex]
      let cityFromLocation = cityInfo.cityLocation[cityFromIndex]
      let distance = math.abs(cityFromLocation-cityToLocation)
      console.log(cityToIndex)


      if (pepita.energy >= distance * 2 + 10){
        pepita.energy -= distance * 2 + 10
        pepita.location = placeToGo
        if (!pepita.visitedCities.includes(placeToGo)

      }
      pepita.energy -= disstance * 2 + 10;
    } else {
      alert('pepita cant travel ${distance} km to ${placeToGo} - eat more grams')
    }

    }

    // Husk at return'e alt!!
    return {
      gramsToEat,
      kmsToFly,
      eat,
      pepita,
      fly,
      goToPlace,
      cityInfo,
    };
  }
};
</script>
