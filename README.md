<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Free JPG to PDF Converter</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background: #f4f4f4;
            padding: 30px;
        }
        h1 {
            color: #333;
        }
        input[type="file"] {
            margin: 20px 0;
        }
        button {
            padding: 10px 20px;
            background: #28a745;
            color: white;
            border: none;
            cursor: pointer;
            border-radius: 5px;
        }
        button:hover {
            background: #218838;
        }
    </style>
</head>
<body>
    <h1>Free JPG to PDF Converter</h1>
    <p>Select one or more JPG images to convert into a single PDF.</p>
    
    <input type="file" id="fileInput" accept="image/jpeg" multiple>
    <br>
    <button onclick="convertToPDF()">Convert to PDF</button>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <script>
        async function convertToPDF() {
            const { jsPDF } = window.jspdf;
            const pdf = new jsPDF();
            const files = document.getElementById('fileInput').files;

            if (files.length === 0) {
                alert("Please select at least one JPG image.");
                return;
            }

            for (let i = 0; i < files.length; i++) {
                const imgData = await readFileAsDataURL(files[i]);
                if (i > 0) pdf.addPage();
                pdf.addImage(imgData, 'JPEG', 10, 10, 190, 277);
            }

            pdf.save("converted.pdf");
        }

        function readFileAsDataURL(file) {
            return new Promise((resolve, reject) => {
                const reader = new FileReader();
                reader.onload = () => resolve(reader.result);
                reader.onerror = error => reject(error);
                reader.readAsDataURL(file);
            });
        }
    </script>
</body>
</html># asgharali5386-pixel.github.io
