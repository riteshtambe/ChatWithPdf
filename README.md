# ChatWithPdf
### Project Overview: Interactive PDF Document Analysis and Question Answering System
# My PDF Document

You can view or download the PDF document by clicking the link below:

[View PDF](https://github.com/riteshtambe/ChatWithPdf/raw/main/ChatWithPdf_report.pdf)

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>PDF Viewer</title>
    <style>
        body {
            margin: 0;
            padding: 0;
        }
        #viewer {
            width: 100%;
            height: 500px; /* Adjust the height as needed */
        }
    </style>
</head>
<body>
    <div id="viewer"></div>
    <script src=""></script>
    <script>
        const pdfjsLib = window['pdfjs-dist/build/pdf'];

        // Set the URL of your PDF file here
        const pdfUrl = 'URL_TO_YOUR_PDF';

        pdfjsLib.getDocument(pdfUrl).promise.then(function(pdfDoc) {
            const pdfViewer = document.getElementById('viewer');
            for (let pageNum = 1; pageNum <= pdfDoc.numPages; pageNum++) {
                pdfDoc.getPage(pageNum).then(function(page) {
                    const canvas = document.createElement('canvas');
                    const context = canvas.getContext('2d');
                    canvas.style.display = 'block';
                    pdfViewer.appendChild(canvas);
                    const viewport = page.getViewport({ scale: 1.5 });
                    canvas.height = viewport.height;
                    canvas.width = viewport.width;
                    page.render({ canvasContext: context, viewport: viewport });
                });
            }
        });
    </script>
</body>
</html>
