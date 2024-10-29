<script>
  import * as d3 from 'd3';
  import data from '/src/data/album.json'; 


  const generoScale = d3.scaleOrdinal()
    .domain(["country", "pop", "rock", "indiefolk"])
    .range([
      "/images/generos/country.svg",
      "/images/generos/pop.svg",
      "/images/generos/rock.svg",
      "/images/generos/indiefolk.svg"
    ]);

 
  const colorLightness = d3.scaleOrdinal()
    .domain([1,2,3])
    .range([25,10,-5])

</script>

<main-container>

<header>

  <h1 class="titulo">Taylor Swift</h1>

  <h2 class="subtitulo">Un recorrido por su discografía</h2>

  <h3 class="bajada">Taylor Swift no solo ha conquistado el mundo con su música, sino que también ha tejido una red de conexiones entre sus fans a través de las pulseras de la amistad que sus seguidores hacen para los conciertos. Estas pulseras tienen una codificación propia, diferenciando los álbumes por colores y usando mostacillas que hacen referencia a elementos de las canciones de Taylor. <br> <br>
  Buscamos, a través de las pulseras, hacer un recorrido por la discografía de Taylor Swift, mostrando sus álbumes, cuánto nos gustaron, cuántas canciones tienen, cuántas vendieron, etc. Generamos una codificación similar a la que usan los fans al crear estas pulseras.</h3>

  <img class="referencias" src="/images/referencias.svg" alt="referencia" style="" />
 
</header>

<main>
  <div class="pulseras-container">
    {#each data as album}
      <div class="pulsera">
        <h2 class="album-name">{album.album}</h2>
        <h2 class="anio">{album.anio}</h2>

        <div class="hilo-container">

        <!-- Hilo: según la re-grabación -->
         {#if (album.regrabacion) == "no"}
          <img src="/images/hilos/hilo.svg" alt="hilo" class="hilo__img"/>
        {:else if (album.regrabacion) == "si" && album["regrabada"] === "no"}
          <img src="/images/hilos/regrabacion.svg" alt="hilo" class="hilo__img"/>
        {:else}
          <img src="/images/hilos/regrabada.svg" alt="hilo" class="hilo__img" />
        {/if}

        <!-- Mostacillas: una por cada canción -->
        <div class="mostacillas_a">
          {#each Array(album.canciones_a) as _, i}
            <img class="mostacilla"src="/images/canciones/canciones.svg" alt="mostacilla" />
          {/each}
        </div>

        <div class="mostacillas_b">
          {#each Array(album.canciones_b) as _, i}
            <img class="mostacilla"src="/images/canciones/canciones.svg" alt="mostacilla" />
          {/each}
        </div>

        <!-- Dijes: segun el genero -->
      
       
        <div class="dijes">
        {#if (album.rock) == "si"}
          <img src="/images/generos/rock.svg" alt="genero" style="position: absolute; filter: hue-rotate({colorLightness(album.gusto)}deg) ;" />
        {/if}
        {#if (album.country) == "si"}
          <img src="/images/generos/country.svg" alt="genero" style="position: absolute; filter: hue-rotate({colorLightness(album.gusto)}deg);" />
        {/if}
        {#if (album.indiefolk) == "si"}
          <img src="/images/generos/indiefolk.svg" alt="genero" style="position: absolute; filter: hue-rotate({colorLightness(album.gusto)}deg);" />
        {/if}
        {#if (album.pop) == "si"}
          <img src="/images/generos/pop.svg" alt="genero" style="position: absolute; filter: hue-rotate({colorLightness(album.gusto)}deg);" />
        {/if}
      </div>
   
    

      <!-- Reproducciones: pulsera segun billones -->
      <div class="reproducciones">
        {#if (album.reproducciones) == "1"}
          <img src="/images/billones/1.svg" alt="1" style="" />
        {/if}
        {#if (album.reproducciones) == "2"}
          <img src="/images/billones/2.svg" alt="2" style="" />
        {/if}
        {#if (album.reproducciones) == "3"}
          <img src="/images/billones/3.svg" alt="3" style="" />
        {/if}
        {#if (album.reproducciones) == "4"}
          <img src="/images/billones/4.svg" alt="4" style="" />
        {/if}
        {#if (album.reproducciones) == "5"}
          <img src="/images/billones/5.svg" alt="5" style="" />
        {/if}
        {#if (album.reproducciones) == "6"}
          <img src="/images/billones/6.svg" alt="6" style="" />
        {/if}
        {#if (album.reproducciones) == "7"}
          <img src="/images/billones/7.svg" alt="7" style="" />
        {/if}
        {#if (album.reproducciones) == "8"}
          <img src="/images/billones/8.svg" alt="8" style="" />
        {/if}
        {#if (album.reproducciones) == "9"}
          <img src="/images/billones/9.svg" alt="9" style="" />
        {/if}
        {#if (album.reproducciones) == "10"}
          <img src="/images/billones/10.svg" alt="10" style="" />
        {/if}
        {#if (album.reproducciones) == "11"}
          <img src="/images/billones/11.svg" alt="11" style="" />
        {/if}
      </div>
    </div>
    </div>
    {/each}
  </div>
</main>
</main-container>

<style>

@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap');

.main-container {
  font-family: "Montserrat", sans-serif;
  background-color: #f0f0f0;
}

body {
  margin: 0;
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  align-items: center;
  justify-content: center;
  background-color: #f0f0f0;
}

header {
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
}

.titulo{
  font-weight: 700;
  font-size: 80px;
  text-align: center;
  color: #969BFF;
  margin-top: 20px;
  text-shadow: 2px 2px 0px #dbdbdb;;
}

.subtitulo{
  font-weight: 300;
  font-size: 25px;
  text-align: center;
  color: #210268;
}

main {
  display: flex;
  justify-content: center;
  align-items: center;
}

.album-name{
  font-size: 25px;
  font-weight: 400;
  color:#210268;
}

.anio{
  font-size: 15px;
  font-weight: 300;
  color: #8a8a8a;
  transform: translateY(-25px);
}

.bajada{
  text-align: center;
  font-size: 18px;
  font-weight: 300;
  color: #8a8a8a;
  margin-top: 30px;
  margin-left: 200px;
  margin-right: 200px;
}

.referencias{
  width: 70%;
  margin:auto;
  margin-top: 50px;
}

.pulseras-container {
  flex-wrap: wrap;
  gap: 40px;
  justify-content: center;
}

.pulsera {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 40px 0;
}

.reproducciones{
  position: absolute;
  display: flex;
  width: 300px;
  height: 300px;
  top: 50%; 
  left: 50%; 
  transform: translate(-50%, -38%);
  z-index: 2; 
}

.mostacillas_a {

  width: 100%;
    position: absolute;
    display: flex;
    z-index: 3;
    top: 0;
    justify-content: right;
    transform: translateY(17px);
    padding-right: 440px;
    gap: 2px;
}

.mostacillas_b {

width: 100%;
  position: absolute;
  display: flex;
  z-index: 3;
  top: 0;
  justify-content: left;
  transform: translateY(17px);
  padding-left: 440px;
  gap: 2px;
}

.hilo-container {
  position: relative;
  width: 800px;
  max-width: 900px;
}



.dijes {
  position: relative;
  width: 70px;
  max-height: 10px;
  left: 50%; 
  transform: translate(-35px, -70px);
  z-index: 3; 
}



</style>