<!DOCTYPE html>
<html>
<head>
  <title>AI Image Generator</title>
  <style>
    body { font-family: Arial; background:#121212; color:#fff; padding:20px; }
    input, button { padding:10px; width:100%; margin-top:10px; }
    img { margin-top:20px; max-width:100%; border-radius:10px; }
  </style>
</head>
<body>
  <h2>AI Image Generator</h2>
  <input id="prompt" placeholder="Enter image prompt...">
  <button onclick="generate()">Generate Image</button>
  <div id="result"></div>

  <script>
    async function generate(){
      document.getElementById("result").innerHTML = "Generating...";
      // BACKEND REQUIRED – ONLY UI TEMPLATE
      setTimeout(()=> {
        document.getElementById("result").innerHTML =
          "<img src='https://placehold.co/600x400?text=AI+Image+Preview'>";
      },2000);
    }
  </script>
</body>
</html>
<!DOCTYPE html>
<html>
<head>
  <title>AI Video Generator</title>
  <style>
    body{ background:#101010; color:white; padding:20px; font-family:Arial; }
    input, textarea, button{ width:100%; padding:10px; margin-top:10px; }
    video{ margin-top:20px; width:100%; border-radius:10px; }
  </style>
</head>
<body>
  <h2>AI Video Generator</h2>
  <textarea id="script" placeholder="Enter video script..."></textarea>
  <button onclick="makeVideo()">Generate Video</button>
  <div id="out"></div>

  <script>
    function makeVideo(){
      document.getElementById("out").innerHTML = "Generating video...";
      setTimeout(()=>{
        document.getElementById("out").innerHTML =
          "<video controls><source src='sample.mp4'></video>";
      }, 3000);
    }
  </script>
</body>
</html>
<!DOCTYPE html>
<html>
<head>
  <title>AI Outfit Changer</title>
  <style>
    body{ font-family:Arial; background:#0d0d0d; color:white; padding:20px; }
    input, button{ width:100%; padding:10px; margin-top:10px; }
    img{ margin-top:20px; width:100%; border-radius:10px; }
  </style>
</head>
<body>
  <h2>AI Outfit Changer Tool</h2>
  <input type="file" id="photo">
  <input id="style" placeholder="Enter outfit style (e.g. black suit)">
  <button onclick="changeOutfit()">Change Outfit</button>
  <div id="preview"></div>

  <script>
    function changeOutfit(){
      document.getElementById("preview").innerHTML =
        "Processing outfit change...";
      setTimeout(()=>{
        document.getElementById("preview").innerHTML =
          "<img src='https://placehold.co/500x600?text=New+Outfit'>";
    },2000);
    }
  </script>
</body>
</html>
!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Voice Generator</title>
    <style>
        :root {
            --bg-color: #0f0f1a;
            --card-bg: #1a1a2e;
            --accent: #00d4ff; /* Cyan accent for voice tools */
            --text: #e0e0e0;
            --secondary: #555;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text);
            font-family: 'Segoe UI', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        .container {
            width: 500px;
            background: var(--card-bg);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            border: 1px solid #333;
            text-align: center;
        }

        h1 {
            color: var(--accent);
            margin-bottom: 20px;
            font-size: 24px;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
        }

        /* Text Input Area */
        textarea {
            width: 100%;
            height: 120px;
            background: #111;
            border: 1px solid #444;
            color: white;
            padding: 15px;
            border-radius: 8px;
            resize: none;
            font-size: 16px;
            margin-bottom: 20px;
            outline: none;
            box-sizing: border-box; /* Fixes padding issues */
        }

        textarea:focus { border-color: var(--accent); }

        /* Controls Grid */
        .controls {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-bottom: 20px;
            text-align: left;
        }

        label { font-size: 12px; color: #aaa; display: block; margin-bottom: 5px; }

        select, input[type="range"] {
            width: 100%;
            background: #222;
            color: white;
            border: 1px solid #444;
            padding: 8px;
            border-radius: 5px;
            outline: none;
        }

        /* Buttons */
        .btn-group {
            display: flex;
            gap: 10px;
            justify-content: center;
        }

        button {
            padding: 12px 25px;
            border: none;
            border-radius: 25px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
            font-size: 16px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .btn-play {
            background: var(--accent);
            color: #000;
        }
        .btn-play:hover { background: #00b8d4; box-shadow: 0 0 15px rgba(0, 212, 255, 0.4); }

        .btn-stop {
            background: #333;
            color: white;
        }
        .btn-stop:hover { background: #444; }

        /* Audio Visualizer Animation */
        .visualizer {
            height: 40px;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 5px;
            margin-top: 20px;
            opacity: 0; /* Hidden by default */
            transition: opacity 0.3s;
        }

        .bar {
            width: 6px;
            height: 10px;
            background: var(--accent);
            border-radius: 3px;
            animation: bounce 0.5s infinite;
        }

        /* Create distinct animations for bars */
        .bar:nth-child(1) { animation-delay: 0.1s; }
        .bar:nth-child(2) { animation-delay: 0.3s; }
        .bar:nth-child(3) { animation-delay: 0.0s; }
        .bar:nth-child(4) { animation-delay: 0.4s; }
        .bar:nth-child(5) { animation-delay: 0.2s; }

        @keyframes bounce {
            0%, 100% { height: 10px; }
            50% { height: 30px; }
        }

        .active .visualizer { opacity: 1; }
    </style>
</head>
<body>

    <div class="container" id="mainContainer">
        <h1>🎙️ AI Voice Generator</h1>
        
        <textarea id="text-input" placeholder="Type something here to convert to speech..."></textarea>

        <div class="controls">
            <div>
                <label>Select Voice</label>
                <select id="voice-select">
                    <option value="">Loading voices...</option>
                </select>
            </div>
            <div>
                <label>Speed (Rate)</label>
                <input type="range" id="rate" min="0.5" max="2" value="1" step="0.1">
            </div>
            <div>
                <label>Pitch</label>
                <input type="range" id="pitch" min="0.5" max="2" value="1" step="0.1">
            </div>
        </div>

        <div class="btn-group">
            <button class="btn-play" onclick="speakText()">▶ Generate Voice</button>
            <button class="btn-stop" onclick="stopText()">⏹ Stop</button>
        </div>

        <div class="visualizer">
            <div class="bar"></div>
            <div class="bar"></div>
            <div class="bar"></div>
            <div class="bar"></div>
            <div class="bar"></div>
        </div>
    </div>

    <script>
        // Initialize Speech API
        const synth = window.speechSynthesis;
        const textInput = document.getElementById('text-input');
        const voiceSelect = document.getElementById('voice-select');
        const rateInput = document.getElementById('rate');
        const pitchInput = document.getElementById('pitch');
        const container = document.getElementById('mainContainer');

        let voices = [];

        // 1. Fetch available browser voices
        function getVoices() {
            voices = synth.getVoices();
            voiceSelect.innerHTML = '';

            // Filter for English voices initially (optional)
            voices.forEach(voice => {
                const option = document.createElement('option');
                option.textContent = `${voice.name} (${voice.lang})`;
                option.setAttribute('data-lang', voice.lang);
                option.setAttribute('data-name', voice.name);
                voiceSelect.appendChild(option);
            });
        }

        // Browsers load voices asynchronously, so we wait for the event
        if (synth.onvoiceschanged !== undefined) {
            synth.onvoiceschanged = getVoices;
        }

        // 2. The Speak Function
        function speakText() {
            // Stop any current audio
            if (synth.speaking) {
                console.error('Already speaking...');
                return;
            }

            if (textInput.value !== '') {
                // Activate visual animation
                container.classList.add('active');

                // Create the utterance object
                const speakText = new SpeechSynthesisUtterance(textInput.value);
                
                // Find selected voice
                const selectedVoiceName = voiceSelect.selectedOptions[0].getAttribute('data-name');
                voices.forEach(voice => {
                    if (voice.name === selectedVoiceName) {
                        speakText.voice = voice;
                    }
                });

                // Set Rate and Pitch
                speakText.rate = rateInput.value;
                speakText.pitch = pitchInput.value;

                // When audio finishes
                speakText.onend = e => {
                    console.log('Done speaking...');
                    container.classList.remove('active');
                };

                // Error handling
                speakText.onerror = e => {
                    console.error('Something went wrong');
                    container.classList.remove('active');
                };

                // Speak!
                synth.speak(speakText);
            }
        }

        // 3. Stop Function
        function stopText() {
            if(synth.speaking) {
                synth.cancel();
                container.classList.remove('active');
            }
        }
        
        // Initial load
        getVoices();
    </script>

</body>
</html>
