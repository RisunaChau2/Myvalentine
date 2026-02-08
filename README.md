J john was right when he said:<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A special message for you...</title>
    <style>
        body { font-family: 'Arial', sans-serif; text-align: center; background-color: #ffe6e6; display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100vh; overflow: hidden; margin: 0; }
        .container { max-width: 600px; padding: 20px; z-index: 2; }
        .video-wrapper { position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; border-radius: 15px; margin-bottom: 20px; box-shadow: 0 10px 30px rgba(0,0,0,0.1); }
        .video-wrapper iframe { position: absolute; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none; }
        .buttons { display: flex; gap: 20px; justify-content: center; align-items: center; margin-top: 20px; position: relative; }
        #yesBtn { background-color: #ff4d4d; color: white; border: none; padding: 15px 30px; font-size: 18px; border-radius: 10px; cursor: pointer; transition: transform 0.2s ease-out; z-index: 1000; position: relative; font-weight: bold; }
        #noBtn { background-color: #808080; color: white; border: none; padding: 15px 30px; font-size: 18px; border-radius: 10px; cursor: pointer; position: relative; z-index: 1; }
        h1 { color: #d63384; font-size: 1.6rem; line-height: 1.4; }
        b { font-weight: 900; color: #b0005d; text-shadow: 1px 1px 2px rgba(0,0,0,0.1); }
        #overlay { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(255,230,230,0.98); z-index: 9999; display: flex; flex-direction: column; align-items: center; justify-content: center; cursor: pointer; }
    </style>
</head>
<body>

<div id="overlay" onclick="startEverything()">
    <h2 style="color: #d63384;">Tap to open your message ❤️</h2>
    <p>Turn your volume up!</p>
</div>

<div id="main-content" class="container">
    <div class="video-wrapper">
        <iframe id="videoPlayer" src="https://www.youtube.com/embed/V9PVRfjEBTI?enablejsapi=1&loop=1&playlist=V9PVRfjEBTI" frameborder="0" allow="autoplay; encrypted-media"></iframe>
    </div>
    
    <h1 id="question">Will you be my Valentine... also add **the one you love the most**? 🌹</h1>
    
    <div class="buttons">
        <button id="yesBtn" onclick="celebrate()">Yes</button>
        <button id="noBtn" onclick="makeYesBigger()">No</button>
    </div>
</div>

<script>
    let scale = 1;
    const player = document.getElementById('videoPlayer');

    function startEverything() {
        document.getElementById('overlay').style.display = 'none';
        player.src += "&autoplay=1&mute=0";
    }

    function makeYesBigger() {
        const yesBtn = document.getElementById('yesBtn');
        const noBtn = document.getElementById('noBtn');
        scale += 4.5; 
        yesBtn.style.transform = `scale(${scale})`;
        
        const messages = ["You sure?", "Think again!", "Sticky together?", "No choice now!", "Just click Yes!"];
        noBtn.innerText = messages[Math.floor(Math.random() * messages.length)];
        
        // Push the No button further away as Yes grows
        noBtn.style.transform = `translateX(${scale * 10}px)`;
    }

    function celebrate() {
        document.getElementById('main-content').innerHTML = `
            <h1 style="font-size: 2.5rem;">Yay! ❤️</h1>
            <p style="font-size: 1.2rem; color: #d63384;">Birds of a feather, we should stick together!</p>
            <div class="video-wrapper">
                <iframe src="https://www.youtube.com/embed/V9PVRfjEBTI?autoplay=1&start=75" frameborder="0" allow="autoplay"></iframe>
            </div>
        `;
    }
</script>
</body>
</html>
