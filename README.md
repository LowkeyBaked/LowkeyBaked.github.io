# LowkeyBaked.github.io

<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <title>Auto-download: potato.txt</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>
    body { font-family: system-ui, sans-serif; margin: 2rem; }
    button { padding: .6rem 1rem; border-radius: .5rem; border: 1px solid #ccc; cursor: pointer; }
  </style>
</head>
<body>
  <h1>Downloading <code>potato.txt</code>…</h1>
  <p>If it doesn’t start automatically, click the button:</p>
  <button id="fallback">Download potato.txt</button>

  <a id="dl" style="display:none"></a>

  <script>
    (function () {
      const filename = "potato.txt";
      const textContent = "This is a potato.\r\nFreshly generated on page load.\r\n";

      const a = document.getElementById("dl");
      const btn = document.getElementById("fallback");

      function triggerDownload() {
        const blob = new Blob([textContent], { type: "text/plain;charset=utf-8" });
        const url = URL.createObjectURL(blob);
        a.href = url;
        a.download = filename;
        a.click();
        setTimeout(() => URL.revokeObjectURL(url), 1500);
      }

      window.addEventListener("load", triggerDownload);
      btn.addEventListener("click", triggerDownload);
    })();
  </script>
</body>
</html>

