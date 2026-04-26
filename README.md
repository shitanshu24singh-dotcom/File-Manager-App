<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>File Manager App</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f4f9;
      margin: 0;
      padding: 20px;
      display: flex;
      justify-content: center;
      align-items: flex-start;
    }
    .container {
      background: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      width: 400px;
    }
    h2 {
      text-align: center;
      margin-bottom: 20px;
    }
    input[type="file"] {
      margin-bottom: 15px;
    }
    ul {
      list-style: none;
      padding: 0;
    }
    li {
      background: #f9f9f9;
      padding: 10px;
      margin-bottom: 10px;
      border-radius: 5px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    .delete-btn {
      background: #f44336;
      color: white;
      border: none;
      padding: 5px 10px;
      border-radius: 5px;
      cursor: pointer;
    }
    .delete-btn:hover {
      background: #d32f2f;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>File Manager</h2>
    <input type="file" id="fileInput" multiple>
    <ul id="fileList"></ul>
  </div>

  <script>
    const fileInput = document.getElementById("fileInput");
    const fileList = document.getElementById("fileList");

    fileInput.addEventListener("change", () => {
      const files = Array.from(fileInput.files);
      files.forEach(file => {
        const li = document.createElement("li");
        li.textContent = file.name;

        const deleteBtn = document.createElement("button");
        deleteBtn.textContent = "Delete";
        deleteBtn.className = "delete-btn";
        deleteBtn.onclick = () => li.remove();

        li.appendChild(deleteBtn);
        fileList.appendChild(li);
      });
      fileInput.value = ""; // reset input
    });
  </script>
</body>
</html>
