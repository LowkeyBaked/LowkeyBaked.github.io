# LowkeyBaked.github.io
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <title>Auto-download text file</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>
    body { font-family: system-ui, sans-serif; margin: 2rem; }
    button { padding: 0.5rem 0.9rem; border-radius: 0.5rem; border: 1px solid #ccc; cursor: pointer; }
  </style>
</head>
<body>
  <h1>Your download should start automatically</h1>
  <p>If it doesn’t, click this button:</p>
  <button id="fallback">Download file</button>

  <!-- Hidden anchor used to trigger the download -->
  <a id="dl" download="example.txt" style="display:none"></a>

  <script>
    (function () {
      // === Customize these two lines ===
      const filename = "example.txt";
      const textContent = "Hello! This file was generated when you visited the page.\r\n";

      const anchor = document.getElementById("dl");
      const fallbackBtn = document.getElementById("fallback");

      function triggerDownload() {
        const blob = new Blob([textContent], { type: "text/plain;charset=utf-8" });
        const url = URL.createObjectURL(blob);

        anchor.href = url;
        anchor.download = filename;
        anchor.click();

        // Clean up the temporary object URL shortly after
        setTimeout(() => URL.revokeObjectURL(url), 1000);
      }

      // Try to start the download as soon as the page finishes loading
      window.addEventListener("load", triggerDownload);

      // Fallback (for browsers that block auto-downloads without a user gesture)
      fallbackBtn.addEventListener("click", triggerDownload);
    })();
  </script>
</body>
</html>
