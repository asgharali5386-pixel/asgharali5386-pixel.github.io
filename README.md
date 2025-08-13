<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>JPG to PDF Converter - Free Online Tool</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 20px;
            background-color: #f5f5f5;
        }
        h1 {
            color: #333;
        }
        input {
            margin: 20px 0;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            background: #28a745;
            border: none;
            color: white;
            cursor: pointer;
        }
        button:hover {
            background: #218838;
        }
    </style>
</head>
<body>
    <h1>JPG to PDF Converter</h1>
    <p>Select a JPG image and convert it to PDF instantly.</p>
    
    <input type="file" id="imageFile" accept="image/jpeg">
    <br>
    <button onclick="convertToPDF()">Convert to PDF</button>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <script>
        async function convertToPDF() {
            const fileInput = document.getElementById('imageFile');
            if (!fileInput.files.length) {
                alert("Please select a JPG image first!");
                return;
            }
            const file = fileInput.files[0];
            const reader = new FileReader();
            
            reader.onload = function(e) {
                const { jsPDF } = window.jspdf;
                const pdf = new jsPDF();
                const imgData = e.target.result;
