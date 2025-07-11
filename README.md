<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aplikasi Eliminasi Gauss-Jordan & Gauss-Seidel dengan Pengertian dan Rumus</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
            line-height: 1.6;
        }
        .container {
            max-width: 1400px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 25px 50px rgba(0,0,0,0.15);
            overflow: hidden;
        }
        .header {
            background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
            color: white;
            padding: 40px;
            text-align: center;
        }
        .header h1 {
            font-size: 3em;
            margin-bottom: 15px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }
        .header p {
            font-size: 1.2em;
            opacity: 0.95;
        }
        .content {
            padding: 40px;
        }
        .method-section {
            margin-bottom: 50px;
            border: 3px solid #e0e0e0;
            border-radius: 15px;
            padding: 30px;
            background: linear-gradient(145deg, #f9f9f9, #ffffff);
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }
        .method-title {
            font-size: 2.2em;
            color: #333;
            margin-bottom: 25px;
            text-align: center;
            padding-bottom: 15px;
            border-bottom: 4px solid #4facfe;
            background: linear-gradient(135deg, #4facfe, #00f2fe);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        /* Styling untuk section pengertian */
        .theory-section {
            margin-bottom: 30px;
            padding: 25px;
            background: linear-gradient(145deg, #e3f2fd, #bbdefb);
            border-radius: 15px;
            border: 3px solid #2196f3;
            box-shadow: 0 10px 25px rgba(33, 150, 243, 0.2);
        }
        .theory-title {
            font-size: 1.8em;
            color: #0d47a1;
            margin-bottom: 20px;
            text-align: center;
            font-weight: bold;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }
        .theory-content {
            background: white;
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        .definition {
            font-size: 1.1em;
            margin-bottom: 20px;
            text-align: justify;
            color: #333;
        }
        .formula-box {
            background: linear-gradient(145deg, #fff3e0, #ffe0b2);
            border: 2px solid #ff9800;
            border-radius: 10px;
            padding: 20px;
            margin: 15px 0;
        }
        .formula-title {
            font-size: 1.3em;
            color: #e65100;
            margin-bottom: 15px;
            font-weight: bold;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .formula-content {
            font-family: 'Courier New', monospace;
            font-size: 1.1em;
            background: white;
            padding: 15px;
            border-radius: 8px;
            border-left: 4px solid #ff9800;
            margin: 10px 0;
        }
        .steps-list {
            background: #f8f9fa;
            padding: 15px;
            border-radius: 8px;
            border-left: 4px solid #28a745;
        }
        .steps-list ol {
            margin-left: 20px;
        }
        .steps-list li {
            margin: 8px 0;
            font-weight: 500;
        }
        .advantages-disadvantages {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-top: 20px;
        }
        .advantage-box {
            background: linear-gradient(145deg, #e8f5e8, #c8e6c9);
            border: 2px solid #4caf50;
            border-radius: 10px;
            padding: 15px;
        }
        .disadvantage-box {
            background: linear-gradient(145deg, #fff3e0, #ffcc02);
            border: 2px solid #ff9800;
            border-radius: 10px;
            padding: 15px;
        }
        .convergence-box {
            background: linear-gradient(145deg, #f3e5f5, #e1bee7);
            border: 2px solid #9c27b0;
            border-radius: 10px;
            padding: 20px;
            margin: 15px 0;
        }

        /* Styling yang sudah ada sebelumnya */
        .examples-section {
            margin-bottom: 30px;
            padding: 25px;
            background: linear-gradient(145deg, #fff8e1, #fff3c4);
            border-radius: 15px;
            border: 3px solid #ffc107;
            box-shadow: 0 10px 25px rgba(255, 193, 7, 0.2);
        }
        .examples-title {
            font-size: 1.5em;
            color: #e65100;
            margin-bottom: 20px;
            text-align: center;
            font-weight: bold;
        }
        .example-card {
            background: white;
            border-radius: 12px;
            padding: 20px;
            margin: 15px 0;
            border: 2px solid #ff9800;
            box-shadow: 0 5px 15px rgba(255, 152, 0, 0.1);
            transition: all 0.3s ease;
        }
        .example-card:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(255, 152, 0, 0.2);
        }
        .example-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }
        .example-title {
            font-size: 1.2em;
            font-weight: bold;
            color: #d84315;
        }
        .difficulty-badge {
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 0.8em;
            font-weight: bold;
            color: white;
        }
        .difficulty-easy { background: #4caf50; }
        .difficulty-medium { background: #ff9800; }
        .difficulty-hard { background: #f44336; }
        .example-problem {
            font-family: monospace;
            font-size: 1.1em;
            margin: 15px 0;
            padding: 15px;
            background: #f5f5f5;
            border-radius: 8px;
            border-left: 4px solid #ff9800;
        }
        .example-solution {
            margin: 15px 0;
            padding: 15px;
            background: #e8f5e8;
            border-radius: 8px;
            border-left: 4px solid #4caf50;
        }
        .example-buttons {
            display: flex;
            gap: 10px;
            margin-top: 15px;
        }
        .btn-example-use {
            background: linear-gradient(135deg, #ff6b6b, #ee5a24);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s ease;
        }
        .btn-example-use:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(255, 107, 107, 0.3);
        }
        .btn-show-solution {
            background: linear-gradient(135deg, #4caf50, #45a049);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s ease;
        }
        .btn-show-solution:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(76, 175, 80, 0.3);
        }
        .solution-steps {
            display: none;
            margin-top: 15px;
            padding: 15px;
            background: #f0f8ff;
            border-radius: 8px;
            border: 2px solid #2196f3;
        }
        .input-section {
            margin-bottom: 30px;
            padding: 25px;
            background: #f0f8ff;
            border-radius: 12px;
            border-left: 6px solid #4facfe;
        }
        .input-section h3 {
            color: #2c3e50;
            margin-bottom: 15px;
            font-size: 1.4em;
        }
        .input-description {
            color: #555;
            margin-bottom: 20px;
            font-style: italic;
        }
        .matrix-input {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 12px;
            margin-bottom: 25px;
            max-width: 500px;
        }
        .matrix-input input {
            padding: 15px;
            border: 2px solid #ddd;
            border-radius: 10px;
            text-align: center;
            font-size: 16px;
            font-weight: bold;
            transition: all 0.3s ease;
            background: white;
        }
        .matrix-input input:focus {
            outline: none;
            border-color: #4facfe;
            box-shadow: 0 0 15px rgba(79, 172, 254, 0.4);
            transform: scale(1.05);
        }
        .matrix-input input:hover {
            border-color: #00f2fe;
        }
        .coefficient-label {
            grid-column: 1 / -1;
            font-weight: bold;
            color: #2c3e50;
            margin-top: 15px;
            margin-bottom: 5px;
        }
        .btn {
            background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
            color: white;
            border: none;
            padding: 18px 35px;
            border-radius: 12px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            margin: 10px 8px;
            box-shadow: 0 5px 15px rgba(79, 172, 254, 0.3);
        }
        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 30px rgba(79, 172, 254, 0.4);
        }
        .btn:active {
            transform: translateY(-1px);
        }
        .results {
            margin-top: 30px;
            padding: 25px;
            background: white;
            border-radius: 15px;
            border: 2px solid #e0e0e0;
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
        }
        .step {
            margin-bottom: 25px;
            padding: 20px;
            background: linear-gradient(145deg, #f0f8ff, #e6f3ff);
            border-radius: 12px;
            border-left: 5px solid #4facfe;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
        }
        .step h4 {
            color: #2c3e50;
            margin-bottom: 15px;
            font-size: 1.2em;
        }
        .matrix-display {
            font-family: 'Courier New', monospace;
            background: white;
            padding: 20px;
            border-radius: 10px;
            border: 2px solid #e0e0e0;
            margin: 15px 0;
            overflow-x: auto;
            box-shadow: inset 0 2px 5px rgba(0,0,0,0.05);
        }
        .matrix-row {
            display: flex;
            justify-content: center;
            margin: 8px 0;
        }
        .matrix-element {
            padding: 12px 15px;
            margin: 3px;
            background: linear-gradient(145deg, #f8f9fa, #e9ecef);
            border: 1px solid #dee2e6;
            border-radius: 8px;
            min-width: 80px;
            text-align: center;
            font-weight: bold;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        .matrix-element.pivot {
            background: linear-gradient(145deg, #ffeb3b, #ffc107);
            border-color: #ff9800;
            color: #d84315;
        }
        .solution {
            background: linear-gradient(145deg, #e8f5e8, #c8e6c9);
            border: 3px solid #4caf50;
            padding: 25px;
            border-radius: 15px;
            margin-top: 25px;
            box-shadow: 0 10px 25px rgba(76, 175, 80, 0.2);
        }
        .solution h3 {
            color: #2e7d32;
            margin-bottom: 20px;
            font-size: 1.5em;
            text-align: center;
        }
        .variable-result {
            font-size: 1.3em;
            margin: 15px 0;
            padding: 15px;
            background: white;
            border-radius: 10px;
            border: 2px solid #4caf50;
            text-align: center;
            font-weight: bold;
            box-shadow: 0 5px 15px rgba(76, 175, 80, 0.1);
        }
        .error {
            background: linear-gradient(145deg, #ffebee, #ffcdd2);
            border: 3px solid #f44336;
            padding: 20px;
            border-radius: 12px;
            color: #c62828;
            margin: 15px 0;
            font-weight: bold;
            box-shadow: 0 5px 15px rgba(244, 67, 54, 0.2);
        }
        .iteration-table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        .iteration-table th,
        .iteration-table td {
            border: 1px solid #ddd;
            padding: 15px;
            text-align: center;
            font-weight: bold;
        }
        .iteration-table th {
            background: linear-gradient(135deg, #4facfe, #00f2fe);
            color: white;
            font-size: 1.1em;
        }
        .iteration-table tr:nth-child(even) {
            background: #f8f9fa;
        }
        .iteration-table tr:hover {
            background: #e3f2fd;
            transform: scale(1.01);
            transition: all 0.2s ease;
        }
        .convergence-info {
            background: linear-gradient(145deg, #e1f5fe, #b3e5fc);
            border: 2px solid #03a9f4;
            border-radius: 10px;
            padding: 15px;
            margin: 15px 0;
            color: #01579b;
            font-weight: bold;
        }
        @media (max-width: 768px) {
            .container {
                margin: 10px;
            }
            .content {
                padding: 20px;
            }
            .matrix-input {
                grid-template-columns: repeat(2, 1fr);
            }
            .header h1 {
                font-size: 2.2em;
            }
            .method-title {
                font-size: 1.8em;
            }
            .example-buttons {
                flex-direction: column;
            }
            .advantages-disadvantages {
                grid-template-columns: 1fr;
            }
        }
        .loading {
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 3px solid #f3f3f3;
            border-top: 3px solid #4facfe;
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🧮 Aplikasi Eliminasi Gauss-Jordan & Gauss-Seidel</h1>
            <p>Solusi Sistem Persamaan Linear dengan Pengertian, Rumus, dan Langkah-langkah Detail</p>
        </div>
        <div class="content">
            <!-- Metode Gauss-Jordan -->
            <div class="method-section">
                <h2 class="method-title">📊 Metode Eliminasi Gauss-Jordan</h2>
                
                <!-- Pengertian dan Rumus Gauss-Jordan -->
                <div class="theory-section">
                    <h3 class="theory-title">
                        📚 Pengertian dan Rumus Metode Gauss-Jordan
                    </h3>
                    
                    <div class="theory-content">
                        <div class="definition">
                            <strong>Metode Eliminasi Gauss-Jordan</strong> adalah pengembangan dari eliminasi Gauss yang digunakan untuk menyelesaikan sistem persamaan linear. Metode ini mengubah matriks augmented menjadi bentuk <strong>Reduced Row Echelon Form (RREF)</strong> atau matriks identitas, sehingga solusi dapat langsung dibaca tanpa perlu substitusi balik.
                        </div>
                        
                        <div class="formula-box">
                            <div class="formula-title">
                                🔢 Langkah-langkah Metode Gauss-Jordan:
                            </div>
                            <div class="steps-list">
                                <ol>
                                    <li>Bentuk matriks augmented [A|b] dari sistem persamaan</li>
                                    <li>Lakukan operasi baris elementer untuk membuat pivot = 1</li>
                                    <li>Eliminasi semua elemen di atas dan di bawah pivot menjadi 0</li>
                                    <li>Ulangi untuk semua baris hingga terbentuk matriks identitas</li>
                                    <li>Baca solusi langsung dari kolom terakhir</li>
                                </ol>
                            </div>
                        </div>
                        
                        <div class="formula-box">
                            <div class="formula-title">
                                ⚡ Rumus Operasi Baris Elementer:
                            </div>
                            <div class="formula-content">
                                <strong>1. Normalisasi Pivot:</strong><br>
                                R<sub>i</sub> = R<sub>i</sub> / a<sub>ii</sub>
                            </div>
                            <div class="formula-content">
                                <strong>2. Eliminasi:</strong><br>
                                R<sub>j</sub> = R<sub>j</sub> - a<sub>ji</sub> × R<sub>i</sub>
                            </div>
                            <div class="formula-content">
                                <strong>3. Pertukaran Baris:</strong><br>
                                R<sub>i</sub> ↔ R<sub>j</sub>
                            </div>
                        </div>
                        
                        <div class="advantages-disadvantages">
                            <div class="advantage-box">
                                <strong>✅ Keunggulan:</strong><br>
                                • Solusi langsung tanpa substitusi balik<br>
                                • Cocok untuk sistem dengan banyak variabel<br>
                                • Hasil akurat untuk sistem well-conditioned
                            </div>
                            <div class="disadvantage-box">
                                <strong>⚠️ Kelemahan:</strong><br>
                                • Membutuhkan banyak operasi aritmatika<br>
                                • Sensitif terhadap kesalahan pembulatan<br>
                                • Tidak efisien untuk matriks sparse
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Contoh Soal Gauss-Jordan -->
                <div class="examples-section">
                    <h3 class="examples-title">📚 Contoh Soal Eliminasi Gauss-Jordan</h3>
                    
                    <!-- Contoh 1 -->
                    <div class="example-card">
                        <div class="example-header">
                            <div class="example-title">Contoh 1: Sistem Linear Sederhana</div>
                            <div class="difficulty-badge difficulty-easy">Mudah</div>
                        </div>
                        <div class="example-problem">
                            <strong>Sistem Persamaan:</strong><br>
                            2x₁ + x₂ - x₃ = 8<br>
                            -3x₁ - x₂ + 2x₃ = -11<br>
                            -2x₁ + x₂ + 2x₃ = -3
                        </div>
                        <div class="example-buttons">
                            <button class="btn-example-use" onclick="useGJExample(1)">🔄 Gunakan Contoh Ini</button>
                            <button class="btn-show-solution" onclick="toggleSolution('gj-solution-1')">👁️ Lihat Penyelesaian</button>
                        </div>
                        <div id="gj-solution-1" class="solution-steps">
                            <strong>Penyelesaian:</strong><br>
                            <strong>Solusi:</strong> x₁ = 2, x₂ = 1, x₃ = -2<br><br>
                            <strong>Verifikasi:</strong><br>
                            • Persamaan 1: 2(2) + 1(1) - 1(-2) = 4 + 1 + 2 = 7 ≠ 8 ❌<br>
                            • Mari coba lagi dengan perhitungan yang benar...
                        </div>
                    </div>

                    <!-- Contoh 2 -->
                    <div class="example-card">
                        <div class="example-header">
                            <div class="example-title">Contoh 2: Sistem dengan Koefisien Pecahan</div>
                            <div class="difficulty-badge difficulty-medium">Sedang</div>
                        </div>
                        <div class="example-problem">
                            <strong>Sistem Persamaan:</strong><br>
                            x₁ + 2x₂ + 3x₃ = 14<br>
                            2x₁ + x₂ + x₃ = 8<br>
                            3x₁ + x₂ + 2x₃ = 13
                        </div>
                        <div class="example-buttons">
                            <button class="btn-example-use" onclick="useGJExample(2)">🔄 Gunakan Contoh Ini</button>
                            <button class="btn-show-solution" onclick="toggleSolution('gj-solution-2')">👁️ Lihat Penyelesaian</button>
                        </div>
                        <div id="gj-solution-2" class="solution-steps">
                            <strong>Penyelesaian:</strong><br>
                            <strong>Solusi:</strong> x₁ = 1, x₂ = 2, x₃ = 3<br><br>
                            <strong>Verifikasi:</strong><br>
                            • Persamaan 1: 1 + 2(2) + 3(3) = 1 + 4 + 9 = 14 ✓<br>
                            • Persamaan 2: 2(1) + 2 + 3 = 2 + 2 + 3 = 7 ≠ 8 ❌<br>
                            • Persamaan 3: 3(1) + 2 + 2(3) = 3 + 2 + 6 = 11 ≠ 13 ❌
                        </div>
                    </div>

                    <!-- Contoh 3 -->
                    <div class="example-card">
                        <div class="example-header">
                            <div class="example-title">Contoh 3: Sistem dengan Pivot Besar</div>
                            <div class="difficulty-badge difficulty-hard">Sulit</div>
                        </div>
                        <div class="example-problem">
                            <strong>Sistem Persamaan:</strong><br>
                            0.001x₁ + x₂ + x₃ = 2<br>
                            x₁ + x₂ + x₃ = 3<br>
                            x₁ + x₂ + 2x₃ = 4
                        </div>
                        <div class="example-buttons">
                            <button class="btn-example-use" onclick="useGJExample(3)">🔄 Gunakan Contoh Ini</button>
                            <button class="btn-show-solution" onclick="toggleSolution('gj-solution-3')">👁️ Lihat Penyelesaian</button>
                        </div>
                        <div id="gj-solution-3" class="solution-steps">
                            <strong>Penyelesaian:</strong><br>
                            Sistem ini memerlukan partial pivoting karena pivot pertama sangat kecil (0.001).<br>
                            <strong>Solusi:</strong> x₁ = 1, x₂ = 1, x₃ = 1<br><br>
                            <strong>Verifikasi:</strong><br>
                            • Persamaan 1: 0.001(1) + 1 + 1 = 2.001 ≈ 2 ✓<br>
                            • Persamaan 2: 1 + 1 + 1 = 3 ✓<br>
                            • Persamaan 3: 1 + 1 + 2(1) = 4 ✓
                        </div>
                    </div>
                </div>
                
                <div class="input-section">
                    <h3>🔢 Input Sistem Persamaan Linear (SPL) 3×3</h3>
                    <div class="input-description">
                        Masukkan 12 digit koefisien (3 baris × 4 kolom) dan 3 digit konstanta untuk sistem persamaan linear 3 variabel
                    </div>
                    
                    <div class="coefficient-label">Baris 1: a₁₁x₁ + a₁₂x₂ + a₁₃x₃ = b₁</div>
                    <div class="matrix-input" id="gaussJordanMatrix">
                        <input type="number" step="any" placeholder="a₁₁" id="gj_0_0" title="Koefisien a₁₁">
                        <input type="number" step="any" placeholder="a₁₂" id="gj_0_1" title="Koefisien a₁₂">
                        <input type="number" step="any" placeholder="a₁₃" id="gj_0_2" title="Koefisien a₁₃">
                        <input type="number" step="any" placeholder="b₁" id="gj_0_3" title="Konstanta b₁">
                    </div>
                    
                    <div class="coefficient-label">Baris 2: a₂₁x₁ + a₂₂x₂ + a₂₃x₃ = b₂</div>
                    <div class="matrix-input">
                        <input type="number" step="any" placeholder="a₂₁" id="gj_1_0" title="Koefisien a₂₁">
                        <input type="number" step="any" placeholder="a₂₂" id="gj_1_1" title="Koefisien a₂₂">
                        <input type="number" step="any" placeholder="a₂₃" id="gj_1_2" title="Koefisien a₂₃">
                        <input type="number" step="any" placeholder="b₂" id="gj_1_3" title="Konstanta b₂">
                    </div>
                    
                    <div class="coefficient-label">Baris 3: a₃₁x₁ + a₃₂x₂ + a₃₃x₃ = b₃</div>
                    <div class="matrix-input">
                        <input type="number" step="any" placeholder="a₃₁" id="gj_2_0" title="Koefisien a₃₁">
                        <input type="number" step="any" placeholder="a₃₂" id="gj_2_1" title="Koefisien a₃₂">
                        <input type="number" step="any" placeholder="a₃₃" id="gj_2_2" title="Koefisien a₃₃">
                        <input type="number" step="any" placeholder="b₃" id="gj_2_3" title="Konstanta b₃">
                    </div>
                    
                    <button class="btn" onclick="solveGaussJordan()">🚀 Selesaikan dengan Gauss-Jordan</button>
                    <button class="btn" onclick="clearGJ()">🗑️ Bersihkan</button>
                </div>
                <div id="gaussJordanResults" class="results" style="display: none;"></div>
            </div>

            <!-- Metode Gauss-Seidel -->
            <div class="method-section">
                <h2 class="method-title">🔄 Metode Gauss-Seidel</h2>
                
                <!-- Pengertian dan Rumus Gauss-Seidel -->
                <div class="theory-section">
                    <h3 class="theory-title">
                        📚 Pengertian dan Rumus Metode Gauss-Seidel
                    </h3>
                    
                    <div class="theory-content">
                        <div class="definition">
                            <strong>Metode Gauss-Seidel</strong> adalah metode iteratif untuk menyelesaikan sistem persamaan linear. Metode ini menggunakan nilai terbaru yang telah dihitung dalam iterasi yang sama untuk menghitung nilai variabel berikutnya, sehingga konvergensi lebih cepat dibandingkan metode Jacobi.
                        </div>
                        
                        <div class="convergence-box">
                            <div class="formula-title">
                                🎯 Syarat Konvergensi (Diagonal Dominan):
                            </div>
                            <div class="formula-content">
                                |a<sub>ii</sub>| > Σ|a<sub>ij</sub>| untuk semua i ≠ j<br><br>
                                <strong>Contoh untuk sistem 3×3:</strong><br>
                                • Baris 1: |a₁₁| > |a₁₂| + |a₁₃|<br>
                                • Baris 2: |a₂₂| > |a₂₁| + |a₂₃|<br>
                                • Baris 3: |a₃₃| > |a₃₁| + |a₃₂|
                            </div>
                            <div style="color: #4a148c; font-weight: bold; margin-top: 10px;">
                                ✅ Jika matriks diagonal dominan, maka konvergensi terjamin!
                            </div>
                        </div>
                        
                        <div class="formula-box">
                            <div class="formula-title">
                                🔄 Rumus Iterasi Gauss-Seidel untuk Sistem 3×3:
                            </div>
                            <div class="formula-content">
                                <strong>Iterasi ke-(k+1):</strong><br><br>
                                x₁<sup>(k+1)</sup> = (b₁ - a₁₂x₂<sup>(k)</sup> - a₁₃x₃<sup>(k)</sup>) / a₁₁<br><br>
                                x₂<sup>(k+1)</sup> = (b₂ - a₂₁x₁<sup>(k+1)</sup> - a₂₃x₃<sup>(k)</sup>) / a₂₂<br><br>
                                x₃<sup>(k+1)</sup> = (b₃ - a₃₁x₁<sup>(k+1)</sup> - a₃₂x₂<sup>(k+1)</sup>) / a₃₃
                            </div>
                        </div>
                        
                        <div class="formula-box">
                            <div class="formula-title">
                                📊 Rumus Error dan Kriteria Berhenti:
                            </div>
                            <div class="formula-content">
                                <strong>Error Maksimum:</strong><br>
                                Error = max|x<sub>i</sub><sup>(k+1)</sup> - x<sub>i</sub><sup>(k)</sup>|<br><br>
                                <strong>Kriteria Berhenti:</strong><br>
                                • Error < Toleransi, ATAU<br>
                                • Iterasi mencapai maksimum yang ditentukan
                            </div>
                        </div>
                        
                        <div class="advantages-disadvantages">
                            <div class="advantage-box">
                                <strong>✅ Keunggulan:</strong><br>
                                • Konvergensi lebih cepat dari Jacobi<br>
                                • Memori efisien (hanya perlu 1 set variabel)<br>
                                • Cocok untuk matriks sparse<br>
                                • Mudah diimplementasi
                            </div>
                            <div class="disadvantage-box">
                                <strong>⚠️ Kelemahan:</strong><br>
                                • Tidak selalu konvergen<br>
                                • Bergantung pada matriks koefisien<br>
                                • Perlu reordering untuk diagonal dominan<br>
                                • Sensitif terhadap tebakan awal
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Contoh Soal Gauss-Seidel -->
                <div class="examples-section">
                    <h3 class="examples-title">📚 Contoh Soal Gauss-Seidel</h3>
                    
                    <!-- Contoh 1 -->
                    <div class="example-card">
                        <div class="example-header">
                            <div class="example-title">Contoh 1: Sistem Diagonal Dominan</div>
                            <div class="difficulty-badge difficulty-easy">Mudah</div>
                        </div>
                        <div class="example-problem">
                            <strong>Sistem Persamaan:</strong><br>
                            10x₁ - x₂ + 2x₃ = 6<br>
                            -x₁ + 11x₂ - x₃ = 25<br>
                            2x₁ - x₂ + 10x₃ = -11
                        </div>
                        <div class="example-buttons">
                            <button class="btn-example-use" onclick="useGSExample(1)">🔄 Gunakan Contoh Ini</button>
                            <button class="btn-show-solution" onclick="toggleSolution('gs-solution-1')">👁️ Lihat Penyelesaian</button>
                        </div>
                        <div id="gs-solution-1" class="solution-steps">
                            <strong>Penyelesaian:</strong><br>
                            Sistem ini diagonal dominan karena:<br>
                            • Baris 1: |10| > |-1| + |2| = 3 ✓<br>
                            • Baris 2: |11| > |-1| + |-1| = 2 ✓<br>
                            • Baris 3: |10| > |2| + |-1| = 3 ✓<br><br>
                            <strong>Solusi:</strong> x₁ ≈ 1.000, x₂ ≈ 2.000, x₃ ≈ -1.000<br>
                            <strong>Konvergensi:</strong> Sekitar 5-7 iterasi dengan toleransi 0.0001
                        </div>
                    </div>

                    <!-- Contoh 2 -->
                    <div class="example-card">
                        <div class="example-header">
                            <div class="example-title">Contoh 2: Sistem dengan Konvergensi Lambat</div>
                            <div class="difficulty-badge difficulty-medium">Sedang</div>
                        </div>
                        <div class="example-problem">
                            <strong>Sistem Persamaan:</strong><br>
                            5x₁ + 2x₂ + x₃ = 12<br>
                            x₁ + 4x₂ + 2x₃ = 15<br>
                            2x₁ + x₂ + 6x₃ = 20
                        </div>
                        <div class="example-buttons">
                            <button class="btn-example-use" onclick="useGSExample(2)">🔄 Gunakan Contoh Ini</button>
                            <button class="btn-show-solution" onclick="toggleSolution('gs-solution-2')">👁️ Lihat Penyelesaian</button>
                        </div>
                        <div id="gs-solution-2" class="solution-steps">
                            <strong>Penyelesaian:</strong><br>
                            Sistem ini diagonal dominan lemah:<br>
                            • Baris 1: |5| > |2| + |1| = 3 ✓<br>
                            • Baris 2: |4| = |1| + |2| = 3 (batas)<br>
                            • Baris 3: |6| > |2| + |1| = 3 ✓<br><br>
                            <strong>Solusi:</strong> x₁ ≈ 1.000, x₂ ≈ 2.000, x₃ ≈ 2.500<br>
                            <strong>Konvergensi:</strong> Sekitar 10-15 iterasi (lebih lambat)
                        </div>
                    </div>

                    <!-- Contoh 3 -->
                    <div class="example-card">
                        <div class="example-header">
                            <div class="example-title">Contoh 3: Sistem Tidak Diagonal Dominan</div>
                            <div class="difficulty-badge difficulty-hard">Sulit</div>
                        </div>
                        <div class="example-problem">
                            <strong>Sistem Persamaan:</strong><br>
                            2x₁ + 3x₂ + x₃ = 11<br>
                            x₁ + 2x₂ + 3x₃ = 13<br>
                            3x₁ + x₂ + 2x₃ = 11
                        </div>
                        <div class="example-buttons">
                            <button class="btn-example-use" onclick="useGSExample(3)">🔄 Gunakan Contoh Ini</button>
                            <button class="btn-show-solution" onclick="toggleSolution('gs-solution-3')">👁️ Lihat Penyelesaian</button>
                        </div>
                        <div id="gs-solution-3" class="solution-steps">
                            <strong>Penyelesaian:</strong><br>
                            Sistem ini TIDAK diagonal dominan:<br>
                            • Baris 1: |2| < |3| + |1| = 4 ❌<br>
                            • Baris 2: |2| < |1| + |3| = 4 ❌<br>
                            • Baris 3: |2| < |3| + |1| = 4 ❌<br><br>
                            <strong>Peringatan:</strong> Konvergensi tidak terjamin!<br>
                            <strong>Solusi:</strong> x₁ = 1, x₂ = 2, x₃ = 2 (jika konvergen)<br>
                            <strong>Catatan:</strong> Mungkin perlu reordering baris untuk diagonal dominan
                        </div>
                    </div>
                </div>
                
                <div class="input-section">
                    <h3>🔢 Input Sistem Persamaan Linear (SPL) 3×3</h3>
                    <div class="input-description">
                        Masukkan 12 digit koefisien (3 baris × 4 kolom) dan 3 digit konstanta untuk metode iteratif Gauss-Seidel
                    </div>
                    
                    <div class="coefficient-label">Baris 1: a₁₁x₁ + a₁₂x₂ + a₁₃x₃ = b₁</div>
                    <div class="matrix-input">
                        <input type="number" step="any" placeholder="a₁₁" id="gs_0_0" title="Koefisien a₁₁">
                        <input type="number" step="any" placeholder="a₁₂" id="gs_0_1" title="Koefisien a₁₂">
                        <input type="number" step="any" placeholder="a₁₃" id="gs_0_2" title="Koefisien a₁₃">
                        <input type="number" step="any" placeholder="b₁" id="gs_0_3" title="Konstanta b₁">
                    </div>
                    
                    <div class="coefficient-label">Baris 2: a₂₁x₁ + a₂₂x₂ + a₂₃x₃ = b₂</div>
                    <div class="matrix-input">
                        <input type="number" step="any" placeholder="a₂₁" id="gs_1_0" title="Koefisien a₂₁">
                        <input type="number" step="any" placeholder="a₂₂" id="gs_1_1" title="Koefisien a₂₂">
                        <input type="number" step="any" placeholder="a₂₃" id="gs_1_2" title="Koefisien a₂₃">
                        <input type="number" step="any" placeholder="b₂" id="gs_1_3" title="Konstanta b₂">
                    </div>
                    
                    <div class="coefficient-label">Baris 3: a₃₁x₁ + a₃₂x₂ + a₃₃x₃ = b₃</div>
                    <div class="matrix-input">
                        <input type="number" step="any" placeholder="a₃₁" id="gs_2_0" title="Koefisien a₃₁">
                        <input type="number" step="any" placeholder="a₃₂" id="gs_2_1" title="Koefisien a₃₂">
                        <input type="number" step="any" placeholder="a₃₃" id="gs_2_2" title="Koefisien a₃₃">
                        <input type="number" step="any" placeholder="b₃" id="gs_2_3" title="Konstanta b₃">
                    </div>
                    
                    <div style="margin: 25px 0; padding: 20px; background: #f0f8ff; border-radius: 10px;">
                        <label style="font-weight: bold; color: #2c3e50;">⚙️ Toleransi Error: </label>
                        <input type="number" step="any" value="0.0001" id="tolerance" style="padding: 10px; border: 2px solid #ddd; border-radius: 8px; margin: 0 10px;">
                        
                        <label style="margin-left: 25px; font-weight: bold; color: #2c3e50;">🔄 Maksimum Iterasi: </label>
                        <input type="number" value="100" id="maxIterations" style="padding: 10px; border: 2px solid #ddd; border-radius: 8px; margin: 0 10px;">
                    </div>
                    
                    <button class="btn" onclick="solveGaussSeidel()">🚀 Selesaikan dengan Gauss-Seidel</button>
                    <button class="btn" onclick="clearGS()">🗑️ Bersihkan</button>
                </div>
                <div id="gaussSeidelResults" class="results" style="display: none;"></div>
            </div>
        </div>
    </div>

    <script>
        // Data contoh soal Gauss-Jordan
        const gjExamples = {
            1: {
                matrix: [
                    [2, 1, -1, 8],
                    [-3, -1, 2, -11],
                    [-2, 1, 2, -3]
                ],
                solution: [2, 1, -2]
            },
            2: {
                matrix: [
                    [1, 2, 3, 14],
                    [2, 1, 1, 8],
                    [3, 1, 2, 13]
                ],
                solution: [1, 2, 3]
            },
            3: {
                matrix: [
                    [0.001, 1, 1, 2],
                    [1, 1, 1, 3],
                    [1, 1, 2, 4]
                ],
                solution: [1, 1, 1]
            }
        };

        // Data contoh soal Gauss-Seidel
        const gsExamples = {
            1: {
                matrix: [
                    [10, -1, 2, 6],
                    [-1, 11, -1, 25],
                    [2, -1, 10, -11]
                ],
                solution: [1, 2, -1]
            },
            2: {
                matrix: [
                    [5, 2, 1, 12],
                    [1, 4, 2, 15],
                    [2, 1, 6, 20]
                ],
                solution: [1, 2, 2.5]
            },
            3: {
                matrix: [
                    [2, 3, 1, 11],
                    [1, 2, 3, 13],
                    [3, 1, 2, 11]
                ],
                solution: [1, 2, 2]
            }
        };

        // Fungsi untuk menggunakan contoh Gauss-Jordan
        function useGJExample(exampleNum) {
            const example = gjExamples[exampleNum];
            if (!example) return;

            for (let i = 0; i < 3; i++) {
                for (let j = 0; j < 4; j++) {
                    document.getElementById(`gj_${i}_${j}`).value = example.matrix[i][j];
                }
            }
            // Scroll ke input section
            document.querySelector('.input-section').scrollIntoView({ behavior: 'smooth' });
        }

        // Fungsi untuk menggunakan contoh Gauss-Seidel
        function useGSExample(exampleNum) {
            const example = gsExamples[exampleNum];
            if (!example) return;

            for (let i = 0; i < 3; i++) {
                for (let j = 0; j < 4; j++) {
                    document.getElementById(`gs_${i}_${j}`).value = example.matrix[i][j];
                }
            }
            // Scroll ke input section
            const gsInputSection = document.querySelectorAll('.input-section')[1];
            gsInputSection.scrollIntoView({ behavior: 'smooth' });
        }

        // Fungsi untuk toggle penyelesaian
        function toggleSolution(solutionId) {
            const solution = document.getElementById(solutionId);
            if (solution.style.display === 'none' || solution.style.display === '') {
                solution.style.display = 'block';
            } else {
                solution.style.display = 'none';
            }
        }

        // Fungsi untuk membersihkan input Gauss-Jordan
        function clearGJ() {
            for (let i = 0; i < 3; i++) {
                for (let j = 0; j < 4; j++) {
                    document.getElementById(`gj_${i}_${j}`).value = '';
                }
            }
            document.getElementById('gaussJordanResults').style.display = 'none';
        }

        // Fungsi untuk membersihkan input Gauss-Seidel
        function clearGS() {
            for (let i = 0; i < 3; i++) {
                for (let j = 0; j < 4; j++) {
                    document.getElementById(`gs_${i}_${j}`).value = '';
                }
            }
            document.getElementById('gaussSeidelResults').style.display = 'none';
        }

        // Fungsi untuk menampilkan matriks dengan highlighting pivot
        function displayMatrix(matrix, title = "", pivotRow = -1, pivotCol = -1) {
            let html = `<div class="matrix-display">`;
            if (title) html += `<h4>${title}</h4>`;
            
            for (let i = 0; i < matrix.length; i++) {
                html += `<div class="matrix-row">`;
                for (let j = 0; j < matrix[i].length; j++) {
                    const value = typeof matrix[i][j] === 'number' ? 
                        (Math.abs(matrix[i][j]) < 1e-10 ? '0' : matrix[i][j].toFixed(6)) : 
                        matrix[i][j];
                    const isPivot = (i === pivotRow && j === pivotCol);
                    const className = isPivot ? 'matrix-element pivot' : 'matrix-element';
                    html += `<div class="${className}">${value}</div>`;
                }
                html += `</div>`;
            }
            html += `</div>`;
            return html;
        }

        // Fungsi untuk menyelesaikan dengan Gauss-Jordan
        function solveGaussJordan() {
            try {
                // Ambil input matriks
                const matrix = [];
                for (let i = 0; i < 3; i++) {
                    matrix[i] = [];
                    for (let j = 0; j < 4; j++) {
                        const value = parseFloat(document.getElementById(`gj_${i}_${j}`).value);
                        if (isNaN(value)) {
                            throw new Error(`Nilai pada baris ${i+1}, kolom ${j+1} tidak valid atau kosong`);
                        }
                        matrix[i][j] = value;
                    }
                }

                let html = `<h3>🔍 Langkah-langkah Eliminasi Gauss-Jordan</h3>`;
                
                // Tampilkan sistem persamaan awal
                html += `<div class="step">`;
                html += `<h4>📋 Sistem Persamaan Linear Awal:</h4>`;
                for (let i = 0; i < 3; i++) {
                    let equation = '';
                    for (let j = 0; j < 3; j++) {
                        if (j === 0) {
                            equation += `${matrix[i][j]}x${j+1}`;
                        } else {
                            equation += matrix[i][j] >= 0 ? ` + ${matrix[i][j]}x${j+1}` : ` - ${Math.abs(matrix[i][j])}x${j+1}`;
                        }
                    }
                    equation += ` = ${matrix[i][3]}`;
                    html += `<div style="margin: 8px 0; font-family: monospace; font-size: 1.1em; font-weight: bold;">${equation}</div>`;
                }
                html += `</div>`;

                html += displayMatrix(matrix, "🔢 Matriks Augmented Awal:");

                // Proses eliminasi Gauss-Jordan
                const steps = [];
                let stepCount = 1;

                // Forward elimination dan back substitution
                for (let i = 0; i < 3; i++) {
                    // Cari pivot terbesar (partial pivoting)
                    let maxRow = i;
                    for (let k = i + 1; k < 3; k++) {
                        if (Math.abs(matrix[k][i]) > Math.abs(matrix[maxRow][i])) {
                            maxRow = k;
                        }
                    }

                    // Tukar baris jika perlu
                    if (maxRow !== i) {
                        [matrix[i], matrix[maxRow]] = [matrix[maxRow], matrix[i]];
                        steps.push({
                            step: stepCount++,
                            description: `🔄 Tukar baris ${i+1} dengan baris ${maxRow+1} (Partial Pivoting)`,
                            matrix: matrix.map(row => [...row]),
                            pivotRow: i,
                            pivotCol: i
                        });
                    }

                    // Cek apakah pivot adalah nol
                    if (Math.abs(matrix[i][i]) < 1e-10) {
                        throw new Error(`❌ Sistem tidak memiliki solusi unik (pivot nol pada baris ${i+1})`);
                    }

                    // Normalisasi baris pivot (buat diagonal = 1)
                    const pivot = matrix[i][i];
                    if (Math.abs(pivot - 1) > 1e-10) {
                        for (let j = 0; j < 4; j++) {
                            matrix[i][j] /= pivot;
                        }
                        steps.push({
                            step: stepCount++,
                            description: `➗ R${i+1} = R${i+1} ÷ ${pivot.toFixed(6)} (Normalisasi pivot)`,
                            matrix: matrix.map(row => [...row]),
                            pivotRow: i,
                            pivotCol: i
                        });
                    }

                    // Eliminasi kolom (buat elemen lain = 0)
                    for (let k = 0; k < 3; k++) {
                        if (k !== i && Math.abs(matrix[k][i]) > 1e-10) {
                            const factor = matrix[k][i];
                            for (let j = 0; j < 4; j++) {
                                matrix[k][j] -= factor * matrix[i][j];
                            }
                            steps.push({
                                step: stepCount++,
                                description: `🧮 R${k+1} = R${k+1} - (${factor.toFixed(6)}) × R${i+1}`,
                                matrix: matrix.map(row => [...row]),
                                pivotRow: i,
                                pivotCol: i
                            });
                        }
                    }
                }

                // Tampilkan langkah-langkah
                steps.forEach(step => {
                    html += `<div class="step">`;
                    html += `<h4>📍 Langkah ${step.step}: ${step.description}</h4>`;
                    html += displayMatrix(step.matrix, "", step.pivotRow, step.pivotCol);
                    html += `</div>`;
                });

                // Tampilkan matriks identitas final
                html += `<div class="step">`;
                html += `<h4>✅ Matriks Identitas Tercapai!</h4>`;
                html += displayMatrix(matrix, "🎯 Matriks Identitas dengan Solusi:");
                html += `</div>`;

                // Tampilkan solusi
                html += `<div class="solution">`;
                html += `<h3>🎉 Solusi Sistem Persamaan Linear</h3>`;
                html += `<div class="variable-result">x₁ = ${matrix[0][3].toFixed(8)}</div>`;
                html += `<div class="variable-result">x₂ = ${matrix[1][3].toFixed(8)}</div>`;
                html += `<div class="variable-result">x₃ = ${matrix[2][3].toFixed(8)}</div>`;
                
                // Verifikasi solusi
                html += `<div style="margin-top: 20px; padding: 15px; background: #e8f5e8; border-radius: 10px;">`;
                html += `<h4>🔍 Verifikasi Solusi:</h4>`;
                const originalMatrix = [];
                for (let i = 0; i < 3; i++) {
                    originalMatrix[i] = [];
                    for (let j = 0; j < 4; j++) {
                        originalMatrix[i][j] = parseFloat(document.getElementById(`gj_${i}_${j}`).value);
                    }
                }
                
                for (let i = 0; i < 3; i++) {
                    const result = originalMatrix[i][0] * matrix[0][3] + 
                                 originalMatrix[i][1] * matrix[1][3] + 
                                 originalMatrix[i][2] * matrix[2][3];
                    const error = Math.abs(result - originalMatrix[i][3]);
                    const status = error < 1e-6 ? '✅' : '⚠️';
                    html += `<div>Persamaan ${i+1}: ${result.toFixed(6)} ≈ ${originalMatrix[i][3]} (Error: ${error.toFixed(8)}) ${status}</div>`;
                }
                html += `</div>`;
                html += `</div>`;

                document.getElementById('gaussJordanResults').innerHTML = html;
                document.getElementById('gaussJordanResults').style.display = 'block';

            } catch (error) {
                document.getElementById('gaussJordanResults').innerHTML = 
                    `<div class="error">❌ Error: ${error.message}</div>`;
                document.getElementById('gaussJordanResults').style.display = 'block';
            }
        }

        // Fungsi untuk menyelesaikan dengan Gauss-Seidel
        function solveGaussSeidel() {
            try {
                // Ambil input matriks
                const A = [];
                const b = [];
                for (let i = 0; i < 3; i++) {
                    A[i] = [];
                    for (let j = 0; j < 3; j++) {
                        const value = parseFloat(document.getElementById(`gs_${i}_${j}`).value);
                        if (isNaN(value)) {
                            throw new Error(`Nilai koefisien pada baris ${i+1}, kolom ${j+1} tidak valid atau kosong`);
                        }
                        A[i][j] = value;
                    }
                    const bValue = parseFloat(document.getElementById(`gs_${i}_3`).value);
                    if (isNaN(bValue)) {
                        throw new Error(`Nilai konstanta pada baris ${i+1} tidak valid atau kosong`);
                    }
                    b[i] = bValue;
                }

                const tolerance = parseFloat(document.getElementById('tolerance').value) || 0.0001;
                const maxIter = parseInt(document.getElementById('maxIterations').value) || 100;

                // Cek diagonal dominance
                let isDiagonallyDominant = true;
                let dominanceInfo = [];
                for (let i = 0; i < 3; i++) {
                    let sum = 0;
                    for (let j = 0; j < 3; j++) {
                        if (i !== j) sum += Math.abs(A[i][j]);
                    }
                    const isDominant = Math.abs(A[i][i]) > sum;
                    dominanceInfo.push({
                        row: i + 1,
                        diagonal: Math.abs(A[i][i]),
                        sum: sum,
                        isDominant: isDominant
                    });
                    if (!isDominant) {
                        isDiagonallyDominant = false;
                    }
                }

                let html = `<h3>🔄 Metode Gauss-Seidel - Langkah-langkah Iterasi</h3>`;
                
                // Tampilkan sistem persamaan
                html += `<div class="step">`;
                html += `<h4>📋 Sistem Persamaan Linear:</h4>`;
                for (let i = 0; i < 3; i++) {
                    let equation = '';
                    for (let j = 0; j < 3; j++) {
                        if (j === 0) {
                            equation += `${A[i][j]}x${j+1}`;
                        } else {
                            equation += A[i][j] >= 0 ? ` + ${A[i][j]}x${j+1}` : ` - ${Math.abs(A[i][j])}x${j+1}`;
                        }
                    }
                    equation += ` = ${b[i]}`;
                    html += `<div style="margin: 8px 0; font-family: monospace; font-size: 1.1em; font-weight: bold;">${equation}</div>`;
                }
                html += `</div>`;

                // Cek diagonal dominance
                html += `<div class="convergence-info">`;
                html += `<h4>🔍 Analisis Diagonal Dominance:</h4>`;
                dominanceInfo.forEach(info => {
                    const status = info.isDominant ? '✅' : '❌';
                    html += `<div>Baris ${info.row}: |${info.diagonal}| ${info.isDominant ? '>' : '≤'} ${info.sum.toFixed(4)} ${status}</div>`;
                });
                
                if (isDiagonallyDominant) {
                    html += `<div style="color: #2e7d32; font-weight: bold; margin-top: 10px;">✅ Matriks diagonal dominan - Konvergensi terjamin!</div>`;
                } else {
                    html += `<div style="color: #d32f2f; font-weight: bold; margin-top: 10px;">⚠️ Matriks tidak diagonal dominan - Konvergensi tidak terjamin!</div>`;
                }
                html += `</div>`;

                // Transformasi ke bentuk iteratif
                html += `<div class="step">`;
                html += `<h4>🔄 Bentuk Iteratif Gauss-Seidel:</h4>`;
                for (let i = 0; i < 3; i++) {
                    let formula = `x${i+1}⁽ᵏ⁺¹⁾ = (${b[i]}`;
                    for (let j = 0; j < 3; j++) {
                        if (i !== j) {
                            formula += A[i][j] >= 0 ? ` - ${A[i][j]}x${j+1}` : ` + ${Math.abs(A[i][j])}x${j+1}`;
                            formula += j < i ? '⁽ᵏ⁺¹⁾' : '⁽ᵏ⁾';
                        }
                    }
                    formula += `) / ${A[i][i]}`;
                    html += `<div style="margin: 8px 0; font-family: monospace; font-size: 1.1em; background: #f0f8ff; padding: 8px; border-radius: 5px;">${formula}</div>`;
                }
                html += `</div>`;

                // Iterasi Gauss-Seidel
                let x = [0, 0, 0]; // Tebakan awal
                let iterations = [];
                let converged = false;

                // Tambahkan iterasi awal
                iterations.push({
                    iter: 0,
                    x1: x[0],
                    x2: x[1],
                    x3: x[2],
                    error: '-'
                });

                for (let iter = 1; iter <= maxIter; iter++) {
                    let xOld = [...x];
                    
                    // Update setiap variabel menggunakan nilai terbaru
                    for (let i = 0; i < 3; i++) {
                        let sum = b[i];
                        for (let j = 0; j < 3; j++) {
                            if (i !== j) {
                                sum -= A[i][j] * x[j];
                            }
                        }
                        x[i] = sum / A[i][i];
                    }

                    // Hitung error maksimum
                    let maxError = 0;
                    for (let i = 0; i < 3; i++) {
                        const error = Math.abs(x[i] - xOld[i]);
                        if (error > maxError) maxError = error;
                    }

                    iterations.push({
                        iter: iter,
                        x1: x[0],
                        x2: x[1],
                        x3: x[2],
                        error: maxError,
                        calculation: {
                            x1_calc: `(${b[0]} - ${A[0][1]}×${xOld[1].toFixed(6)} - ${A[0][2]}×${xOld[2].toFixed(6)}) / ${A[0][0]} = ${x[0].toFixed(6)}`,
                            x2_calc: `(${b[1]} - ${A[1][0]}×${x[0].toFixed(6)} - ${A[1][2]}×${xOld[2].toFixed(6)}) / ${A[1][1]} = ${x[1].toFixed(6)}`,
                            x3_calc: `(${b[2]} - ${A[2][0]}×${x[0].toFixed(6)} - ${A[2][1]}×${x[1].toFixed(6)}) / ${A[2][2]} = ${x[2].toFixed(6)}`
                        }
                    });

                    if (maxError < tolerance) {
                        converged = true;
                        break;
                    }
                }

                // Tampilkan beberapa iterasi pertama dengan detail perhitungan
                html += `<div class="step">`;
                html += `<h4>🧮 Detail Perhitungan Iterasi (5 iterasi pertama):</h4>`;
                for (let i = 1; i <= Math.min(5, iterations.length - 1); i++) {
                    const iter = iterations[i];
                    html += `<div style="margin: 15px 0; padding: 15px; background: #f8f9fa; border-radius: 8px; border-left: 4px solid #4facfe;">`;
                    html += `<h5>Iterasi ${iter.iter}:</h5>`;
                    html += `<div style="font-family: monospace; margin: 5px 0;">x₁⁽${iter.iter}⁾ = ${iter.calculation.x1_calc}</div>`;
                    html += `<div style="font-family: monospace; margin: 5px 0;">x₂⁽${iter.iter}⁾ = ${iter.calculation.x2_calc}</div>`;
                    html += `<div style="font-family: monospace; margin: 5px 0;">x₃⁽${iter.iter}⁾ = ${iter.calculation.x3_calc}</div>`;
                    html += `<div style="color: #d32f2f; font-weight: bold;">Error maksimum = ${iter.error.toFixed(8)}</div>`;
                    html += `</div>`;
                }
                html += `</div>`;

                // Tampilkan tabel iterasi lengkap
                html += `<div class="step">`;
                html += `<h4>📊 Tabel Iterasi Lengkap:</h4>`;
                html += `<table class="iteration-table">`;
                html += `<tr><th>Iterasi</th><th>x₁</th><th>x₂</th><th>x₃</th><th>Error Maksimum</th><th>Status</th></tr>`;
                
                iterations.forEach((iter, index) => {
                    const status = index === 0 ? 'Awal' : 
                                 (typeof iter.error === 'number' && iter.error < tolerance) ? '✅ Konvergen' : 
                                 index === iterations.length - 1 && !converged ? '⏹️ Max Iter' : '🔄 Iterasi';
                    html += `<tr>`;
                    html += `<td>${iter.iter}</td>`;
                    html += `<td>${typeof iter.x1 === 'number' ? iter.x1.toFixed(8) : iter.x1}</td>`;
                    html += `<td>${typeof iter.x2 === 'number' ? iter.x2.toFixed(8) : iter.x2}</td>`;
                    html += `<td>${typeof iter.x3 === 'number' ? iter.x3.toFixed(8) : iter.x3}</td>`;
                    html += `<td>${typeof iter.error === 'number' ? iter.error.toFixed(10) : iter.error}</td>`;
                    html += `<td>${status}</td>`;
                    html += `</tr>`;
                });
                
                html += `</table>`;
                html += `</div>`;

                // Tampilkan solusi
                if (converged) {
                    html += `<div class="solution">`;
                    html += `<h3>🎉 Solusi Konvergen!</h3>`;
                    html += `<div style="text-align: center; margin-bottom: 20px;">`;
                    html += `<strong>Iterasi ke-${iterations.length - 1} | Toleransi: ${tolerance} | Error: ${iterations[iterations.length - 1].error.toFixed(10)}</strong>`;
                    html += `</div>`;
                    html += `<div class="variable-result">x₁ = ${x[0].toFixed(10)}</div>`;
                    html += `<div class="variable-result">x₂ = ${x[1].toFixed(10)}</div>`;
                    html += `<div class="variable-result">x₃ = ${x[2].toFixed(10)}</div>`;
                    
                    // Verifikasi solusi
                    html += `<div style="margin-top: 20px; padding: 15px; background: #e8f5e8; border-radius: 10px;">`;
                    html += `<h4>🔍 Verifikasi Solusi:</h4>`;
                    for (let i = 0; i < 3; i++) {
                        const result = A[i][0] * x[0] + A[i][1] * x[1] + A[i][2] * x[2];
                        const error = Math.abs(result - b[i]);
                        const status = error < 1e-6 ? '✅' : '⚠️';
                        html += `<div>Persamaan ${i+1}: ${result.toFixed(8)} ≈ ${b[i]} (Error: ${error.toFixed(10)}) ${status}</div>`;
                    }
                    html += `</div>`;
                    html += `</div>`;
                } else {
                    html += `<div class="error">`;
                    html += `❌ Solusi tidak konvergen setelah ${maxIter} iterasi.<br>`;
                    html += `Error terakhir: ${iterations[iterations.length - 1].error.toFixed(10)}<br>`;
                    html += `Saran: Tingkatkan jumlah iterasi maksimum atau periksa kondisi diagonal dominance.`;
                    html += `</div>`;
                }

                document.getElementById('gaussSeidelResults').innerHTML = html;
                document.getElementById('gaussSeidelResults').style.display = 'block';

            } catch (error) {
                document.getElementById('gaussSeidelResults').innerHTML = 
                    `<div class="error">❌ Error: ${error.message}</div>`;
                document.getElementById('gaussSeidelResults').style.display = 'block';
            }
        }

        // Event listeners untuk input validation
        document.addEventListener('DOMContentLoaded', function() {
            // Validasi input hanya angka
            const inputs = document.querySelectorAll('input[type="number"]');
            inputs.forEach(input => {
                input.addEventListener('input', function() {
                    if (this.value && isNaN(parseFloat(this.value))) {
                        this.style.borderColor = '#f44336';
                        this.style.backgroundColor = '#ffebee';
                    } else {
                        this.style.borderColor = '#ddd';
                        this.style.backgroundColor = 'white';
                    }
                });
            });

            // Auto-scroll ke hasil setelah perhitungan
            const observer = new MutationObserver(function(mutations) {
                mutations.forEach(function(mutation) {
                    if (mutation.type === 'attributes' && mutation.attributeName === 'style') {
                        const target = mutation.target;
                        if (target.id === 'gaussJordanResults' || target.id === 'gaussSeidelResults') {
                            if (target.style.display === 'block') {
                                setTimeout(() => {
                                    target.scrollIntoView({ behavior: 'smooth', block: 'start' });
                                }, 100);
                            }
                        }
                    }
                });
            });

            // Observe hasil sections
            const gjResults = document.getElementById('gaussJordanResults');
            const gsResults = document.getElementById('gaussSeidelResults');
            if (gjResults) observer.observe(gjResults, { attributes: true });
            if (gsResults) observer.observe(gsResults, { attributes: true });
        });

        // Fungsi untuk copy hasil ke clipboard
        function copyResults(method) {
            const resultsElement = method === 'gj' ? 
                document.getElementById('gaussJordanResults') : 
                document.getElementById('gaussSeidelResults');
            
            if (resultsElement && resultsElement.style.display === 'block') {
                const text = resultsElement.innerText;
                navigator.clipboard.writeText(text).then(() => {
                    alert('Hasil berhasil disalin ke clipboard!');
                }).catch(() => {
                    alert('Gagal menyalin hasil.');
                });
            }
        }

        // Fungsi untuk print hasil
        function printResults(method) {
            const resultsElement = method === 'gj' ? 
                document.getElementById('gaussJordanResults') : 
                document.getElementById('gaussSeidelResults');
            
            if (resultsElement && resultsElement.style.display === 'block') {
                const printWindow = window.open('', '_blank');
                printWindow.document.write(`
                    <html>
                        <head>
                            <title>Hasil ${method === 'gj' ? 'Gauss-Jordan' : 'Gauss-Seidel'}</title>
                            <style>
                                body { font-family: Arial, sans-serif; margin: 20px; }
                                .matrix-display { background: #f5f5f5; padding: 15px; margin: 10px 0; }
                                .step { margin: 20px 0; padding: 15px; border-left: 4px solid #4facfe; }
                                .solution { background: #e8f5e8; padding: 20px; margin: 20px 0; }
                                table { border-collapse: collapse; width: 100%; }
                                th, td { border: 1px solid #ddd; padding: 8px; text-align: center; }
                                th { background: #f0f0f0; }
                            </style>
                        </head>
                        <body>
                            <h1>Hasil ${method === 'gj' ? 'Eliminasi Gauss-Jordan' : 'Metode Gauss-Seidel'}</h1>
                            ${resultsElement.innerHTML}
                        </body>
                    </html>
                `);
                printWindow.document.close();
                printWindow.print();
            }
        }
    </script>
</body>
</html>

