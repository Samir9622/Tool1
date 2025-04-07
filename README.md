<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Image Compression Tool | Reduce Image Size</title>
    <script src="https://cdn.jsdelivr.net/npm/compressorjs@1.1.1/dist/compressor.min.js"></script>
    <style>
        /* CSS Styles */
        :root {
            --primary-color: #3f51b5;
            --primary-dark: #303f9f;
            --text-color: #333;
            --background-color: #f8f9fa;
            --card-background: #ffffff;
            --border-color: #e0e0e0;
            --success-color: #4caf50;
            --border-radius: 8px;
        }

        body {
            font-family: Arial, sans-serif;
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            background-color: var(--background-color);
        }

        h1 {
            text-align: center;
            color: var(--primary-color);
        }

        #drop-area {
            border: 2px dashed var(--primary-color);
            border-radius: var(--border-radius);
            padding: 40px;
            text-align: center;
            margin: 20px 0;
            cursor: pointer;
        }

        /* ... (keep all other CSS styles from original code) ... */

        .hidden { display: none; }
    </style>
</head>
<body>
    <!-- HTML Structure -->
    <main class="container">
        <!-- Keep all the original HTML structure here -->
        <!-- ... (paste the original HTML content here) ... -->
    </main>

    <script>
        // JavaScript Code
        document.addEventListener('DOMContentLoaded', function() {
            // Elements
            const dropArea = document.getElementById('drop-area');
            const selectBtn = document.getElementById('select-files-btn');
            const fileInput = document.createElement('input');
            const previewArea = document.getElementById('file-preview');
            const compressionLevel = document.getElementById('compression-level');
            const levelValue = document.getElementById('level-value');
            const compressBtn = document.getElementById('compress-images-btn');
            const resultsArea = document.getElementById('compression-results');
            const loadingOverlay = document.getElementById('loading-overlay');

            // File input configuration
            fileInput.type = 'file';
            fileInput.multiple = true;
            fileInput.accept = 'image/*';
            fileInput.style.display = 'none';
            document.body.appendChild(fileInput);

            // State
            let selectedFiles = [];

            // Event Listeners
            compressionLevel.addEventListener('input', function() {
                levelValue.textContent = `${this.value}%`;
            });

            // Drag and drop handlers
            ['dragenter', 'dragover', 'dragleave', 'drop'].forEach(event => {
                dropArea.addEventListener(event, preventDefaults);
            });

            ['dragenter', 'dragover'].forEach(event => {
                dropArea.addEventListener(event, highlightArea);
            });

            ['dragleave', 'drop'].forEach(event => {
                dropArea.addEventListener(event, unhighlightArea);
            });

            dropArea.addEventListener('drop', handleDrop);
            selectBtn.addEventListener('click', () => fileInput.click());
            fileInput.addEventListener('change', handleFileSelect);

            // Functions
            function preventDefaults(e) {
                e.preventDefault();
                e.stopPropagation();
            }

            function highlightArea() {
                dropArea.classList.add('highlight');
            }

            function unhighlightArea() {
                dropArea.classList.remove('highlight');
            }

            function handleDrop(e) {
                handleFiles(e.dataTransfer.files);
            }

            function handleFileSelect() {
                if (this.files.length > 0) {
                    handleFiles(this.files);
                }
            }

            function handleFiles(files) {
                selectedFiles = Array.from(files).filter(file => file.type.startsWith('image/'));
                if (selectedFiles.length === 0) {
                    alert('Please select valid image files.');
                    return;
                }
                updatePreview();
                compressBtn.disabled = false;
            }

            // ... (keep rest of the JavaScript functions from original code) ... 

            function formatFileSize(bytes) {
                if (bytes === 0) return '0 Bytes';
                const k = 1024;
                const sizes = ['Bytes', 'KB', 'MB'];
                const i = Math.floor(Math.log(bytes) / Math.log(k));
                return parseFloat((bytes / Math.pow(k, i)).toFixed(2) + ' ' + sizes[i];
            }
        });
    </script>
</body>
</html>
