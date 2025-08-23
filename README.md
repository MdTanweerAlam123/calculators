<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jharkhand Sand Conversion Calculator</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #8B4513;
            --secondary: #2E8B57;
            --accent: #CD853F;
            --light: #FFF8DC;
            --dark: #654321;
            --success: #228B22;
            --warning: #FF8C00;
            --info: #20B2AA;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #FFF8DC 0%, #F5DEB3 100%);
            color: #654321;
            line-height: 1.6;
            padding: 20px;
            min-height: 100vh;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(139, 69, 19, 0.2);
            overflow: hidden;
            position: relative;
        }
        
        .expiration-notice {
            position: absolute;
            top: 10px;
            right: 10px;
            background: var(--accent);
            color: white;
            padding: 5px 10px;
            border-radius: 5px;
            font-size: 0.8rem;
            z-index: 100;
        }
        
        header {
            background: linear-gradient(135deg, var(--primary) 0%, #A0522D 100%);
            color: white;
            padding: 25px;
            text-align: center;
            position: relative;
        }
        
        h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
        }
        
        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
        }
        
        .main-content {
            display: flex;
            flex-wrap: wrap;
            padding: 20px;
        }
        
        .calculator-section {
            flex: 1;
            min-width: 300px;
            padding: 20px;
        }
        
        .library-section {
            flex: 1;
            min-width: 300px;
            padding: 20px;
            background: var(--light);
            border-radius: 10px;
            max-height: 80vh;
            overflow: hidden;
            display: flex;
            flex-direction: column;
        }
        
        .section-title {
            font-size: 1.5rem;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid var(--secondary);
            color: var(--primary);
        }
        
        .input-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
        }
        
        input, select {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 16px;
            transition: all 0.3s;
        }
        
        input:focus, select:focus {
            border-color: var(--secondary);
            outline: none;
            box-shadow: 0 0 0 3px rgba(46, 139, 87, 0.2);
        }
        
        .btn-group {
            display: flex;
            gap: 15px;
            margin: 25px 0;
        }
        
        .btn {
            flex: 1;
            padding: 14px 20px;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            text-align: center;
            background: linear-gradient(135deg, var(--secondary) 0%, #3CB371 100%);
            color: white;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 7px 15px rgba(46, 139, 87, 0.4);
            background: linear-gradient(135deg, #3CB371 0%, var(--secondary) 100%);
        }
        
        .btn-secondary {
            background: linear-gradient(135deg, var(--accent) 0%, #DEB887 100%);
        }
        
        .btn-secondary:hover {
            background: linear-gradient(135deg, #DEB887 0%, var(--accent) 100%);
            box-shadow: 0 7px 15px rgba(205, 133, 63, 0.4);
        }
        
        .result-box {
            background: var(--light);
            padding: 20px;
            border-radius: 10px;
            margin-top: 20px;
            border-left: 5px solid var(--secondary);
        }
        
        .result-title {
            font-weight: 600;
            margin-bottom: 10px;
            color: var(--primary);
        }
        
        .result-value {
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--secondary);
        }
        
        .calculation-steps {
            margin-top: 30px;
            padding: 20px;
            background: #f8f9fa;
            border-radius: 10px;
            border-left: 5px solid var(--info);
        }
        
        .steps-title {
            font-weight: 600;
            margin-bottom: 15px;
            color: var(--primary);
        }
        
        .step {
            margin-bottom: 10px;
            padding: 10px;
            background: white;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
        }
        
        .library-list {
            flex: 1;
            overflow-y: auto;
            margin-top: 20px;
            padding-right: 5px;
        }
        
        .library-item {
            padding: 15px;
            margin-bottom: 10px;
            background: white;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
            cursor: pointer;
            transition: all 0.3s;
            border-left: 4px solid transparent;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .library-item:hover {
            transform: translateX(5px);
            box-shadow: 0 5px 15px rgba(139, 69, 19, 0.1);
        }
        
        .library-item-content {
            flex: 1;
        }
        
        .rock-name {
            font-weight: 600;
            color: var(--primary);
        }
        
        .rock-density {
            opacity: 0.9;
            font-size: 0.9rem;
            margin-top: 5px;
        }
        
        .rock-description {
            margin-top: 8px;
            font-size: 0.9rem;
            opacity: 0.8;
        }
        
        .add-unit-btn {
            background: linear-gradient(135deg, var(--secondary) 0%, #3CB371 100%);
            color: white;
            border: none;
            border-radius: 5px;
            padding: 8px 12px;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .add-unit-btn:hover {
            background: linear-gradient(135deg, #3CB371 0%, var(--secondary) 100%);
            transform: scale(1.05);
        }
        
        .search-box {
            margin-bottom: 20px;
            position: relative;
        }
        
        .search-box i {
            position: absolute;
            left: 15px;
            top: 50%;
            transform: translateY(-50%);
            color: #888;
        }
        
        .search-box input {
            padding-left: 40px;
        }
        
        .category-filter {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-bottom: 15px;
        }
        
        .category-btn {
            padding: 8px 15px;
            border: none;
            border-radius: 20px;
            font-size: 0.9rem;
            cursor: pointer;
            transition: all 0.3s;
            background: #ddd;
        }
        
        .category-btn.active {
            background: linear-gradient(135deg, var(--secondary) 0%, #3CB371 100%);
            color: white;
        }
        
        footer {
            text-align: center;
            padding: 20px;
            background: linear-gradient(135deg, var(--primary) 0%, #A0522D 100%);
            color: white;
            margin-top: 30px;
        }
        
        .unit-display {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-top: 10px;
        }
        
        .unit-value {
            font-weight: 600;
            color: var(--secondary);
        }
        
        @media (max-width: 768px) {
            .main-content {
                flex-direction: column;
            }
            
            .calculator-section, .library-section {
                width: 100%;
            }
            
            .library-section {
                max-height: none;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="expiration-notice">Valid until: 31.12.2025</div>
        
        <header>
            <h2>Jharkhand Sand Conversion (CFT ↔ Tons) Calculator</h2>
            <p class="subtitle">Convert between Cubic Feet (CFT) and Tons for different types of sand in Jharkhand</p>
        </header>
        
        <div class="main-content">
            <div class="calculator-section">
                <h2 class="section-title">Conversion Calculator</h2>
                
                <div class="input-group">
                    <label for="material">Select Sand Type</label>
                    <select id="material">
                        <option value="custom">Custom (Enter density manually)</option>
                        <option value="river_sand_fine">River Sand (Fine)</option>
                        <option value="river_sand_medium">River Sand (Medium)</option>
                        <option value="river_sand_coarse">River Sand (Coarse)</option>
                        <option value="construction_sand">Construction Sand</option>
                        <option value="packaged_sand">Packaged River Sand</option>
                        <option value="wet_sand">Wet Sand</option>
                        <option value="dry_sand">Dry Sand</option>
                        <option value="balughat_sand">Balughat Sand (Estimated)</option>
                    </select>
                </div>
                
                <div class="input-group">
                    <label for="density">Bulk Density (kg/m³)</label>
                    <input type="number" id="density" placeholder="Enter bulk density" value="1600">
                </div>
                
                <div class="input-group">
                    <label for="cft">Volume (Cubic Feet - CFT)</label>
                    <input type="number" id="cft" placeholder="Enter CFT value">
                </div>
                
                <div class="input-group">
                    <label for="tons">Weight (Tons)</label>
                    <input type="number" id="tons" placeholder="Enter Tons value">
                </div>
                
                <div class="btn-group">
                    <button class="btn" id="convertCFTtoTon">Convert CFT to Ton</button>
                    <button class="btn btn-secondary" id="convertTonToCFT">Convert Ton to CFT</button>
                </div>
                
                <div class="result-box">
                    <div class="result-title">Conversion Result:</div>
                    <div class="result-value" id="result">-</div>
                </div>
                
                <div class="calculation-steps">
                    <div class="steps-title">Calculation Steps:</div>
                    <div id="steps">
                        <p>Select a sand type or enter density, then input a value to convert.</p>
                    </div>
                </div>
            </div>
            
            <div class="library-section">
                <h2 class="section-title">Jharkhand Sand Library</h2>
                
                <div class="search-box">
                    <i class="fas fa-search"></i>
                    <input type="text" id="search" placeholder="Search sand types...">
                </div>
                
                <div class="category-filter" id="categoryFilter">
                    <button class="category-btn active" data-category="all">All</button>
                    <button class="category-btn" data-category="river">River Sand</button>
                    <button class="category-btn" data-category="construction">Construction</button>
                    <button class="category-btn" data-category="special">Special Types</button>
                </div>
                
                <div class="library-list" id="mineralLibrary">
                    <!-- River Sands -->
                    <div class="library-item" data-density="1440" data-category="river">
                        <div class="library-item-content">
                            <div class="rock-name">River Sand (Fine)</div>
                            <div class="rock-density">Density: ~1,440 kg/m³</div>
                            <div class="rock-description">Fine-grained river sand with small particle size</div>
                            <div class="unit-display">1 CFT = <span class="unit-value">0.041</span> Tons</div>
                        </div>
                        <button class="add-unit-btn" data-density="1440">Add</button>
                    </div>
                    
                    <div class="library-item" data-density="1520" data-category="river">
                        <div class="library-item-content">
                            <div class="rock-name">River Sand (Medium)</div>
                            <div class="rock-density">Density: ~1,520 kg/m³</div>
                            <div class="rock-description">Medium-grained river sand, balanced particle size</div>
                            <div class="unit-display">1 CFT = <span class="unit-value">0.043</span> Tons</div>
                        </div>
                        <button class="add-unit-btn" data-density="1520">Add</button>
                    </div>
                    
                    <div class="library-item" data-density="1600" data-category="river">
                        <div class="library-item-content">
                            <div class="rock-name">River Sand (Coarse)</div>
                            <div class="rock-density">Density: ~1,600 kg/m³</div>
                            <div class="rock-description">Coarse-grained river sand with larger particles</div>
                            <div class="unit-display">1 CFT = <span class="unit-value">0.045</span> Tons</div>
                        </div>
                        <button class="add-unit-btn" data-density="1600">Add</button>
                    </div>
                    
                    <!-- Construction Sands -->
                    <div class="library-item" data-density="1600" data-category="construction">
                        <div class="library-item-content">
                            <div class="rock-name">Construction Sand (General)</div>
                            <div class="rock-density">Density: ~1,600 kg/m³</div>
                            <div class="rock-description">General construction sand for concrete applications</div>
                            <div class="unit-display">1 CFT = <span class="unit-value">0.045</span> Tons</div>
                        </div>
                        <button class="add-unit-btn" data-density="1600">Add</button>
                    </div>
                    
                    <div class="library-item" data-density="1680" data-category="construction">
                        <div class="library-item-content">
                            <div class="rock-name">Construction River Sand</div>
                            <div class="rock-density">Density: ~1,680 kg/m³</div>
                            <div class="rock-description">River sand specifically for construction purposes</div>
                            <div class="unit-display">1 CFT = <span class="unit-value">0.048</span> Tons</div>
                        </div>
                        <button class="add-unit-btn" data-density="1680">Add</button>
                    </div>
                    
                    <div class="library-item" data-density="1860" data-category="construction">
                        <div class="library-item-content">
                            <div class="rock-name">Packaged River Sand</div>
                            <div class="rock-density">Density: ~1,860 kg/m³</div>
                            <div class="rock-description">Processed and packaged sand from suppliers</div>
                            <div class="unit-display">1 CFT = <span class="unit-value">0.053</span> Tons</div>
                        </div>
                        <button class="add-unit-btn" data-density="1860">Add</button>
                    </div>
                    
                    <!-- Special Types -->
                    <div class="library-item" data-density="1570" data-category="special">
                        <div class="library-item-content">
                            <div class="rock-name">Dry Sand</div>
                            <div class="rock-density">Density: ~1,540–1,600 kg/m³</div>
                            <div class="rock-description">Dry sand with minimal moisture content</div>
                            <div class="unit-display">1 CFT = <span class="unit-value">0.044</span> Tons</div>
                        </div>
                        <button class="add-unit-btn" data-density="1570">Add</button>
                    </div>
                    
                    <div class="library-item" data-density="1880" data-category="special">
                        <div class="library-item-content">
                            <div class="rock-name">Wet Sand</div>
                            <div class="rock-density">Density: ~1,760–2,000 kg/m³</div>
                            <div class="rock-description">Moisture-laden sand with higher density</div>
                            <div class="unit-display">1 CFT = <span class="unit-value">0.053</span> Tons</div>
                        </div>
                        <button class="add-unit-btn" data-density="1880">Add</button>
                    </div>
                    
                    <div class="library-item" data-density="1650" data-category="special">
                        <div class="library-item-content">
                            <div class="rock-name">Balughat Sand (Estimated)</div>
                            <div class="rock-density">Density: ~1,500–1,800 kg/m³</div>
                            <div class="rock-description">Estimated values for Balughat region sand</div>
                            <div class="unit-display">1 CFT = <span class="unit-value">0.047</span> Tons</div>
                        </div>
                        <button class="add-unit-btn" data-density="1650">Add</button>
                    </div>
                </div>
            </div>
        </div>
        
        <footer>
            <p>Jharkhand Sand Calculator © 2023 | Valid until December 31, 2025 | Density values may vary based on source and moisture content</p>
        </footer>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Check expiration date
            const expirationDate = new Date('2025-12-31');
            const currentDate = new Date();
            
            if (currentDate > expirationDate) {
                alert('This application has expired. Please contact support for renewal.');
                document.querySelectorAll('input, select, button').forEach(element => {
                    element.disabled = true;
                });
            }
            
            // Constants
            const cftToM3 = 35.3147; // Conversion factor from cubic meters to cubic feet
            const kgToTon = 1000; // 1000 kg in a ton
            
            // DOM Elements
            const materialSelect = document.getElementById('material');
            const densityInput = document.getElementById('density');
            const cftInput = document.getElementById('cft');
            const tonsInput = document.getElementById('tons');
            const convertCFTtoTonBtn = document.getElementById('convertCFTtoTon');
            const convertTonToCFTBtn = document.getElementById('convertTonToCFT');
            const resultElement = document.getElementById('result');
            const stepsElement = document.getElementById('steps');
            const searchInput = document.getElementById('search');
            const mineralLibrary = document.getElementById('mineralLibrary');
            const libraryItems = mineralLibrary.getElementsByClassName('library-item');
            const categoryButtons = document.querySelectorAll('.category-btn');
            const addUnitButtons = document.querySelectorAll('.add-unit-btn');
            
            // Predefined sand types and their densities (kg/m³)
            const materials = {
                'custom': 1600,
                'river_sand_fine': 1440,
                'river_sand_medium': 1520,
                'river_sand_coarse': 1600,
                'construction_sand': 1600,
                'packaged_sand': 1860,
                'wet_sand': 1880,
                'dry_sand': 1570,
                'balughat_sand': 1650
            };
            
            // Calculate and update unit values for all sand types
            function updateUnitValues() {
                const items = document.querySelectorAll('.library-item');
                items.forEach(item => {
                    const density = parseFloat(item.getAttribute('data-density'));
                    const tonsPerCFT = (density / cftToM3) / kgToTon;
                    const unitValue = item.querySelector('.unit-value');
                    if (unitValue) {
                        unitValue.textContent = tonsPerCFT.toFixed(3);
                    }
                });
            }
            
            // Initialize unit values
            updateUnitValues();
            
            // Event Listeners
            materialSelect.addEventListener('change', function() {
                const selectedMaterial = this.value;
                densityInput.value = materials[selectedMaterial];
            });
            
            convertCFTtoTonBtn.addEventListener('click', convertCFTtoTon);
            convertTonToCFTBtn.addEventListener('click', convertTonToCFT);
            
            searchInput.addEventListener('input', function() {
                const searchTerm = this.value.toLowerCase();
                const activeCategory = document.querySelector('.category-btn.active').dataset.category;
                
                Array.from(libraryItems).forEach(item => {
                    const sandName = item.querySelector('.rock-name').textContent.toLowerCase();
                    const itemCategory = item.dataset.category;
                    
                    if (sandName.includes(searchTerm) && 
                        (activeCategory === 'all' || itemCategory === activeCategory)) {
                        item.style.display = 'flex';
                    } else {
                        item.style.display = 'none';
                    }
                });
            });
            
            // Category filter buttons
            categoryButtons.forEach(button => {
                button.addEventListener('click', function() {
                    // Set active button
                    categoryButtons.forEach(btn => btn.classList.remove('active'));
                    this.classList.add('active');
                    
                    const category = this.dataset.category;
                    const searchTerm = searchInput.value.toLowerCase();
                    
                    // Filter items
                    Array.from(libraryItems).forEach(item => {
                        const sandName = item.querySelector('.rock-name').textContent.toLowerCase();
                        const itemCategory = item.dataset.category;
                        
                        if ((category === 'all' || itemCategory === category) && 
                            sandName.includes(searchTerm)) {
                            item.style.display = 'flex';
                        } else {
                            item.style.display = 'none';
                        }
                    });
                });
            });
            
            // Add click event to library items
            Array.from(libraryItems).forEach(item => {
                item.addEventListener('click', function(e) {
                    if (!e.target.classList.contains('add-unit-btn')) {
                        const density = this.getAttribute('data-density');
                        densityInput.value = density;
                        
                        // Find and select the custom option
                        materialSelect.value = 'custom';
                        
                        // Highlight the selected item
                        Array.from(libraryItems).forEach(i => {
                            i.style.borderLeft = '4px solid transparent';
                        });
                        this.style.borderLeft = '4px solid var(--secondary)';
                    }
                });
            });
            
            // Add unit buttons
            addUnitButtons.forEach(button => {
                button.addEventListener('click', function(e) {
                    e.stopPropagation();
                    const density = this.getAttribute('data-density');
                    densityInput.value = density;
                    materialSelect.value = 'custom';
                    
                    // Show confirmation
                    const sandName = this.closest('.library-item').querySelector('.rock-name').textContent;
                    showResult(`Added ${sandName} density: ${density} kg/m³`);
                    
                    // Show calculation for 1 unit
                    const tonsPerCFT = (density / cftToM3) / kgToTon;
                    const cftPerTon = (kgToTon / density) * cftToM3;
                    
                    stepsElement.innerHTML = `
                        <div class="step">
                            <strong>Conversion for ${sandName}:</strong>
                        </div>
                        <div class="step">
                            1 CFT = ${tonsPerCFT.toFixed(4)} Tons<br>
                            1 Ton = ${cftPerTon.toFixed(4)} CFT
                        </div>
                        <div class="step">
                            <strong>Formula:</strong> Tons = (Density / ${cftToM3}) / ${kgToTon}<br>
                            <strong>Calculation:</strong> (${density} / ${cftToM3}) / ${kgToTon} = ${tonsPerCFT.toFixed(4)} Tons
                        </div>
                    `;
                });
            });
            
            // Conversion Functions
            function convertCFTtoTon() {
                const density = parseFloat(densityInput.value);
                const cft = parseFloat(cftInput.value);
                
                if (isNaN(density) || isNaN(cft) || density <= 0 || cft <= 0) {
                    showError('Please enter valid density and CFT values.');
                    return;
                }
                
                // Convert CFT to m³
                const cubicMeters = cft / cftToM3;
                
                // Calculate mass in kg
                const massKg = cubicMeters * density;
                
                // Convert kg to tons
                const tons = massKg / kgToTon;
                
                // Display result
                showResult(`${cft} CFT = ${tons.toFixed(3)} Tons`);
                
                // Show calculation steps
                showStepsCFTtoTon(cft, density, cubicMeters, massKg, tons);
            }
            
            function convertTonToCFT() {
                const density = parseFloat(densityInput.value);
                const tons = parseFloat(tonsInput.value);
                
                if (isNaN(density) || isNaN(tons) || density <= 0 || tons <= 0) {
                    showError('Please enter valid density and Tons values.');
                    return;
                }
                
                // Convert tons to kg
                const massKg = tons * kgToTon;
                
                // Calculate volume in m³
                const cubicMeters = massKg / density;
                
                // Convert m³ to CFT
                const cft = cubicMeters * cftToM3;
                
                // Display result
                showResult(`${tons} Tons = ${cft.toFixed(3)} CFT`);
                
                // Show calculation steps
                showStepsTonToCFT(tons, density, massKg, cubicMeters, cft);
            }
            
            // Steps Functions
            function showStepsCFTtoTon(cft, density, cubicMeters, massKg, tons) {
                stepsElement.innerHTML = `
                    <div class="step">
                        <strong>Step 1:</strong> Convert CFT to cubic meters<br>
                        Formula: Cubic Meters = CFT / ${cftToM3}<br>
                        Calculation: ${cft} / ${cftToM3} = ${cubicMeters.toFixed(4)} m³
                    </div>
                    <div class="step">
                        <strong>Step 2:</strong> Calculate mass in kilograms<br>
                        Formula: Mass (kg) = Volume (m³) × Density (kg/m³)<br>
                        Calculation: ${cubicMeters.toFixed(4)} × ${density} = ${massKg.toFixed(2)} kg
                    </div>
                    <div class="step">
                        <strong>Step 3:</strong> Convert kilograms to tons<br>
                        Formula: Tons = kg / ${kgToTon}<br>
                        Calculation: ${massKg.toFixed(2)} / ${kgToTon} = ${tons.toFixed(3)} tons
                    </div>
                    <div class="step">
                        <strong>Final Result:</strong> ${cft} CFT = ${tons.toFixed(3)} Tons
                    </div>
                `;
            }
            
            function showStepsTonToCFT(tons, density, massKg, cubicMeters, cft) {
                stepsElement.innerHTML = `
                    <div class="step">
                        <strong>Step 1:</strong> Convert tons to kilograms<br>
                        Formula: kg = Tons × ${kgToTon}<br>
                        Calculation: ${tons} × ${kgToTon} = ${massKg.toFixed(2)} kg
                    </div>
                    <div class="step">
                        <strong>Step 2:</strong> Calculate volume in cubic meters<br>
                        Formula: Volume (m³) = Mass (kg) / Density (kg/m³)<br>
                        Calculation: ${massKg.toFixed(2)} / ${density} = ${cubicMeters.toFixed(4)} m³
                    </div>
                    <div class="step">
                        <strong>Step 3:</strong> Convert cubic meters to CFT<br>
                        Formula: CFT = m³ × ${cftToM3}<br>
                        Calculation: ${cubicMeters.toFixed(4)} × ${cftToM3} = ${cft.toFixed(3)} CFT
                    </div>
                    <div class="step">
                        <strong>Final Result:</strong> ${tons} Tons = ${cft.toFixed(3)} CFT
                    </div>
                `;
            }
            
            function showResult(message) {
                resultElement.textContent = message;
            }
            
            function showError(message) {
                resultElement.textContent = 'Error: ' + message;
                stepsElement.innerHTML = `<div class="step" style="color: var(--accent);">${message}</div>`;
            }
        });
    </script>
</body>
</html>
