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
    .range([0.4, 1])    // de menos luminoso a totalmente visible

</script>

<main>
  <div class="header">
    
    <h3 class="headline">
      <b>Fin de semana musical</b>
      Cómo leer esta partitura del fin de semana de los jovenes     
    </h3>
    <p class="bajada">
      Este no es un pentagrama tradicional. Es una memoria codificada en música. Cada nota es un joven entrevistado. <br />
      ¿Que música escuchó? ¿Cuánto tiempo? ¿Qué estaba haciendo? ¿Cómo se sintió?<br />
      Para descifrar qué pasó, hay que observar con atención: <br />

      ¿Te animás a leer entre líneas?
    </p>
    </div>
    <div class ="referencias">
      <div class = 'notas'>
      <p><strong>Notas musicales:</strong></p>
      <ul>
        <li><img src="/images/semicorchea.png" width="20" /> estaba entrenando</li>
        <li><img src="/images/corchea.png" width="20" /> estaba en una fiesta</li>
        <li><img src="/images/negra.png" width="20" /> estaba estudiando</li>
        <li><img src="/images/blanca.png" width="20" />  estaba viajando</li>
        <li><img src="/images/redonda.png" width="20" />  estaba haciendo otra cosa</li>
      </ul>
      </div>
      
      <div class = 'generos'>
      <p><strong>Géneros musicales:</strong></p>
      <ul>
        <li style="color: red;">Rock</li>
        <li style="color: blue;">Reggeaton</li>
        <li style="color: green;">Cumbia</li>
        <li style="color: purple;">Electronica</li>
        <li style="color: orange;">Pop</li>
        <li style="color: cyan;">Otro</li>
      </ul>
      </div>

      <div class= 'minutos'>
      <p><strong>Tiempo escuchado:</strong></p>
      <ul>
        <li style= " color : rgba(0, 0, 0, 0.3)"> 15 minutos</li>
        <li style="color: rgba(0, 0, 0, 0.5)"> 30 minutos</li>
        <li style="color : rgba(0, 0, 0, 0.7)"> 1 hora</li>
        <li style="color : rgba(0, 0, 0, 0.9)"> 2 horas</li>
        <li style="color : rgba(0, 0, 0, 1)"> 4 horas</li>
      </ul>
      </div>

      <div class= 'energia'>
      <p><strong>Cuanto le cambio el dia a la persona:</strong></p>
      <ol>
        <li> Primera linea</li>
        <li> Segunda linea</li>
        <li> Tercera linea</li>
        <li> Cuarta linea</li>
        <li> Quinta linea</li>
      </ol>
      </div>

      <div class = 'dia'>
      <p><strong>Dia de la semana:</strong></p>
      <ul>
        <li>Viernes</li>
        <li>Sabado</li>
        <li>Domingo</li>
      </ul>
      </div>
    
  </div>

    <!-- Scroll horizontal Viernes  -->
    <section id="sectionPin1">
      <div class="pin-wrap-sticky">
        <div class="pin-wrap">
          <div class="pentagrama">
            <h2 >
              <b>Viernes</b>
            </h2>
            </div>
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
            {#if d.actividad == "semicorchea"} 
              <svg
                width="100"
                height="100"
                x={80 + i * 80}
                y={energiaToY(d.energia) - 50}
                opacity={brilloScale(d.minutos)}
                viewBox="0 0 86 164" 
                fill={colorScale(d.genero)}
                xmlns="http://www.w3.org/2000/svg"
              >
                <path d="M58 0C64.0995 18.1847 85.7828 21.2927 81.4248 45.4434C87.2557 53.528 88.6326 61.5868 78.8291 76C88.9412 49.3738 78.0588 46.0018 58 34.209V88H56V0H58ZM58.3447 16.5859C65.6117 28.9565 74.4233 36.5251 80.1182 43.7168C79.4262 36.8479 78.9017 26.9955 58.3447 16.5859Z" 
                fill={colorScale(d.genero)} />
                <path
                  d="M27.3233 97.3935C23.7958 92.1509 27.5752 84.6147 35.638 80.5736C43.7007 76.5324 53.1493 77.297 56.6768 82.5395C60.2042 87.7821 56.4248 95.3183 48.362 99.4687C40.2993 103.51 30.8507 102.636 27.3233 97.3935V97.3935Z"
                  fill={colorScale(d.genero)}
                />
              </svg>
             
            {:else if d.actividad == "corchea"}
              <svg
                width="100"
                height="100"
                x={80 + i * 80}
                y={energiaToY(d.energia) - 50}
                opacity={brilloScale(d.minutos)}
                viewBox="0 0 86 164" fill={colorScale(d.genero)} xmlns="http://www.w3.org/2000/svg">
                <path d="M58 0C74.0585 27.8643 98.1481 31.597 78.8291 60C88.9412 33.3738 78.0588 30.0018 58 18.209V88H56V0H58Z" fill={colorScale(d.genero)} />
                <path 
                d="M27.3233 97.3935C23.7958 92.1509 27.5752 84.6147 35.638 80.5736C43.7007 76.5324 53.1493 77.297 56.6768 82.5395C60.2042 87.7821 56.4248 95.3183 48.362 99.4687C40.2993 103.51 30.8507 102.636 27.3233 97.3935V97.3935Z" 
                fill={colorScale(d.genero)}/>
              </svg>
      
            {:else if d.actividad == "negra"}
              <svg
                width="100"
                height="100"
                x={80 + i * 80}
                y={energiaToY(d.energia) - 50}
                opacity={brilloScale(d.minutos)}
                viewBox="0 0 86 180"
                fill={colorScale(d.genero)}
                xmlns="http://www.w3.org/2000/svg"
              >
                <path d="M58 0H56V88H58V0Z" fill={colorScale(d.genero)} />
                <path
                  d="M27.3233 97.3935C23.7958 92.1509 27.5752 84.6147 35.638 80.5736C43.7007 76.5324 53.1493 77.297 56.6768 82.5395C60.2042 87.7821 56.4248 95.3183 48.362 99.4687C40.2993 103.51 30.8507 102.636 27.3233 97.3935V97.3935Z"                   
                  fill={colorScale(d.genero)}
                />
              </svg>
              
            {:else if d.actividad == "blanca"}
            <svg
                width="100"
                height="100"
                x={80 + i * 80}
                y={energiaToY(d.energia) - 50}
                opacity={brilloScale(d.minutos)}
                viewBox="0 0 86 164" fill={colorScale(d.genero)} xmlns="http://www.w3.org/2000/svg">
              
                <path path d="M58 0H56V88H58V0Z" fill={colorScale(d.genero)} />
                <path
                  d="M27.3233 97.3935C23.7958 92.1509 27.5752 84.6147 35.638 80.5736C43.7007 76.5324 53.1493 77.297 56.6768 82.5395C60.2042 87.7821 56.4248 95.3183 48.362 99.4687C40.2993 103.51 30.8507 102.636 27.3233 97.3935V97.3935ZM55.417 83.1949C54.0312 81.0104 46.9762 82.2119 39.6694 85.9254C39.5434 85.9254 39.5434 86.0346 39.4174 86.0346C39.2914 86.0346 39.1654 86.1438 39.1654 86.1438C31.9845 89.8573 27.3233 94.5537 28.835 96.6289C30.2208 98.8133 37.2757 97.6119 44.5826 93.8984C44.7086 93.8984 44.7086 93.7892 44.8346 93.7892L44.9606 93.68C52.1415 90.0757 56.8027 85.3793 55.417 83.1949V83.1949Z" 
                  fill={colorScale(d.genero)}/>
              </svg>
              
            {:else if d.actividad == "redonda"}
            <svg
                width="100"
                height="100"
                x={80 + i * 80}
                y={energiaToY(d.energia) - 50}
                opacity={brilloScale(d.minutos)}
                viewBox="0 0 86 164"
                fill={colorScale(d.genero)}
                xmlns="http://www.w3.org/2000/svg"              >
                <path
                  d="M32.0974 100.514C26.4533 98.8054 22 94.1609 22 89.9836C22 78.1601 47.8128 73.4812 58.4729 83.3725C70.0004 94.0687 51.188 106.295 32.0974 100.514H32.0974ZM49.3147 97.5442C52.4551 92.8287 49.4526 83.486 44.0131 81.0476C36.025 77.4667 31.1285 83.5689 34.4555 92.9586C36.7567 99.4532 46.1191 102.343 49.3147 97.5442Z"           
                  fill={colorScale(d.genero)}
                />
              </svg>
              
            {/if}
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
          <div class="pentagrama">
            <h2 >
              <b>Sabado</b>
            </h2>
            </div>
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
               {#if d.actividad == "semicorchea"} 
              <svg
                width="100"
                height="100"
                x={80 + i * 80}
                y={energiaToY(d.energia) - 50}
                opacity={brilloScale(d.minutos)}
                viewBox="0 0 86 164" 
                fill={colorScale(d.genero)}
                xmlns="http://www.w3.org/2000/svg"
              >
                <path d="M58 0C64.0995 18.1847 85.7828 21.2927 81.4248 45.4434C87.2557 53.528 88.6326 61.5868 78.8291 76C88.9412 49.3738 78.0588 46.0018 58 34.209V88H56V0H58ZM58.3447 16.5859C65.6117 28.9565 74.4233 36.5251 80.1182 43.7168C79.4262 36.8479 78.9017 26.9955 58.3447 16.5859Z" 
                fill={colorScale(d.genero)} />
                <path
                  d="M27.3233 97.3935C23.7958 92.1509 27.5752 84.6147 35.638 80.5736C43.7007 76.5324 53.1493 77.297 56.6768 82.5395C60.2042 87.7821 56.4248 95.3183 48.362 99.4687C40.2993 103.51 30.8507 102.636 27.3233 97.3935V97.3935Z"
                  fill={colorScale(d.genero)}
                />
              </svg>
             
            {:else if d.actividad == "corchea"}
              <svg
                width="100"
                height="100"
                x={80 + i * 80}
                y={energiaToY(d.energia) - 50}
                opacity={brilloScale(d.minutos)}
                viewBox="0 0 86 164" fill={colorScale(d.genero)} xmlns="http://www.w3.org/2000/svg">
                <path d="M58 0C74.0585 27.8643 98.1481 31.597 78.8291 60C88.9412 33.3738 78.0588 30.0018 58 18.209V88H56V0H58Z" fill={colorScale(d.genero)} />
                <path 
                d="M27.3233 97.3935C23.7958 92.1509 27.5752 84.6147 35.638 80.5736C43.7007 76.5324 53.1493 77.297 56.6768 82.5395C60.2042 87.7821 56.4248 95.3183 48.362 99.4687C40.2993 103.51 30.8507 102.636 27.3233 97.3935V97.3935Z" 
                fill={colorScale(d.genero)}/>
              </svg>
      
            {:else if d.actividad == "negra"}
              <svg
                width="100"
                height="100"
                x={80 + i * 80}
                y={energiaToY(d.energia) - 50}
                opacity={brilloScale(d.minutos)}
                viewBox="0 0 86 180"
                fill={colorScale(d.genero)}
                xmlns="http://www.w3.org/2000/svg"
              >
                <path d="M58 0H56V88H58V0Z" fill={colorScale(d.genero)} />
                <path
                  d="M27.3233 97.3935C23.7958 92.1509 27.5752 84.6147 35.638 80.5736C43.7007 76.5324 53.1493 77.297 56.6768 82.5395C60.2042 87.7821 56.4248 95.3183 48.362 99.4687C40.2993 103.51 30.8507 102.636 27.3233 97.3935V97.3935Z"                   
                  fill={colorScale(d.genero)}
                />
              </svg>
              
            {:else if d.actividad == "blanca"}
            <svg
                width="100"
                height="100"
                x={80 + i * 80}
                y={energiaToY(d.energia) - 50}
                opacity={brilloScale(d.minutos)}
                viewBox="0 0 86 164" fill={colorScale(d.genero)} xmlns="http://www.w3.org/2000/svg">
              
                <path path d="M58 0H56V88H58V0Z" fill={colorScale(d.genero)} />
                <path
                  d="M27.3233 97.3935C23.7958 92.1509 27.5752 84.6147 35.638 80.5736C43.7007 76.5324 53.1493 77.297 56.6768 82.5395C60.2042 87.7821 56.4248 95.3183 48.362 99.4687C40.2993 103.51 30.8507 102.636 27.3233 97.3935V97.3935ZM55.417 83.1949C54.0312 81.0104 46.9762 82.2119 39.6694 85.9254C39.5434 85.9254 39.5434 86.0346 39.4174 86.0346C39.2914 86.0346 39.1654 86.1438 39.1654 86.1438C31.9845 89.8573 27.3233 94.5537 28.835 96.6289C30.2208 98.8133 37.2757 97.6119 44.5826 93.8984C44.7086 93.8984 44.7086 93.7892 44.8346 93.7892L44.9606 93.68C52.1415 90.0757 56.8027 85.3793 55.417 83.1949V83.1949Z" 
                  fill={colorScale(d.genero)}/>
              </svg>
              
            {:else if d.actividad == "redonda"}
            <svg
                width="100"
                height="100"
                x={80 + i * 80}
                y={energiaToY(d.energia) - 50}
                opacity={brilloScale(d.minutos)}
                viewBox="0 0 86 164"
                fill={colorScale(d.genero)}
                xmlns="http://www.w3.org/2000/svg"              >
                <path
                  d="M32.0974 100.514C26.4533 98.8054 22 94.1609 22 89.9836C22 78.1601 47.8128 73.4812 58.4729 83.3725C70.0004 94.0687 51.188 106.295 32.0974 100.514H32.0974ZM49.3147 97.5442C52.4551 92.8287 49.4526 83.486 44.0131 81.0476C36.025 77.4667 31.1285 83.5689 34.4555 92.9586C36.7567 99.4532 46.1191 102.343 49.3147 97.5442Z"           
                  fill={colorScale(d.genero)}
                />
              </svg>
              
            {/if}
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
       <div class="pentagrama">
            <h2 >
              <b>Domingo
            </h2>
        </div>
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
             {#if d.actividad == "semicorchea"} 
              <svg
                width="100"
                height="100"
                x={80 + i * 80}
                y={energiaToY(d.energia) - 50}
                opacity={brilloScale(d.minutos)}
                viewBox="0 0 86 164" 
                fill={colorScale(d.genero)}
                xmlns="http://www.w3.org/2000/svg"
              >
                <path d="M58 0C64.0995 18.1847 85.7828 21.2927 81.4248 45.4434C87.2557 53.528 88.6326 61.5868 78.8291 76C88.9412 49.3738 78.0588 46.0018 58 34.209V88H56V0H58ZM58.3447 16.5859C65.6117 28.9565 74.4233 36.5251 80.1182 43.7168C79.4262 36.8479 78.9017 26.9955 58.3447 16.5859Z" 
                fill={colorScale(d.genero)} />
                <path
                  d="M27.3233 97.3935C23.7958 92.1509 27.5752 84.6147 35.638 80.5736C43.7007 76.5324 53.1493 77.297 56.6768 82.5395C60.2042 87.7821 56.4248 95.3183 48.362 99.4687C40.2993 103.51 30.8507 102.636 27.3233 97.3935V97.3935Z"
                  fill={colorScale(d.genero)}
                />
              </svg>
             
            {:else if d.actividad == "corchea"}
              <svg
                width="100"
                height="100"
                x={80 + i * 80}
                y={energiaToY(d.energia) - 50}
                opacity={brilloScale(d.minutos)}
                viewBox="0 0 86 164" fill={colorScale(d.genero)} xmlns="http://www.w3.org/2000/svg">
                <path d="M58 0C74.0585 27.8643 98.1481 31.597 78.8291 60C88.9412 33.3738 78.0588 30.0018 58 18.209V88H56V0H58Z" fill={colorScale(d.genero)} />
                <path 
                d="M27.3233 97.3935C23.7958 92.1509 27.5752 84.6147 35.638 80.5736C43.7007 76.5324 53.1493 77.297 56.6768 82.5395C60.2042 87.7821 56.4248 95.3183 48.362 99.4687C40.2993 103.51 30.8507 102.636 27.3233 97.3935V97.3935Z" 
                fill={colorScale(d.genero)}/>
              </svg>
      
            {:else if d.actividad == "negra"}
              <svg
                width="100"
                height="100"
                x={80 + i * 80}
                y={energiaToY(d.energia) - 50}
                opacity={brilloScale(d.minutos)}
                viewBox="0 0 86 180"
                fill={colorScale(d.genero)}
                xmlns="http://www.w3.org/2000/svg"
              >
                <path d="M58 0H56V88H58V0Z" fill={colorScale(d.genero)} />
                <path
                  d="M27.3233 97.3935C23.7958 92.1509 27.5752 84.6147 35.638 80.5736C43.7007 76.5324 53.1493 77.297 56.6768 82.5395C60.2042 87.7821 56.4248 95.3183 48.362 99.4687C40.2993 103.51 30.8507 102.636 27.3233 97.3935V97.3935Z"                   
                  fill={colorScale(d.genero)}
                />
              </svg>
              
            {:else if d.actividad == "blanca"}
            <svg
                width="100"
                height="100"
                x={80 + i * 80}
                y={energiaToY(d.energia) - 50}
                opacity={brilloScale(d.minutos)}
                viewBox="0 0 86 164" fill={colorScale(d.genero)} xmlns="http://www.w3.org/2000/svg">
              
                <path path d="M58 0H56V88H58V0Z" fill={colorScale(d.genero)} />
                <path
                  d="M27.3233 97.3935C23.7958 92.1509 27.5752 84.6147 35.638 80.5736C43.7007 76.5324 53.1493 77.297 56.6768 82.5395C60.2042 87.7821 56.4248 95.3183 48.362 99.4687C40.2993 103.51 30.8507 102.636 27.3233 97.3935V97.3935ZM55.417 83.1949C54.0312 81.0104 46.9762 82.2119 39.6694 85.9254C39.5434 85.9254 39.5434 86.0346 39.4174 86.0346C39.2914 86.0346 39.1654 86.1438 39.1654 86.1438C31.9845 89.8573 27.3233 94.5537 28.835 96.6289C30.2208 98.8133 37.2757 97.6119 44.5826 93.8984C44.7086 93.8984 44.7086 93.7892 44.8346 93.7892L44.9606 93.68C52.1415 90.0757 56.8027 85.3793 55.417 83.1949V83.1949Z" 
                  fill={colorScale(d.genero)}/>
              </svg>
              
            {:else if d.actividad == "redonda"}
            <svg
                width="100"
                height="100"
                x={80 + i * 80}
                y={energiaToY(d.energia) - 50}
                opacity={brilloScale(d.minutos)}
                viewBox="0 0 86 164"
                fill={colorScale(d.genero)}
                xmlns="http://www.w3.org/2000/svg"              >
                <path
                  d="M32.0974 100.514C26.4533 98.8054 22 94.1609 22 89.9836C22 78.1601 47.8128 73.4812 58.4729 83.3725C70.0004 94.0687 51.188 106.295 32.0974 100.514H32.0974ZM49.3147 97.5442C52.4551 92.8287 49.4526 83.486 44.0131 81.0476C36.025 77.4667 31.1285 83.5689 34.4555 92.9586C36.7567 99.4532 46.1191 102.343 49.3147 97.5442Z"           
                  fill={colorScale(d.genero)}
                />
              </svg>
              
            {/if}
          {/each}
        </svg>
      </div>
    </div>
  </section>
</main>

<style>
  .referencias {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(4, 1fr);
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    grid-template-areas:
      "notas generos minutos "
      "notas generos minutos "
      " energia dia  ."
      " energia dia .";
     gap: 10px;
     padding: 15px;
    justify-content: center; /* Centra horizontalmente el grid */
    align-content: center; 
    position: relative;
    font-family: 'Karla', sans-serif;
   }
  .notas {
    grid-area: notas;
    font-size: 20px;
    font-weight: 300;
    margin: 10px;
    color: black;
  }
  .notas ul {
  list-style: none;
  padding-left: 0;
  }
  
  .generos {
    grid-area: generos;
    font-size: 20px;
    font-weight: 300;
    margin: 10px;
    color: black;
  }
  .minutos {
    grid-area: minutos;
    font-size: 20px;
    font-weight: 300;
    margin: 10px;
    color: black;
  }
  .energia {
    grid-area: energia;
    font-size: 20px;
    font-weight: 300;
    margin: 10px;
    color: black;
  }
  .dia {
    grid-area: dia;
    font-size: 20px;
    font-weight: 300;
    margin: 10px;
    color: black;
  }
  .header {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    margin-top: 20px;
    margin-bottom: 80px;
  }

.headline {
  font-size: 48px;
  font-weight: 700;
  margin-bottom: 20px;
  text-align: center;
  color: #222;
}

.bajada {
  font-size: 20px;
  font-weight: 300;
  line-height: 1.6;
  max-width: 800px;
  margin: 0 auto 60px auto;
  text-align: center;
  color: #444;
  font-family: 'Karla', sans-serif;
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
  height: 100vh;
  width: 2200px; /* igual al ancho del SVG */
  will-change: transform;
  display: flex;
  align-items: center;
  justify-content: center;
  
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
svg {
  display: block;
  margin: 0 auto;
}
.pentagrama{
  position: absolute;
  top: 20px;
  left: 20px;
  font-size: 24px;
  font-weight: bold;
  color: black;
  align-items: center
}
</style>
