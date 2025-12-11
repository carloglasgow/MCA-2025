# [Week 7: Curration Challenges]
## Task 1: Updating last week's metadata
I updated the MEI encoding for "Bros" to enhance its metadata for academic use. The update involved two key additions: a <notesStmt> element to classify the song's genre as "Indie Rock" and "Dream Pop," and a revised <availability> section that properly credits the original publisher (Kobalt Music Publishing) while applying a Creative Commons BY-NC-SA 4.0 license to my own encoding work. These changes bring the file in line with digital musicology standards, making the encoding a clearer, more reusable scholarly resource that distinguishes between the original copyrighted work and my derivative analysis. <br>
You can see the updated MEI file, <a href= "Bros-modified(v2).mei" target="_blank">here</a>

## Task 2: Rendering the Revised 
<body>
<style>
mei-titlestmt > mei-composer::before {
	content: "Artist:";
	font-family: Arial;
	font-weight: bold;
    }  
mei-titlestmt > mei-arranger {
	display: block;
    }

mei-titlestmt > mei-arranger::before {
	content: "Arrangement by:";
	font-family: Arial;
	font-weight: bold;
    }
mei-titlestmt > mei-respstmt > mei-resp {
	display: none;
    }

mei-titlestmt >  mei-respstmt > mei-name {
	display:block;
	margin-bottom:30px;
	  }

mei-titlestmt >  mei-respstmt > mei-name::before {
	content: "Encoded by:";
	font-family: Arial;
	font-weight: bold;
	
    }	
mei-extent {
	display:none;}
	  
mei-editionstmt > mei-title::before {
	content: "Source of Transcription";
	text-transform: uppercase;
	font-family: Arial Black;
	font-size: 12px;
	display:block;
	  }


mei-editionstmt > mei-title[type="subtitle"]::before {
	content:"";
	  }
	  
mei-editionstmt > #subtitle {
	display:block;
	  }
	 
mei-editionstmt > mei-arranger::before {
	content: "Arranger:";
	font-family: Arial;
	font-weight: bold;
	  }
	  
mei-editionstmt > mei-arranger {
	display:block;
	  }
	  
mei-editionstmt > mei-respstmt > mei-resp {
	display:none;
	  }
	  
mei-editionstmt > mei-respstmt > mei-name::before {
	content: "Published on:";
	font-family: Arial;
	font-weight: bold;
	  }
	  
mei-editionstmt > mei-respstmt > mei-name {
	display: block;
	margin-bottom: 30px;
	  }
	  
mei-editionstmt > mei-date {
	display: none;
	  }
	  
mei-pubstmt > mei-publisher {
	display: none; }
	  
mei-pubstmt > mei-date::before {
	content:",";
	  }
	  
mei-pubstmt > mei-availability > mei-userestrict::before {
	content: "This file is protected under";
	font-style: italic;
	  }
	  
mei-pubstmt > mei-availability > mei-userestrict {
	display: block;
	font-style: italic;
	  }
	  
mei-seriesstmt > mei-title {
	display: none;
	  }
	  
mei-seriesstmt > mei-content {
	display: none;
	  }
	  
mei-seriesstmt > mei-editor {
	display: none;
	  }
	  
mei-application > mei-name {
	display: none;
	  }
	  
mei-application > mei-project {
	display: none;
	  }
	  
mei-appinfo > mei-projectdesc {
	display: block;
	font-style: italic;
	margin-bottom: 30px;
	  }
	  
mei-appinfo > mei-application > mei-p {
	display:none;
	  }

mei-worklist > mei-title::before {
	content: "Original Piece of Work";
	text-transform: uppercase;
	font-family: Arial Black;
	font-size: 12px;
	display:block;
	  }
mei-worklist > mei-title {
	display: block;
	  }
	  
mei-worklist > mei-composer::before {
	content: "Artist:";
	font-family: Arial;
	font-weight: bold;
	  }
	
mei-worklist > mei-composer {
	display:block ;
	  }

mei-worklist > mei-lyricst {
	display: block;
	  }
	  
mei-worklist > mei-lyricst::before {
	content: "Lyrics:";
	font-family: Arial;
	font-weight: bold;
	  }
	  
mei-worklist > mei-creation > mei-date::before {
	content: "Released:";
	font-family: Arial;
	font-weight: bold;
	  }
	  
mei-worklist > mei-creation > mei-date {
	display: block;
	  }
	  
mei-worklist > mei-creation > mei-geogname {
	display:block;
	  }
	  
mei-worklist > mei-creation > mei-geogname::before {
	content: "Location:";
	font-family: Arial;
	font-weight: bold;
	  }
	  
mei-worklist > mei-classification > mei-genre {
	display: block;
	margin-bottom: 15px;
	  }
	  
mei-worklist > mei-classification > mei-genre::before {
	content: "Genre:";
	font-family: Arial;
	font-weight: bold;
	
	  }
</style>

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
