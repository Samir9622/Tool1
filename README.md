<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Free Online Image Compression Tool | Reduce Image Size</title>
    <meta name="description" content="Reduce your image file size without losing quality. Supports JPG, PNG, and WebP formats. Fast, secure, and completely free!">
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@6.4.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/browser-image-compression@2.0.0/dist/browser-image-compression.js"></script>
    <style>
        .drop-area {
            border: 2px dashed #cbd5e0;
            transition: all 0.3s ease;
        }
        .drop-area.highlight {
            border-color: #4a90e2;
            background-color: rgba(74, 144, 226, 0.1);
        }
        .slider {
            -webkit-appearance: none;
            height: 8px;
            border-radius: 4px;
            background: #e2e8f0;
            outline: none;
        }
        .slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            appearance: none;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background: #4a90e2;
            cursor: pointer;
        }
        .slider::-moz-range-thumb {
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background: #4a90e2;
            cursor: pointer;
        }
    </style>
</head>
<body class="bg-gray-50 font-sans text-gray-800">
    <header class="bg-gradient-to-r from-blue-500 to-teal-400 text-white py-6 shadow-md">
        <div class="container mx-auto px-4">
            <h1 class="text-3xl font-bold text-center">Image Compression Tool</h1>
            <p class="text-center mt-2">Reduce image size without losing quality</p>
        </div>
    </header>

    <main class="container mx-auto px-4 py-8 max-w-4xl">
        <!-- AdSense Ad -->
        <div class="mb-8">
            <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
            <ins class="adsbygoogle"
                 style="display:block"
                 data-ad-client="ca-pub-8773480799818158"
                 data-ad-slot="9354903383"
                 data-ad-format="auto"
                 data-full-width-responsive="true"></ins>
            <script>
                 (adsbygoogle = window.adsbygoogle || []).push({});
            </script>
        </div>

        <section class="mb-10 bg-white rounded-lg shadow-md p-6">
            <h2 class="text-2xl font-semibold mb-6">Compress Your Images</h2>
            
            <!-- Drag & Drop Area -->
            <div id="drop-area" class="drop-area rounded-lg p-10 text-center cursor-pointer mb-6">
                <div class="flex flex-col items-center">
                    <i class="fas fa-cloud-upload-alt text-5xl text-blue-500 mb-4"></i>
                    <p class="text-lg mb-2">Drag & Drop Your Images Here</p>
                    <p class="text-sm text-gray-500 mb-4">Or</p>
                    <input type="file" id="file-input" multiple accept="image/*" class="hidden">
                    <button id="select-file-btn" class="bg-blue-500 hover:bg-blue-600 text-white px-6 py-2 rounded-full transition duration-300 font-medium">
                        Select Files
                    </button>
                </div>
            </div>

            <!-- Compression Settings -->
            <div class="mb-6">
                <h3 class="text-lg font-semibold mb-4">Compression Settings</h3>
                
                <div class="mb-4">
                    <label for="compression-level" class="block text-sm font-medium text-gray-700 mb-1">Compression Level: <span id="compression-value">80%</span></label>
                    <input type="range" id="compression-level" class="slider w-full" min="0" max="100" value="80">
                    <div class="flex justify-between text-xs text-gray-500 mt-1">
                        <span>Higher Quality</span>
                        <span>Smaller Size</span>
                    </div>
                </div>

                <div class="mb-4">
                    <label for="output-format" class="block text-sm font-medium text-gray-700 mb-1">Output Format</label>
                    <select id="output-format" class="w-full p-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
                        <option value="jpeg">JPEG</option>
                        <option value="png">PNG</option>
                        <option value="webp">WebP</option>
                    </select>
                </div>

                <div class="mb-4">
                    <label class="flex items-center">
                        <input type="checkbox" id="maintain-dimensions" class="mr-2" checked>
                        <span class="text-sm">Maintain original dimensions</span>
                    </label>
                </div>
            </div>

            <!-- Files List -->
            <div id="files-container" class="mb-6">
                <!-- Files will be added here dynamically -->
            </div>

            <!-- Compress Button -->
            <button id="compress-button" class="w-full bg-blue-500 hover:bg-blue-600 text-white py-3 px-4 rounded-md transition duration-300 font-medium text-lg disabled:opacity-50 disabled:cursor-not-allowed" disabled>
                Compress Images
            </button>
        </section>

        <!-- Compression Results -->
        <section id="results-section" class="mb-10 bg-white rounded-lg shadow-md p-6 hidden">
            <h2 class="text-2xl font-semibold mb-6">Compression Results</h2>
            <div id="compression-results" class="space-y-4">
                <!-- Results will be added here dynamically -->
            </div>
            <div class="mt-6">
                <button id="download-all-btn" class="bg-green-600 hover:bg-green-700 text-white py-2 px-4 rounded-md transition duration-300 font-medium">
                    <i class="fas fa-download mr-2"></i>Download All
                </button>
                <button id="compress-more-btn" class="bg-blue-500 hover:bg-blue-600 text-white py-2 px-4 rounded-md transition duration-300 font-medium ml-4">
                    <i class="fas fa-plus mr-2"></i>Compress More Images
                </button>
            </div>
        </section>

        <!-- Second AdSense Ad -->
        <div class="mb-8">
            <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
            <ins class="adsbygoogle"
                 style="display:block"
                 data-ad-client="ca-pub-8773480799818158"
                 data-ad-slot="9055111364"
                 data-ad-format="auto"
                 data-full-width-responsive="true"></ins>
            <script>
                 (adsbygoogle = window.adsbygoogle || []).push({});
            </script>
        </div>

        <!-- Features Section -->
        <section class="grid md:grid-cols-3 gap-6 mb-10">
            <div class="bg-white rounded-lg shadow-md p-6 text-center">
                <i class="fas fa-bolt text-4xl text-blue-500 mb-4"></i>
                <h3 class="text-xl font-semibold mb-2">Fast Processing</h3>
                <p class="text-gray-600">Our tool compresses your images in seconds using advanced algorithms to reduce file size without noticeable quality loss.</p>
            </div>
            <div class="bg-white rounded-lg shadow-md p-6 text-center">
                <i class="fas fa-lock text-4xl text-blue-500 mb-4"></i>
                <h3 class="text-xl font-semibold mb-2">Secure & Private</h3>
                <p class="text-gray-600">All image processing happens in your browser. Your files never leave your device, ensuring complete privacy.</p>
            </div>
            <div class="bg-white rounded-lg shadow-md p-6 text-center">
                <i class="fas fa-gift text-4xl text-blue-500 mb-4"></i>
                <h3 class="text-xl font-semibold mb-2">100% Free</h3>
                <p class="text-gray-600">No watermarks, no registration, no hidden fees. Compress as many images as you want, completely free.</p>
            </div>
        </section>
    </main>

    <footer class="bg-gray-800 text-white py-8">
        <div class="container mx-auto px-4 text-center">
            <p>© 2023 Image Compression Tool. All rights reserved.</p>
        </div>
    </footer>

    <script>
        // DOM Elements
        const dropArea = document.getElementById('drop-area');
        const fileInput = document.getElementById('file-input');
        const selectFileBtn = document.getElementById('select-file-btn');
        const filesContainer = document.getElementById('files-container');
        const compressButton = document.getElementById('compress-button');
        const compressionLevel = document.getElementById('compression-level');
        const compressionValue = document.getElementById('compression-value');
        const outputFormat = document.getElementById('output-format');
        const maintainDimensions = document.getElementById('maintain-dimensions');
        const resultsSection = document.getElementById('results-section');
        const compressionResults = document.getElementById('compression-results');
        const downloadAllBtn = document.getElementById('download-all-btn');
        const compressMoreBtn = document.getElementById('compress-more-btn');

        // Variables to store files
        let imagesToCompress = [];
        let compressedImages = [];

        // Prevent default drag behaviors
        ['dragenter', 'dragover', 'dragleave', 'drop'].forEach(eventName => {
            dropArea.addEventListener(eventName, preventDefaults, false);
        });

        function preventDefaults(e) {
            e.preventDefault();
            e.stopPropagation();
        }

        // Highlight drop area when item is dragged over
        ['dragenter', 'dragover'].forEach(eventName => {
            dropArea.addEventListener(eventName, highlight, false);
        });

        ['dragleave', 'drop'].forEach(eventName => {
            dropArea.addEventListener(eventName, unhighlight, false);
        });

        function highlight() {
            dropArea.classList.add('highlight');
        }

        function unhighlight() {
            dropArea.classList.remove('highlight');
        }

        // Handle dropped files
        dropArea.addEventListener('drop', handleDrop, false);

        function handleDrop(e) {
            const dt = e.dataTransfer;
            const files = dt.files;
            handleFiles(files);
        }

        // Handle files from file input
        fileInput.addEventListener('change', function() {
            handleFiles(this.files);
        });

        // Connect select file button to file input
        selectFileBtn.addEventListener('click', function() {
            fileInput.click();
        });

        // Click on drop area to select files
        dropArea.addEventListener('click', function() {
            fileInput.click();
        });

        // Update compression value display
        compressionLevel.addEventListener('input', function() {
            compressionValue.textContent = this.value + '%';
        });

        // Handle the files that were selected or dropped
        function handleFiles(files) {
            if (!files.length) return;
            
            // Filter only image files
            const imageFiles = Array.from(files).filter(file => file.type.match('image.*'));
            
            if (imageFiles.length === 0) {
                alert('Please select image files only.');
                return;
            }

            // Add files to our array
            imageFiles.forEach(file => {
                // Check if file is already in the list (by name)
                if (!imagesToCompress.some(img => img.name === file.name)) {
                    imagesToCompress.push(file);
                    displayFileInfo(file);
                }
            });

            // Enable compress button if we have files
            compressButton.disabled = imagesToCompress.length === 0;
        }

        // Display file information
        function displayFileInfo(file) {
            const fileId = `file-${Date.now()}-${Math.random().toString(36).substr(2, 9)}`;
            
            const fileInfo = document.createElement('div');
            fileInfo.id = fileId;
            fileInfo.className = 'file-info flex items-center justify-between bg-gray-50 p-3 rounded-md mb-3';
            
            // Create thumbnail
            const reader = new FileReader();
            reader.onload = function(e) {
                document.getElementById(`${fileId}-thumbnail`).src = e.target.result;
            };
            reader.readAsDataURL(file);
            
            fileInfo.innerHTML = `
                <div class="flex items-center">
                    <img id="${fileId}-thumbnail" class="w-12 h-12 object-cover rounded mr-3" alt="Thumbnail">
                    <div>
                        <p class="font-medium truncate max-w-xs">${file.name}</p>
                        <p class="text-sm text-gray-500">${formatFileSize(file.size)}</p>
                    </div>
                </div>
                <button class="remove-file text-red-500 hover:text-red-700 transition duration-300" data-file-id="${fileId}">
                    <i class="fas fa-times"></i>
                </button>
            `;
            
            filesContainer.appendChild(fileInfo);
            
            // Add event listener to remove button
            fileInfo.querySelector('.remove-file').addEventListener('click', function() {
                const fileId = this.getAttribute('data-file-id');
                const fileElement = document.getElementById(fileId);
                
                // Find index of file in array
                const fileName = fileElement.querySelector('p').textContent;
                const fileIndex = imagesToCompress.findIndex(file => file.name === fileName);
                
                // Remove file from array
                if (fileIndex !== -1) {
                    imagesToCompress.splice(fileIndex, 1);
                }
                
                // Remove element from DOM
                fileElement.remove();
                
                // Disable compress button if no files
                compressButton.disabled = imagesToCompress.length === 0;
            });
        }

        // Format file size
        function formatFileSize(bytes) {
            if (bytes < 1024) return bytes + ' bytes';
            else if (bytes < 1048576) return (bytes / 1024).toFixed(1) + ' KB';
            else return (bytes / 1048576).toFixed(1) + ' MB';
        }

        // Compress button event
        compressButton.addEventListener('click', async function() {
            if (imagesToCompress.length === 0) {
                alert('Please select at least one image to compress');
                return;
            }
            
            // Clear previous results
            compressionResults.innerHTML = '';
            resultsSection.classList.remove('hidden');
            compressedImages = [];
            
            // Show loading
            compressionResults.innerHTML = `
                <div class="text-center py-8">
                    <i class="fas fa-spinner fa-spin text-4xl text-blue-500 mb-4"></i>
                    <p>Compressing your images...</p>
                </div>
            `;
            
            // Scroll to results
            resultsSection.scrollIntoView({ behavior: 'smooth' });
            
            try {
                // Get compression settings
                const quality = parseInt(compressionLevel.value) / 100;
                const format = outputFormat.value;
                const keepDimensions = maintainDimensions.checked;
                
                // Process each image
                const compressionPromises = imagesToCompress.map(file => compressImage(file, quality, format, keepDimensions));
                const results = await Promise.all(compressionPromises);
                
                // Store compressed images
                compressedImages = results;
                
                // Clear loading indicator
                compressionResults.innerHTML = '';
                
                // Display results
                let totalOriginalSize = 0;
                let totalCompressedSize = 0;
                
                results.forEach((result, index) => {
                    totalOriginalSize += result.originalSize;
                    totalCompressedSize += result.compressedSize;
                    
                    displayCompressionResult(result, index);
                });
                
                // Display summary
                const savingsPercentage = ((totalOriginalSize - totalCompressedSize) / totalOriginalSize * 100).toFixed(1);
                
                // Add summary at the top
                const summaryElement = document.createElement('div');
                summaryElement.className = 'bg-green-50 border border-green-200 rounded-md p-4 mb-6';
                summaryElement.innerHTML = `
                    <div class="flex items-center justify-between">
                        <div>
                            <h3 class="font-semibold text-green-800">Compression Complete!</h3>
                            <p class="text-green-700">Reduced from ${formatFileSize(totalOriginalSize)} to ${formatFileSize(totalCompressedSize)} (saved ${savingsPercentage}%)</p>
                        </div>
                        <div class="text-4xl text-green-500">
                            <i class="fas fa-check-circle"></i>
                        </div>
                    </div>
                `;
                compressionResults.insertBefore(summaryElement, compressionResults.firstChild);
                
            } catch (error) {
                compressionResults.innerHTML = `
                    <div class="bg-red-50 border border-red-200 rounded-md p-4">
                        <div class="flex items-center">
                            <div class="text-3xl text-red-500 mr-4">
                                <i class="fas fa-exclamation-circle"></i>
                            </div>
                            <div>
                                <h3 class="font-semibold text-red-800">Error During Compression</h3>
                                <p class="text-red-700">${error.message || 'An unexpected error occurred.'}</p>
                            </div>
                        </div>
                    </div>
                `;
            }
        });

        // Compress an image
        async function compressImage(file, quality, format, keepDimensions) {
            // Read the image
            const originalImageUrl = await readFileAsDataURL(file);
            const originalSize = file.size;
            
            // Compression options
            const options = {
                maxSizeMB: 10,
                maxWidthOrHeight: keepDimensions ? Infinity : 1920,
                useWebWorker: true,
                fileType: `image/${format}`,
                quality: quality
            };
            
            // Compress the image
            const compressedFile = await imageCompression(file, options);
            const compressedSize = compressedFile.size;
            const compressedUrl = await readFileAsDataURL(compressedFile);
            
            // Create a meaningful filename
            let fileName = file.name;
          
