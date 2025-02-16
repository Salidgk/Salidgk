<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI YouTube Thumbnail Generator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
            background-color: #f4f4f4;
        }
        input {
            width: 80%;
            padding: 10px;
            margin: 10px 0;
        }
        button {
            padding: 10px 20px;
            background-color: #ff0000;
            color: white;
            border: none;
            cursor: pointer;
        }
        .thumbnail-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 10px;
            margin-top: 20px;
        }
        .thumbnail {
            width: 300px;
            height: 170px;
            object-fit: cover;
            border-radius: 10px;
            transition: 0.3s;
        }
        .thumbnail:hover {
            transform: scale(1.1);
        }
    </style>
</head>
<body>
    <h2>AI YouTube Thumbnail Generator</h2>
    <input type="text" id="videoUrl" placeholder="Paste YouTube Video URL here...">
    <button onclick="generateThumbnails()">Generate Thumbnails</button>
    
    <div class="thumbnail-container" id="thumbnails"></div>

    <script>
        function generateThumbnails() {
            let url = document.getElementById("videoUrl").value;
            let videoId = url.split("v=")[1]?.split("&")[0];
            if (!videoId) {
                alert("Invalid YouTube URL! Please enter a valid URL.");
                return;
            }
            
            let baseThumbnail = `https://img.youtube.com/vi/${videoId}/maxresdefault.jpg`;
            let variations = [
                `https://img.youtube.com/vi/${videoId}/hqdefault.jpg`,
                `https://img.youtube.com/vi/${videoId}/mqdefault.jpg`,
                `https://img.youtube.com/vi/${videoId}/sddefault.jpg`
            ];
            
            let thumbnailsDiv = document.getElementById("thumbnails");
            thumbnailsDiv.innerHTML = "";
            
            [baseThumbnail, ...variations].forEach((src, index) => {
                let img = document.createElement("img");
                img.src = src;
                img.className = "thumbnail";
                img.onclick = () => window.open(src, "_blank");
                thumbnailsDiv.appendChild(img);
            });
        }
    </script>
</body>
</html>
