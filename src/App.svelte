<script>
  import * as d3 from "d3"
  

  

  function energiaToY(energia) {
    return 180 - (energia - 1) * 30;
  }

  let viernes = [
  {"persona": 1, "minutos": 2, "genero": "Electronica", "actividad": "semicorchea", "energia": 5},
  {"persona": 2, "minutos": 4, "genero": "Reggeaton", "actividad": "corchea", "energia": 4},
  {"persona": 3, "minutos": 2, "genero": "Otro", "actividad": "corchea", "energia": 3},
  {"persona": 4, "minutos": 4, "genero": "Cumbia", "actividad": "corchea", "energia": 5},
  {"persona": 5, "minutos": 4, "genero": "Reggeaton", "actividad": "corchea", "energia": 4},
  {"persona": 6, "minutos": 0.25, "genero": "Rock", "actividad": "blanca", "energia": 3},
  {"persona": 7, "minutos": 0.25, "genero": "Rock", "actividad": "blanca", "energia": 3},
  {"persona": 8, "minutos": 0.25, "genero": "Pop", "actividad": "semicorchea", "energia": 5},
  {"persona": 9, "minutos": 1, "genero": "Otro", "actividad": "semicorchea", "energia": 4},
  {"persona": 10, "minutos": 2, "genero": "Rock", "actividad": "semicorchea", "energia": 4},
  {"persona": 11, "minutos": 2, "genero": "Rock", "actividad": "semicorchea", "energia": 5},
  {"persona": 12, "minutos": 1, "genero": "Reggeaton", "actividad": "blanca", "energia": 4},
  {"persona": 13, "minutos": 0.5, "genero": "Reggeaton", "actividad": "blanca", "energia": 5},
  {"persona": 14, "minutos": 4, "genero": "Rock", "actividad": "blanca", "energia": 4},
  {"persona": 15, "minutos": 2, "genero": "Cumbia", "actividad": "blanca", "energia": 3},
  {"persona": 16, "minutos": 1, "genero": "Otro", "actividad": "blanca", "energia": 2},
  {"persona": 17, "minutos": 1, "genero": "Cumbia", "actividad": "redonda", "energia": 5},
  {"persona": 18, "minutos": 1, "genero": "Reggeaton", "actividad": "redonda", "energia": 3},
  {"persona": 19, "minutos": 4, "genero": "Pop", "actividad": "blanca", "energia": 5},
  {"persona": 20, "minutos": 4, "genero": "Rock", "actividad": "redonda", "energia": 4},
  {"persona": 21, "minutos": 1, "genero": "Rock", "actividad": "blanca", "energia": 4},
  {"persona": 22, "minutos": 1, "genero": "Rock", "actividad": "blanca", "energia": 3},
  {"persona": 23, "minutos": 4, "genero": "Reggeaton", "actividad": "corchea", "energia": 4},
  {"persona": 24, "minutos": 4, "genero": "Reggeaton", "actividad": "negra", "energia": 4}
  ]
  let sabado =[
  {"persona": 1, "minutos": 4, "genero": "Cumbia", "actividad": "blanca", "energia": 3},
  {"persona": 2, "minutos": 2, "genero": "Cumbia", "actividad": "redonda", "energia": 3},
  {"persona": 3, "minutos": 0.5, "genero": "Cumbia", "actividad": "redonda", "energia": 4},
  {"persona": 4, "minutos": 4, "genero": "Cumbia", "actividad": "corchea", "energia": 5},
  {"persona": 5, "minutos": 0.5, "genero": "Rock", "actividad": "redonda", "energia": 3},
  {"persona": 6, "minutos": 4, "genero": "Cumbia", "actividad": "corchea", "energia": 5},
  {"persona": 7, "minutos": 0.5, "genero": "Reggeaton", "actividad": "semicorchea", "energia": 4},
  {"persona": 8, "minutos": 0.5, "genero": "Cumbia", "actividad": "corchea", "energia": 5},
  {"persona": 9, "minutos": 1, "genero": "Otro", "actividad": "semicorchea", "energia": 4},
  {"persona": 10, "minutos": 2, "genero": "Rock", "actividad": "semicorchea", "energia": 4},
  {"persona": 11, "minutos": 1, "genero": "Otro", "actividad": "negra", "energia": 4},
  {"persona": 12, "minutos": 1, "genero": "Reggeaton", "actividad": "blanca", "energia": 3},
  {"persona": 13, "minutos": 0.25, "genero": "Rock", "actividad": "semicorchea", "energia": 3},
  {"persona": 14, "minutos": 1, "genero": "Rock", "actividad": "semicorchea", "energia": 5},
  {"persona": 15, "minutos": 2, "genero": "Cumbia", "actividad": "blanca", "energia": 3},
  {"persona": 16, "minutos": 0.5, "genero": "Otro", "actividad": "redonda", "energia": 1},
  {"persona": 17, "minutos": 0.25, "genero": "Otro", "actividad": "corchea", "energia": 3},
  {"persona": 18, "minutos": 2, "genero": "Reggeaton", "actividad": "corchea", "energia": 4},
  {"persona": 19, "minutos": 4, "genero": "Reggeaton", "actividad": "blanca", "energia": 5},
  {"persona": 20, "minutos": 2, "genero": "Reggeaton", "actividad": "corchea", "energia": 3},
  {"persona": 21, "minutos": 2, "genero": "Rock", "actividad": "redonda", "energia": 4},
  {"persona": 22, "minutos": 1, "genero": "Electronica", "actividad": "blanca", "energia": 4},
  {"persona": 23, "minutos": 4, "genero": "Pop", "actividad": "corchea", "energia": 4},
  {"persona": 24, "minutos": 4, "genero": "Reggeaton", "actividad": "negra", "energia": 4}
  ]
  let domingo = [
  {"persona": 1, "minutos": 0.5, "genero": "Pop", "actividad": "blanca", "energia": 2},
  {"persona": 2, "minutos": 1, "genero": "Rock", "actividad": "negra", "energia": 2},
  {"persona": 3, "minutos": 0.25, "genero": "Rock", "actividad": "redonda", "energia": 3},
  {"persona": 4, "minutos": 4, "genero": "Cumbia", "actividad": "corchea", "energia": 5},
  {"persona": 5, "minutos": 0.5, "genero": "Rock", "actividad": "blanca", "energia": 3},
  {"persona": 6, "minutos": 0.25, "genero": "Cumbia", "actividad": "redonda", "energia": 4},
  {"persona": 7, "minutos": 0.25, "genero": "Pop", "actividad": "redonda", "energia": 3},
  {"persona": 8, "minutos": 1, "genero": "Rock", "actividad": "redonda", "energia": 5},
  {"persona": 9, "minutos": 1, "genero": "Pop", "actividad": "semicorchea", "energia": 4},
  {"persona": 10, "minutos": 4, "genero": "Rock", "actividad": "blanca", "energia": 5},
  {"persona": 11, "minutos": 2, "genero": "Rock", "actividad": "semicorchea", "energia": 5},
  {"persona": 12, "minutos": 1, "genero": "Reggeaton", "actividad": "blanca", "energia": 3},
  {"persona": 13, "minutos": 1, "genero": "Rock", "actividad": "negra", "energia": 5},
  {"persona": 14, "minutos": 0.25, "genero": "Reggeaton", "actividad": "redonda", "energia": 1},
  {"persona": 15, "minutos": 2, "genero": "Cumbia", "actividad": "blanca", "energia": 3},
  {"persona": 16, "minutos": 0.25, "genero": "Electronica", "actividad": "redonda", "energia": 1},
  {"persona": 17, "minutos": 0.5, "genero": "Rock", "actividad": "blanca", "energia": 3},
  {"persona": 18, "minutos": 2, "genero": "Rock", "actividad": "blanca", "energia": 3},
  {"persona": 19, "minutos": 2, "genero": "Pop", "actividad": "redonda", "energia": 5},
  {"persona": 20, "minutos": 2, "genero": "Rock", "actividad": "negra", "energia": 3},
  {"persona": 21, "minutos": 0.5, "genero": "Rock", "actividad": "redonda", "energia": 3},
  {"persona": 22, "minutos": 0.5, "genero": "Rock", "actividad": "redonda", "energia": 4},
  {"persona": 23, "minutos": 2, "genero": "Rock", "actividad": "redonda", "energia": 2},
  {"persona": 24, "minutos": 4, "genero": "Pop", "actividad": "negra", "energia": 4}
]

  // Escala de color por género (puede ser categórica)
  const colorScale = d3.scaleOrdinal()
    .domain(["Rock", "Reggeaton", "Cumbia", "Electronica", "Pop", "Otro"])
    .range(["red", "blue", "green", "purple", "orange", "cyan"]); 

  // Escala de luminosidad (minutos escuchados)
  const brilloScale = d3.scaleLinear()
    .domain([0.25, 4])  // mínimo y máximo de minutos
    .range([0.3, 1])    // de menos luminoso a totalmente visible

</script>

<main>
  <div class="header">
    
    <h3 class="headline">
      <b>Fin de semana musical</b>
      Cómo leer esta partitura del fin de semana de los jovenes     
    </h3>
    <p class="bajada">
      Este no es un pentagrama tradicional. Es una memoria codificada en música.
      Cada nota es un joven entrevistado. ¿Que música escuchó? ¿Cuánto tiempo? ¿Qué estaba haciendo? ¿Cómo se sintió?
      Para descifrar qué pasó, hay que observar con atención:

      ¿Te animás a leer entre líneas?
    </p>
    <img
      class="referencias"
      src="/images/referencias.svg"
      width="490"
      alt="anillos"
    />
  </div>

    <!-- Scroll horizontal Viernes  -->
    <section id="sectionPin1">
      <div class="pin-wrap-sticky">
        <div class="pin-wrap">
          <h2 class="headline">
            <b>Viernes</b>
          </h2>
          <svg width="2200" height="200">
      
            <!-- Dibujar las 5 líneas del pentagrama -->
            {#each Array(5) as _, i}
              <line 
                x1="0" 
                y1={180 - i * 30} 
                x2="2100" 
                y2={180 - i * 30} 
                stroke="black" 
                stroke-width="2" />
            {/each}
            <!-- las notas -->
            {#each viernes as d, i}
              <image
                href={`/images/${d.actividad}.png`}
                x={80 + i * 80}
                y={energiaToY(d.energia) - 50}  
                width="100"
                height="100"
                style="color: {colorScale(d.genero)}"
                opacity={brilloScale(d.minutos)}
              />
            {/each}
          </svg>
        </div>
      </div>

    </section>

    <!-- ENTRE PENTAGRAMAS -->
    <section class="normal-scroll">
      <h2>Transición</h2>
      <p>Acá sigue el scroll vertical por un momento antes del próximo pentagrama.</p>
    </section>


    <!-- Scroll horizontal Sabado  -->
    <section id="sectionPin2">
      <div class="pin-wrap-sticky">
        <div class="pin-wrap">
          <h2 class="pentagrama-titulo"><b>Sabado</b></h2>
          <svg width="2200" height="200">
            <!-- líneas y notas del segundo pentagrama -->
            {#each Array(5) as _, i}
              <line 
                x1="0" 
                y1={180 - i * 30} 
                x2="2100" 
                y2={180 - i * 30} 
                stroke="black" 
                stroke-width="2" />
            {/each}
            <!-- Dibujar las notas como imágenes -->
            {#each sabado as d, i}
              <image
                href={`/images/${d.actividad}.png`}
                x={80 + i * 80}
                y={energiaToY(d.energia) - 50}  
                width="100"
                height="100"
                fill={colorScale(d.genero)}
                opacity={brilloScale(d.minutos)}
              />
            {/each}
          </svg>
        </div>
      </div>
  </section>

  <!-- ENTRE PENTAGRAMAS -->
  <section class="normal-scroll">
    <h2>Transición</h2>
    <p>Acá sigue el scroll vertical por un momento antes del próximo pentagrama.</p>
  </section>


  <!-- Scroll horizontal Domingo -->
  <section id="sectionPin3">
    <div class="pin-wrap-sticky">
      <div class="pin-wrap">
        <h2 class="pentagrama-titulo"><b>Domingo</b></h2>
        <svg width="2200" height="200">
          <!-- líneas y notas del segundo pentagrama -->
          {#each Array(5) as _, i}
            <line 
              x1="0" 
              y1={180 - i * 30} 
              x2="2100" 
              y2={180 - i * 30} 
              stroke="black" 
              stroke-width="2" />
          {/each}
          <!-- Dibujar las notas como imágenes -->
          {#each domingo as d, i}
            <image
              href={`/images/${d.actividad}.png`}
              x={80 + i * 80}
              y={energiaToY(d.energia) - 50}  
              width="100"
              height="100"
              fill={colorScale(d.genero)}
              opacity={brilloScale(d.minutos)}
            />
          {/each}
        </svg>
      </div>
    </div>
  </section>
</main>

<style>
  .header {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    margin-top: 20px;
    margin-bottom: 80px;
  }

  .headline {
  top: 40px;
  left: 40px; /* aparece al principio del pentagrama */
  font-size: 40px;
  color: black;
  z-index: 10;
  }

  .bajada {
    font-size: 24px;
    font-weight: 300;
    text-align: center;
    margin: 10px;
  }
  .headline b {
    display: block;
  }

  @keyframes move {
  to {
    transform: translateX(calc(-100% + 100vw));
  }
}

#sectionPin1, #sectionPin2, #sectionPin3 {
  height: 500vh;
  overflow: visible;

  view-timeline-axis: block;
}

#sectionPin1 {
  view-timeline-name: --section-pin-1;
}
#sectionPin2 {
  view-timeline-name: --section-pin-2;
}
#sectionPin3 {
  view-timeline-name: --section-pin-3;
}

.pin-wrap-sticky {
  position: sticky;
  top: 0;
  height: 100vh;
  width: 100vw;
  background-color: white;
  
}

.pin-wrap {
  height: 200px;
  width: 2200px; /* igual al ancho del SVG */
  will-change: transform;

  animation: linear move forwards;
  animation-timeline: --section-pin-tl;
  animation-range: contain 0% contain 100%;
}
#sectionPin1 .pin-wrap {
  animation-timeline: --section-pin-1;
}
#sectionPin2 .pin-wrap {
  animation-timeline: --section-pin-2;
}
#sectionPin3 .pin-wrap {
  animation-timeline: --section-pin-3;
}

</style>
