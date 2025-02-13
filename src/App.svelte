<script>
  let clickText = $state();
  let clickTextHeading = $state();
  let showAll = $state(false);

  

  function handleAmpleClick() {
    clickTextHeading = 'Nicht-barrierefreie Fußgängerampeln!';
    clickText = 'In Hamburg sind einige Ampeln noch ohne die bekannten Klickgeräusche ausgestattet. Das macht es fast unmöglich, dass seheingeschränkte Menschen, die Ampel überqueren. Genaue Daten über die Anzahl der "stillen Ampeln" macht die Stadt allerdings nicht.';
  }

  function handleZebraClick() {
    clickTextHeading = 'Fehlendes Audiosignal am Zebrastreifen!';
    clickText = 'Zebrastreifen haben keine auditativen Signale, um einer blinden Person die Verkehrssituation mitzuteilen. Wer in Hamburg schon mal an einem Zebrastreifen stand, weiß das Autos nicht zwangsläufig hier anhalten ';
  }

  function handleBordsteinClick() {
    clickTextHeading = 'Kein abgesengter Bordstein!';
    clickText = 'Hier liegt sogar eine doppelte Einschränkung vor. 1. können Menschen im Rollstuhl oft einen hohen Bordstein nicht überwinden. 2. Ist dadurch der Zugang zur Bushaltestelle nicht barrierefrei. Der Bus kann noch so barrierefrei sein, wenn der Zugang zu der Haltestelle das nicht ist, bringt das nichts.';
  }

  function handleBusClick() {
    clickTextHeading = 'Kein barrierefreier Bus!';
    clickText = 'Busse ohne Rampen und Absenkmechanik würden Menschen mit Bewegungseinschränkungen ausschließen. Im Hamburger Stadtgebiet haben mittlerweile alle Busse eine Absenkmechanik, Rampen und Stellplätze für Rollstühle. Betroffene erzählen allerdings, dass es oft an der Schulung der Busfahrer fehlt, wie sie mit den Betroffenen umgehen sollen.';
  }

  function handleSchotterClick() {
    clickTextHeading = 'Schotter oder Pflastersteine!';
    clickText = 'Bauschutt, Schottersteine durch Baustellenabschnitte oder einfach Pflastersteine können für Personen mit Bewegungseinschränkungen zu einer großen Hürde werden';
  }

  function reset() {
    clickText = '';
  }

  function toggleAllAreas() {
    showAll = !showAll;
  }
</script>

<main>
  <div class="image-container">
    <img src="assets/Kreuzung.png" alt="Interactive Map" width="700" height="500">
    
    <button onclick={toggleAllAreas} class="toggle-button">{showAll ? 'Lösung verbergen' : 'Lösung anzeigen'}</button>
    
    <div
      onclick={handleAmpleClick}
      class="clickable-area"
      style="top: 280px; left: 340px; width: 35px; height: 50px; {showAll ? 'border: 2px solid green;' : ''}"
    ></div>
    <div
      onclick={handleAmpleClick}
      class="clickable-area"
      style="top: 50px; left: 300px; width: 35px; height: 50px; {showAll ? 'border: 2px solid green;' : ''}"
    ></div>
    <div
      onclick={handleZebraClick}
      class="clickable-area"
      style="top: 330px; left: 370px; width: 250px; height: 70px; {showAll ? 'border: 2px solid green;' : ''}"
    ></div>
    <div
      onclick={handleBordsteinClick}
      class="clickable-area"
      style="top: 335px; left: 250px; width: 100px; height: 70px; {showAll ? 'border: 2px solid green;' : ''}"
    ></div>
    <div
      onclick={handleBusClick}
      class="clickable-area"
      style="top: 180px; left: 0px; width: 200px; height: 160px; {showAll ? 'border: 2px solid green;' : ''}"
    ></div>
    <div
      onclick={handleSchotterClick}
      class="clickable-area"
      style="top: 70px; left: 475px; width: 120px; height: 50px; {showAll ? 'border: 2px solid green;' : ''}"
    ></div>
    
    {#if clickText}
      <div class="info-box">
        <button class="close-btn" onclick={reset}>x</button>
        <p class="info-heading">{clickTextHeading}</p>
        <p class="info-text">{clickText}</p>
      </div>
    {/if}
  </div>
</main>

<style>
@import url('https://fonts.googleapis.com/css2?family=Outfit:wght@400;700&display=swap');

    .image-container {
      position: relative;
      display: inline-block;
    }

    .image-container img {
      display: block;
    }

    .clickable-area {
      position: absolute;
      /*background: rgba(255, 255, 255, 0.3);
      border: 2px solid transparent;
      border: 2px solid red;*/
    }

    .info-box {
      position: absolute;
      top: 0;
      left: 0;
      background: white;
      border: 1px solid #ccc;
      box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
      padding: 10px;
      width: 250px;
      height: 355px;
      z-index: 100;
      border-radius: 10px;
      opacity: 0.9
    
      
    }
    .info-heading {
      color: green;
      font-family: Outfit;
    }

    .info-text {
      font-family: Outfit;

    }

    .close-btn {
      position: absolute;
      top: 5px;
      right: 1px;
      cursor: pointer;
      font-weight: bold;
      color: red;
      background-color: rgba(255, 255, 255, 0.0);
    }
  .toggle-button {
    margin-top: 10px;
    padding: 5px 10px;
    background-color: #007BFF;
    color: white;
    border: none;
    cursor: pointer;
    border-radius: 5px;
  }
  .toggle-button:hover {
    background-color: #0056b3;
  }
</style>
