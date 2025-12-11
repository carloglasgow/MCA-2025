# [Week 7: Curration Challenges]
## Task 1: Updating last week's metadata
I updated the MEI encoding for "Bros" to enhance its metadata for academic use. The update involved two key additions: a <notesStmt> element to classify the song's genre as "Indie Rock" and "Dream Pop," and a revised <availability> section that properly credits the original publisher (Kobalt Music Publishing) while applying a Creative Commons BY-NC-SA 4.0 license to my own encoding work. These changes bring the file in line with digital musicology standards, making the encoding a clearer, more reusable scholarly resource that distinguishes between the original copyrighted work and my derivative analysis. <br>
You can see the updated MEI file, <a href= "Bros-modified(v2).mei" target="_blank">here</a>

## Task 2: Rendering the Revised Metadata
<body>
  <div id="MEImeta"></div>
  <div id="app" class="panel" style="border: 1px solid light gray; min-height: 800px;">Verovio is loading...</div>
  <script type="module">
        import 'https://www.verovio.org/javascript/app/verovio-app.js';
        
         const app = new Verovio.App(document.getElementById("app"), {});

    // Load a file (MEI or MusicXML)
    fetch("Bros-modified(v2).mei")
        .then(function(response) {
            return response.text();
        })
        .then(function(text) {
            app.loadData(text);
        });
    </script>
  <script>
    // Get, parse, and show TEI data
    var CETEIcean = new CETEI()
    CETEIcean.getHTML5("Bros-modified(v2).mei", function(data) {
      document.getElementById("TEI").appendChild(data)
    })
    // Get, parse and show MEI header data
    var CETEI4MEI = new CETEI()
    CETEI4MEI.addBehaviors({
      namespaces: {
        mei: "http://www.music-encoding.org/ns/mei"
      }
    })
    CETEI4MEI.getHTML5("Bros-modified(v2).mei", function(data) {
      // get header
      var meiHead = data.querySelector('mei-meiHead')
      document.getElementById("MEImeta").appendChild(meiHead)
    })
    var vrvToolkit = new verovio.toolkit()
    vrvToolkit.setOptions(options = {
        pageHeight: 500,
        pageWidth: 1000,
        ignoreLayout: 1,
        border: 20,
        scale: 50,
        adjustPageHeight: true
    })
    fetch("Bros-modified(v2).mei").then(function( response ) {
        response.text().then(function( data ) {
          var svg = vrvToolkit.renderData(data, {})
          document.getElementById('MEI').innerHTML = svg
        })
    })
  </script>

</body>

<footer><p>Score rendering provided by <a href="http://www.verovio.org">Verovio</a>. Metadata rendered by <a href="https://github.com/TEIC/CETEIcean/"> CETEIcean</a>.</p></footer>
