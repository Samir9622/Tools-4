<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>ImageCompressorPro</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <div class="nav-container">
      <div class="logo">ImageCompressorPro</div>
      <nav>
        <ul class="nav-links">
          <li><a href="#">Home</a></li>
          <li><a href="#">How It Works</a></li>
          <li><a href="#">Blog</a></li>
          <li><a href="#">Contact</a></li>
        </ul>
      </nav>
    </div>
  </header>

  <section class="hero">
    <h1>Free Online Image Compression Tool</h1>
    <p>Reduce your image file size without losing quality. Supports JPG, PNG, and WebP formats. Fast, secure, and completely free!</p>
  </section>

  <!-- Ad Placeholder -->
  <div class="ad">
    <!-- Google Adsense code can be added here -->
  </div>

  <section class="compressor">
    <h2>Compress Your Images</h2>
    <div id="drop-area">
      <input type="file" id="fileElem" accept="image/*" multiple hidden />
      <label for="fileElem">
        <div class="upload-box">
          <img src="https://cdn-icons-png.flaticon.com/512/833/833524.png" alt="Upload Icon" width="50"/>
          <p>Drag & Drop Your Images Here<br>or click to select files</p>
        </div>
      </label>
    </div>

    <label for="quality">Compression Level</label>
    <input type="range" id="quality" min="10" max="90" value="70">

    <label for="format">Output Format</label>
    <select id="format">
      <option value="original">Keep Original</option>
      <option value="jpeg">Convert to JPEG</option>
      <option value="webp">Convert to WebP</option>
    </select>

    <button id="compressBtn">Compress Images</button>

    <div id="result"></div>
  </section>

  <!-- Another Ad Placeholder -->
  <div class="ad"></div>

  <footer>
    <div class="footer-section">
      <div>
        <span>⚡</span>
        <h3>Fast Processing</h3>
        <p>Our tool compresses your images in seconds using smart compression algorithms.</p>
      </div>
      <div>
        <span>🔒</span>
        <h3>Secure & Private</h3>
        <p>All processing happens in your browser. Your files never leave your device.</p>
      </div>
    </div>
    <p class="footer-note">© 2025 ImageCompressorPro</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>
body {
  font-family: 'Segoe UI', sans-serif;
  margin: 0;
  padding: 0;
  background: #f8f9fa;
  color: #333;
}

header {
  background: #0a58ca;
  color: white;
  padding: 15px 20px;
}

.nav-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  font-size: 1.5em;
  font-weight: bold;
}

.nav-links {
  list-style: none;
  display: flex;
  gap: 20px;
}

.nav-links li a {
  color: white;
  text-decoration: none;
  font-weight: 500;
}

.hero {
  text-align: center;
  padding: 40px 20px;
  background: linear-gradient(to right, #e3f2fd, #f1f8ff);
}

.ad {
  text-align: center;
  padding: 20px;
}

.compressor {
  max-width: 600px;
  margin: 0 auto;
  padding: 30px 20px;
  background: white;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.05);
}

.upload-box {
  text-align: center;
  border: 2px dashed #ccc;
  padding: 30px;
  background-color: #fafafa;
  border-radius: 6px;
  cursor: pointer;
}

input[type="range"],
select {
  width: 100%;
  margin: 10px 0 20px;
  padding: 5px;
}

button {
  width: 100%;
  padding: 10px;
  background-color: #0a58ca;
  color: white;
  font-size: 16px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #0948a5;
}

#result {
  margin-top: 20px;
}

footer {
  background: #e9ecef;
  padding: 30px 20px;
  margin-top: 50px;
  text-align: center;
}

.footer-section {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}

.footer-section div {
  max-width: 250px;
}

.footer-note {
  margin-top: 20px;
  color: #777;
}
document.getElementById('compressBtn').addEventListener('click', () => {
  const input = document.getElementById('fileElem');
  const quality = document.getElementById('quality').value;
  const format = document.getElementById('format').value;
  const result = document.getElementById('result');

  if (!input.files.length) {
    alert('Please select an image!');
    return;
  }

  result.innerHTML = '';

  [...input.files].forEach(file => {
    const reader = new FileReader();
    reader.onload = function(e) {
      const img = new Image();
      img.onload = function() {
        const canvas = document.createElement('canvas');
        const ctx = canvas.getContext('2d');

        canvas.width = img.width;
        canvas.height = img.height;
        ctx.drawImage(img, 0, 0);

        let mimeType = file.type;
        if (format === 'jpeg') mimeType = 'image/jpeg';
        else if (format === 'webp') mimeType = 'image/webp';

        canvas.toBlob(blob => {
          const url = URL.createObjectURL(blob);
          const link = document.createElement('a');
          link.href = url;
          link.download = `compressed_${file.name}`;
          link.innerText = `Download ${file.name}`;
          link.style.display = 'block';
          result.appendChild(link);
        }, mimeType, quality / 100);
      };
      img.src = e.target.result;
    };
    reader.readAsDataURL(file);
  });
});
