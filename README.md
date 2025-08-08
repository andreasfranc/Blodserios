<html lang="no"><head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Blodseriøs</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Inter', 'SF Pro Display', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
            background: linear-gradient(135deg, #F8F2DE 0%, #ECDCBF 50%, #F8F2DE 100%);
            min-height: 100vh;
            padding: 40px 20px;
            position: relative;
        }

        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: radial-gradient(circle at 20% 50%, rgba(216, 64, 64, 0.1) 0%, transparent 50%),
                        radial-gradient(circle at 80% 20%, rgba(163, 29, 29, 0.08) 0%, transparent 50%);
            pointer-events: none;
            z-index: 0;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 24px;
            padding: 40px;
            box-shadow: 
                0 32px 64px rgba(163, 29, 29, 0.12),
                0 16px 32px rgba(0, 0, 0, 0.08),
                inset 0 1px 0 rgba(255, 255, 255, 0.4);
            backdrop-filter: blur(20px);
            position: relative;
            z-index: 1;
            border: 1px solid rgba(236, 220, 191, 0.3);
        }

        h1 {
            color: #A31D1D;
            text-align: center;
            margin-bottom: 40px;
            font-size: 3rem;
            font-weight: 700;
            letter-spacing: -0.02em;
            position: relative;
        }

        h1::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 4px;
            background: linear-gradient(90deg, #D84040, #A31D1D);
            border-radius: 2px;
        }

        .form-section {
            background: linear-gradient(145deg, #FFFFFF 0%, #F8F2DE 100%);
            padding: 32px;
            border-radius: 20px;
            margin-bottom: 32px;
            box-shadow: 
                0 8px 32px rgba(163, 29, 29, 0.08),
                0 1px 4px rgba(0, 0, 0, 0.04);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            border: 1px solid rgba(236, 220, 191, 0.4);
            position: relative;
            overflow: hidden;
        }

        .form-section::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(90deg, #D84040, #A31D1D, #D84040);
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .form-section:hover {
            transform: translateY(-4px);
            box-shadow: 
                0 16px 48px rgba(163, 29, 29, 0.12),
                0 4px 16px rgba(0, 0, 0, 0.08);
        }

        .form-section:hover::before {
            opacity: 1;
        }

        .form-section h2 {
            color: #A31D1D;
            font-weight: 600;
            font-size: 1.5rem;
            margin-bottom: 24px;
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .form-group {
            margin-bottom: 24px;
        }

        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
        }

        label {
            display: block;
            font-weight: 500;
            color: #2C1810;
            margin-bottom: 10px;
            font-size: 1rem;
            letter-spacing: -0.01em;
            position: relative;
            cursor: help;
        }

        .tooltip {
            position: relative;
            display: inline-block;
        }

        .tooltip .tooltiptext {
            visibility: hidden;
            width: 280px;
            background: linear-gradient(135deg, #2C1810 0%, #A31D1D 100%);
            color: #FFFFFF;
            text-align: left;
            border-radius: 12px;
            padding: 12px 16px;
            position: absolute;
            z-index: 1000;
            top: 125%;
            left: 50%;
            margin-left: -140px;
            opacity: 0;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            font-size: 0.875rem;
            line-height: 1.4;
            font-weight: 400;
            box-shadow: 0 8px 24px rgba(163, 29, 29, 0.3);
            border: 1px solid rgba(236, 220, 191, 0.2);
        }

        .tooltip .tooltiptext::after {
            content: "";
            position: absolute;
            bottom: 100%;
            left: 50%;
            margin-left: -6px;
            border-width: 6px;
            border-style: solid;
            border-color: transparent transparent #A31D1D transparent;
        }

        .tooltip:hover .tooltiptext {
            visibility: visible;
            opacity: 1;
            transform: translateY(2px);
        }

        /* Ensure tooltips don't get cut off at container edges */
        .tooltip .tooltiptext {
            max-width: calc(100vw - 40px);
        }

        /* Adjust tooltip position for edge cases */
        .form-row .form-group:first-child .tooltip .tooltiptext {
            left: 0;
            margin-left: 0;
        }

        .form-row .form-group:last-child .tooltip .tooltiptext {
            right: 0;
            left: auto;
            margin-left: 0;
        }

        .info-icon {
            display: inline-block;
            width: 16px;
            height: 16px;
            background: #D84040;
            color: white;
            border-radius: 50%;
            text-align: center;
            line-height: 16px;
            font-size: 12px;
            font-weight: 600;
            margin-left: 6px;
            cursor: help;
        }

        input[type="number"] {
            width: 100%;
            padding: 16px 20px;
            border: 2px solid #ECDCBF;
            border-radius: 12px;
            font-size: 16px;
            font-weight: 500;
            background: #FFFFFF;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            color: #2C1810;
        }

        input[type="number"]:focus {
            outline: none;
            border-color: #D84040;
            box-shadow: 
                0 0 0 4px rgba(216, 64, 64, 0.1),
                0 4px 16px rgba(163, 29, 29, 0.1);
            transform: translateY(-1px);
        }

        input[type="number"]::placeholder {
            color: #8B7355;
        }

        .unit {
            color: #8B7355;
            font-size: 0.875rem;
            font-weight: 400;
            margin-left: 6px;
        }

        .submit-btn {
            background: linear-gradient(135deg, #D84040 0%, #A31D1D 100%);
            color: white;
            border: none;
            padding: 20px 40px;
            border-radius: 16px;
            font-size: 18px;
            font-weight: 600;
            cursor: pointer;
            width: 100%;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            box-shadow: 
                0 8px 24px rgba(216, 64, 64, 0.25),
                0 2px 8px rgba(0, 0, 0, 0.1);
            letter-spacing: -0.01em;
            position: relative;
            overflow: hidden;
        }

        .submit-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: left 0.5s;
        }

        .submit-btn:hover {
            transform: translateY(-3px);
            box-shadow: 
                0 16px 40px rgba(216, 64, 64, 0.35),
                0 4px 16px rgba(0, 0, 0, 0.15);
        }

        .submit-btn:hover::before {
            left: 100%;
        }

        .submit-btn:active {
            transform: translateY(-1px);
        }

        .results {
            background: linear-gradient(145deg, #FFFFFF 0%, #F8F2DE 100%);
            padding: 32px;
            border-radius: 20px;
            margin-top: 32px;
            box-shadow: 
                0 8px 32px rgba(163, 29, 29, 0.08),
                0 1px 4px rgba(0, 0, 0, 0.04);
            display: none;
            border: 1px solid rgba(236, 220, 191, 0.4);
        }

        .results h2 {
            color: #A31D1D;
            font-weight: 600;
            font-size: 1.5rem;
            margin-bottom: 24px;
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .health-status {
            display: flex;
            align-items: center;
            margin-bottom: 16px;
            padding: 18px 24px;
            border-radius: 12px;
            font-weight: 500;
            transition: all 0.2s ease;
            position: relative;
            overflow: hidden;
        }

        .health-status::before {
            content: '';
            position: absolute;
            left: 0;
            top: 0;
            bottom: 0;
            width: 4px;
        }

        .status-good {
            background: linear-gradient(135deg, #F0F9F0 0%, #E8F5E8 100%);
            color: #1B5E20;
            border: 1px solid #C8E6C9;
        }

        .status-good::before {
            background: #4CAF50;
        }

        .status-warning {
            background: linear-gradient(135deg, #FFFBF0 0%, #FFF8E1 100%);
            color: #E65100;
            border: 1px solid #FFE0B2;
        }

        .status-warning::before {
            background: #FF9800;
        }

        .status-danger {
            background: linear-gradient(135deg, #FFF5F5 0%, #FFEBEE 100%);
            color: #A31D1D;
            border: 1px solid #FFCDD2;
        }

        .status-danger::before {
            background: #D84040;
        }

        .advice-section {
            background: linear-gradient(135deg, #F8F2DE 0%, #ECDCBF 100%);
            padding: 28px;
            border-radius: 16px;
            margin-top: 24px;
            border: 1px solid rgba(163, 29, 29, 0.15);
        }

        .advice-title {
            font-size: 1.25rem;
            font-weight: 600;
            color: #A31D1D;
            margin-bottom: 18px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .advice-list {
            list-style: none;
            padding: 0;
        }

        .advice-list li {
            padding: 10px 0;
            padding-left: 32px;
            position: relative;
            color: #2C1810;
            line-height: 1.6;
            font-weight: 400;
        }

        .advice-list li:before {
            content: "▸";
            position: absolute;
            left: 12px;
            color: #D84040;
            font-weight: 700;
        }

        .disclaimer {
            background: linear-gradient(135deg, #ECDCBF 0%, #F8F2DE 100%);
            padding: 20px;
            border-radius: 12px;
            margin-top: 24px;
            font-size: 0.9rem;
            color: #5D4E37;
            text-align: center;
            border: 1px solid rgba(163, 29, 29, 0.2);
            font-weight: 500;
        }

        @media (max-width: 768px) {
            .container {
                padding: 24px;
                margin: 16px;
            }
            
            h1 {
                font-size: 2.5rem;
            }

            .form-row {
                grid-template-columns: 1fr;
            }

            .form-section {
                padding: 24px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>🩸 Blodseriøs</h1>
        
        <div id="healthForm">
            <div class="form-section" style="opacity: 1; transform: translateY(0px); transition: opacity 0.6s, transform 0.6s;">
                <h2>🫀 Kardiovaskulær risiko</h2>
                
                <div class="form-row">
                    <div class="form-group">
                        <label for="totalCholesterol" class="tooltip">
                            Total kolesterol <span class="unit">(mg/dL)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">Totalt kolesterol i blodet. Høye nivåer øker risikoen for hjerte- og karsykdom. Inkluderer både "dårlig" LDL og "bra" HDL kolesterol.</span>
                        </label>
                        <input type="number" id="totalCholesterol" step="1" min="0" max="500" placeholder="200">
                    </div>

                    <div class="form-group">
                        <label for="ldlCholesterol" class="tooltip">
                            LDL kolesterol <span class="unit">(mg/dL)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">"Dårlig" kolesterol som kan bygge opp plakk i arteriene. Lavere verdier reduserer risikoen for hjerteinfarkt og hjerneslag.</span>
                        </label>
                        <input type="number" id="ldlCholesterol" step="1" min="0" max="300" placeholder="100">
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="hdlCholesterol" class="tooltip">
                            HDL kolesterol <span class="unit">(mg/dL)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">"Bra" kolesterol som hjelper til med å fjerne LDL fra arteriene. Høyere verdier beskytter mot hjerte- og karsykdom.</span>
                        </label>
                        <input type="number" id="hdlCholesterol" step="1" min="0" max="150" placeholder="50">
                    </div>

                    <div class="form-group">
                        <label for="triglycerides" class="tooltip">
                            Triglyserider <span class="unit">(mg/dL)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">Fettmolekyler i blodet som lagrer energi. Høye nivåer øker risikoen for hjertesykdom og kan indikere diabetes eller metabolsk syndrom.</span>
                        </label>
                        <input type="number" id="triglycerides" step="1" min="0" max="1000" placeholder="150">
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="bloodPressureSystolic" class="tooltip">
                            Blodtrykk systolisk <span class="unit">(mmHg)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">Trykket i arteriene når hjertet pumper ut blod. Det øverste tallet i blodtrykksmålingen. Høye verdier øker risikoen for hjerteinfarkt.</span>
                        </label>
                        <input type="number" id="bloodPressureSystolic" step="1" min="60" max="250" placeholder="120">
                    </div>

                    <div class="form-group">
                        <label for="bloodPressureDiastolic" class="tooltip">
                            Blodtrykk diastolisk <span class="unit">(mmHg)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">Trykket i arteriene når hjertet hviler mellom slag. Det nederste tallet i blodtrykksmålingen. Viser hvor mye motstand det er i blodkarene.</span>
                        </label>
                        <input type="number" id="bloodPressureDiastolic" step="1" min="40" max="150" placeholder="80">
                    </div>
                </div>
            </div>

            <div class="form-section" style="opacity: 1; transform: translateY(0px); transition: opacity 0.6s, transform 0.6s;">
                <h2>🩸 Blodstatus &amp; Jern</h2>
                
                <div class="form-row">
                    <div class="form-group">
                        <label for="hemoglobin" class="tooltip">
                            Hemoglobin <span class="unit">(g/dL)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">Jernholdig protein i røde blodceller som transporterer oksygen. Lave verdier kan indikere anemi, høye verdier dehydrering eller polycythemia.</span>
                        </label>
                        <input type="number" id="hemoglobin" step="0.1" min="0" max="25" placeholder="14.0">
                    </div>

                    <div class="form-group">
                        <label for="hematocrit" class="tooltip">
                            Hematokrit <span class="unit">(%)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">Prosentandelen av blodet som består av røde blodceller. Sammen med hemoglobin brukes dette for å diagnostisere anemi og polycythemia.</span>
                        </label>
                        <input type="number" id="hematocrit" step="0.1" min="0" max="60" placeholder="42">
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="wbc" class="tooltip">
                            Hvite blodceller <span class="unit">(×10³/μL)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">Immunsystemets celler som bekjemper infeksjoner. Høye verdier kan indikere infeksjon eller betennelse, lave verdier immunsvekkelse.</span>
                        </label>
                        <input type="number" id="wbc" step="0.1" min="0" max="50" placeholder="7.0">
                    </div>

                    <div class="form-group">
                        <label for="platelets" class="tooltip">
                            Blodplater <span class="unit">(×10³/μL)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">Små celler som hjelper blodet å koagulere. Lave verdier øker blødningsrisiko, høye verdier kan øke risikoen for blodpropp.</span>
                        </label>
                        <input type="number" id="platelets" step="1" min="0" max="1000" placeholder="250">
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="ferritin" class="tooltip">
                            Ferritin <span class="unit">(ng/mL)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">Protein som lagrer jern i kroppen. Lavt ferritin indikerer jernmangel, høyt kan indikere jernopphopning eller betennelse.</span>
                        </label>
                        <input type="number" id="ferritin" step="1" min="0" max="1000" placeholder="100">
                    </div>

                    <div class="form-group">
                        <label for="ironSaturation" class="tooltip">
                            Jerntransferrin metning <span class="unit">(%)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">Hvor mye av transportproteinet transferrin som er mettet med jern. Viser hvor tilgjengelig jern er for kroppsbruk.</span>
                        </label>
                        <input type="number" id="ironSaturation" step="1" min="0" max="100" placeholder="25">
                    </div>
                </div>
            </div>

            <div class="form-section" style="opacity: 1; transform: translateY(0px); transition: opacity 0.6s, transform 0.6s;">
                <h2>🍯 Diabetes &amp; Metabolisme</h2>
                
                <div class="form-row">
                    <div class="form-group">
                        <label for="hba1c" class="tooltip">
                            HbA1c <span class="unit">(%)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">Langtids blodsukkertest som viser gjennomsnittlig blodsukkernivå de siste 2-3 månedene. Gullstandarden for diabetesdiagnose.</span>
                        </label>
                        <input type="number" id="hba1c" step="0.1" min="0" max="20" placeholder="5.5">
                    </div>

                    <div class="form-group">
                        <label for="bloodSugar" class="tooltip">
                            Fastende glukose <span class="unit">(mg/dL)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">Blodsukkernivå etter 8-12 timers faste. Brukes for å screene for diabetes og prediabetes. Bør kombineres med HbA1c for best vurdering.</span>
                        </label>
                        <input type="number" id="bloodSugar" step="1" min="0" max="400" placeholder="90">
                    </div>
                </div>
            </div>

            <div class="form-section" style="opacity: 1; transform: translateY(0px); transition: opacity 0.6s, transform 0.6s;">
                <h2>🫘 Nyre &amp; Leverfunksjon</h2>
                
                <div class="form-row">
                    <div class="form-group">
                        <label for="creatinine" class="tooltip">
                            Kreatinin <span class="unit">(mg/dL)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">Avfallsprodukt fra muskelmetabolisme som skilles ut av nyrene. Høye verdier kan indikere nedsatt nyrefunksjon.</span>
                        </label>
                        <input type="number" id="creatinine" step="0.01" min="0" max="10" placeholder="1.0">
                    </div>

                    <div class="form-group">
                        <label for="egfr" class="tooltip">
                            eGFR <span class="unit">(mL/min/1.73m²)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">Estimert glomerulær filtrasjonshastighet - mål på hvor godt nyrene filtrerer avfallsstoffer fra blodet. Verdier under 60 indikerer nyresykdom.</span>
                        </label>
                        <input type="number" id="egfr" step="1" min="0" max="150" placeholder="90">
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="alt" class="tooltip">
                            ALT <span class="unit">(U/L)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">Alanin aminotransferase - enzym som hovedsakelig finnes i leveren. Forhøyede verdier kan indikere leverskade eller leverbetennelse.</span>
                        </label>
                        <input type="number" id="alt" step="1" min="0" max="500" placeholder="25">
                    </div>

                    <div class="form-group">
                        <label for="ast" class="tooltip">
                            AST <span class="unit">(U/L)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">Aspartat aminotransferase - enzym i lever, hjerte og muskler. Forhøyede verdier kan indikere skade på disse organene.</span>
                        </label>
                        <input type="number" id="ast" step="1" min="0" max="500" placeholder="25">
                    </div>
                </div>
            </div>

            <div class="form-section" style="opacity: 1; transform: translateY(0px); transition: opacity 0.6s, transform 0.6s;">
                <h2>🦴 Hormoner &amp; Vitaminer</h2>
                
                <div class="form-row">
                    <div class="form-group">
                        <label for="tsh" class="tooltip">
                            TSH <span class="unit">(mIU/L)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">Thyreoidea stimulerende hormon fra hypofysen som regulerer skjoldbruskkjertelen. Høye verdier kan indikere underaktiv skjoldbruskjertel.</span>
                        </label>
                        <input type="number" id="tsh" step="0.01" min="0" max="50" placeholder="2.5">
                    </div>

                    <div class="form-group">
                        <label for="vitaminD" class="tooltip">
                            Vitamin D <span class="unit">(ng/mL)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">Viktig for beinhelse, immunsystem og muskelfunksjon. Mangel er vanlig i Norge på grunn av begrenset sollys, spesielt om vinteren.</span>
                        </label>
                        <input type="number" id="vitaminD" step="0.1" min="0" max="150" placeholder="30">
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="b12" class="tooltip">
                            Vitamin B12 <span class="unit">(pg/mL)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">Essensielt vitamin for nervesystemet og produksjon av røde blodceller. Mangel kan gi tretthet, nevrologiske symptomer og anemi.</span>
                        </label>
                        <input type="number" id="b12" step="1" min="0" max="2000" placeholder="400">
                    </div>

                    <div class="form-group">
                        <label for="crp" class="tooltip">
                            CRP <span class="unit">(mg/L)</span>
                            <span class="info-icon">i</span>
                            <span class="tooltiptext">C-reaktivt protein - markør for betennelse i kroppen. Forhøyede verdier kan indikere infeksjon, kronisk betennelse eller økt kardiovaskulær risiko.</span>
                        </label>
                        <input type="number" id="crp" step="0.1" min="0" max="100" placeholder="1.0">
                    </div>
                </div>
            </div>

            <button type="button" id="analyzeBtn" class="submit-btn">📈 Analyser komplette blodverdier</button>
        </div>

        <div id="results" class="results">
            <h2>📋 Dine resultater</h2>
            <div id="statusContainer"></div>
            <div id="adviceContainer"></div>
        </div>
    </div>

    <script>
        const healthRanges = {
            // Cardiovascular
            totalCholesterol: { ideal: 200, borderline: 240, high: 240 },
            ldlCholesterol: { optimal: 100, nearOptimal: 130, borderline: 160, high: 190 },
            hdlCholesterol: { 
                male: { low: 40, good: 60 },
                female: { low: 50, good: 60 }
            },
            triglycerides: { normal: 150, borderline: 200, high: 500 },
            bloodPressure: {
                normal: { systolic: 120, diastolic: 80 },
                elevated: { systolic: 130, diastolic: 80 },
                stage1: { systolic: 140, diastolic: 90 },
                stage2: { systolic: 180, diastolic: 120 }
            },
            
            // Blood status
            hemoglobin: {
                male: { low: 13.8, high: 17.2 },
                female: { low: 12.1, high: 15.1 }
            },
            hematocrit: {
                male: { low: 41, high: 50 },
                female: { low: 36, high: 44 }
            },
            wbc: { low: 4.5, high: 11.0 },
            platelets: { low: 150, high: 450 },
            
            // Iron studies
            ferritin: {
                male: { low: 30, high: 400 },
                female: { low: 15, high: 150 }
            },
            ironSaturation: { low: 20, high: 50 },
            
            // Diabetes
            hba1c: { normal: 5.7, prediabetes: 6.5, diabetes: 6.5 },
            bloodSugar: { normal: 100, prediabetes: 126, diabetes: 126 },
            
            // Kidney & Liver
            creatinine: {
                male: { low: 0.7, high: 1.3 },
                female: { low: 0.6, high: 1.1 }
            },
            egfr: { stage1: 90, stage2: 60, stage3: 30, stage4: 15 },
            alt: { normal: 40 },
            ast: { normal: 40 },
            
            // Hormones & Vitamins
            tsh: { low: 0.27, high: 4.2 },
            vitaminD: { deficient: 20, insufficient: 30, optimal: 30 },
            b12: { low: 300, high: 900 },
            crp: { normal: 3.0, high: 10.0 }
        };

        function analyzeHealth(data) {
            const results = [];
            const advice = [];

            // Cardiovascular Risk Assessment
            analyzeCardiovascular(data, results, advice);
            
            // Blood Status & Iron
            analyzeBloodStatus(data, results, advice);
            
            // Diabetes & Metabolism
            analyzeDiabetes(data, results, advice);
            
            // Kidney & Liver Function
            analyzeKidneyLiver(data, results, advice);
            
            // Hormones & Vitamins
            analyzeHormonesVitamins(data, results, advice);

            // If no data entered
            if (results.length === 0) {
                results.push({ type: 'warning', text: 'Ingen gyldige verdier registrert. Vennligst fyll ut tilgjengelige blodverdier.' });
                advice.push('Fyll ut de blodverdiene du har tilgjengelig fra din siste blodprøve');
                advice.push('Du trenger ikke fylle ut alle feltene for å få en analyse');
            }

            // General advice if everything is normal
            if (advice.length === 0) {
                advice.push('Gratulerer! Dine blodverdier ser bra ut');
                advice.push('Fortsett med et sunt kosthold og regelmessig fysisk aktivitet');
                advice.push('Ta årlige helsekontroller for å overvåke endringer');
            }

            return { results, advice };
        }

        function analyzeCardiovascular(data, results, advice) {
            // Total cholesterol
            const totalChol = parseFloat(data.totalCholesterol);
            if (totalChol && !isNaN(totalChol)) {
                if (totalChol < 200) {
                    results.push({ type: 'good', text: `Total kolesterol: ${totalChol} mg/dL - Ønskelig` });
                } else if (totalChol < 240) {
                    results.push({ type: 'warning', text: `Total kolesterol: ${totalChol} mg/dL - Grensehøyt` });
                    advice.push('Reduser inntak av mettet fett og øk fiber i kosten');
                } else {
                    results.push({ type: 'danger', text: `Total kolesterol: ${totalChol} mg/dL - Høyt` });
                    advice.push('Konsulter lege om kolesterolbehandling og kostholdsråd');
                }
            }

            // LDL cholesterol
            const ldl = parseFloat(data.ldlCholesterol);
            if (ldl && !isNaN(ldl)) {
                if (ldl < 100) {
                    results.push({ type: 'good', text: `LDL kolesterol: ${ldl} mg/dL - Optimalt` });
                } else if (ldl < 130) {
                    results.push({ type: 'good', text: `LDL kolesterol: ${ldl} mg/dL - Nær optimalt` });
                } else if (ldl < 160) {
                    results.push({ type: 'warning', text: `LDL kolesterol: ${ldl} mg/dL - Grensehøyt` });
                    advice.push('Øk inntak av plantefiber og reduser rødt kjøtt');
                } else {
                    results.push({ type: 'danger', text: `LDL kolesterol: ${ldl} mg/dL - Høyt` });
                    advice.push('Vurder medikamentell behandling med lege');
                }
            }

            // HDL cholesterol
            const hdl = parseFloat(data.hdlCholesterol);
            if (hdl && !isNaN(hdl)) {
                if (hdl >= 60) {
                    results.push({ type: 'good', text: `HDL kolesterol: ${hdl} mg/dL - Høyt (beskyttende)` });
                } else if (hdl >= 40) {
                    results.push({ type: 'warning', text: `HDL kolesterol: ${hdl} mg/dL - Akseptabelt` });
                    advice.push('Øk kardiovaskulær trening for å heve HDL');
                } else {
                    results.push({ type: 'danger', text: `HDL kolesterol: ${hdl} mg/dL - Lavt` });
                    advice.push('Prioriter regelmessig trening og sunt fett fra nøtter/fisk');
                }
            }

            // Triglycerides
            const trig = parseFloat(data.triglycerides);
            if (trig && !isNaN(trig)) {
                if (trig < 150) {
                    results.push({ type: 'good', text: `Triglyserider: ${trig} mg/dL - Normalt` });
                } else if (trig < 200) {
                    results.push({ type: 'warning', text: `Triglyserider: ${trig} mg/dL - Grensehøyt` });
                    advice.push('Reduser sukker og raffinerte karbohydrater');
                } else {
                    results.push({ type: 'danger', text: `Triglyserider: ${trig} mg/dL - Høyt` });
                    advice.push('Unngå alkohol og søte drikker, øk omega-3 inntak');
                }
            }

            // Blood pressure
            const systolic = parseFloat(data.bloodPressureSystolic);
            const diastolic = parseFloat(data.bloodPressureDiastolic);
            if (systolic && diastolic && !isNaN(systolic) && !isNaN(diastolic)) {
                if (systolic < 120 && diastolic < 80) {
                    results.push({ type: 'good', text: `Blodtrykk: ${systolic}/${diastolic} mmHg - Optimalt` });
                } else if (systolic < 130 && diastolic < 80) {
                    results.push({ type: 'warning', text: `Blodtrykk: ${systolic}/${diastolic} mmHg - Forhøyet` });
                    advice.push('Reduser saltinntak og øk kaliumrike matvarer');
                } else if (systolic < 140 || diastolic < 90) {
                    results.push({ type: 'warning', text: `Blodtrykk: ${systolic}/${diastolic} mmHg - Stadium 1 hypertensjon` });
                    advice.push('Konsulter lege om blodtrykksmedisin og livsstilsendringer');
                } else {
                    results.push({ type: 'danger', text: `Blodtrykk: ${systolic}/${diastolic} mmHg - Stadium 2 hypertensjon` });
                    advice.push('Søk medisinsk behandling umiddelbart - høyt blodtrykk');
                }
            }
        }

        function analyzeBloodStatus(data, results, advice) {
            // Hemoglobin
            const hb = parseFloat(data.hemoglobin);
            if (hb && !isNaN(hb)) {
                if (hb < 12.1) {
                    results.push({ type: 'danger', text: `Hemoglobin: ${hb} g/dL - Lavt (anemi)` });
                    advice.push('Øk jerninntak og undersøk årsak til anemi med lege');
                } else if (hb > 17.2) {
                    results.push({ type: 'warning', text: `Hemoglobin: ${hb} g/dL - Høyt` });
                    advice.push('Høyt hemoglobin kan indikere dehydrering eller polycythemia');
                } else {
                    results.push({ type: 'good', text: `Hemoglobin: ${hb} g/dL - Normalt` });
                }
            }

            // White blood cells
            const wbc = parseFloat(data.wbc);
            if (wbc && !isNaN(wbc)) {
                if (wbc < 4.5) {
                    results.push({ type: 'warning', text: `Hvite blodceller: ${wbc} ×10³/μL - Lavt` });
                    advice.push('Lavt antall hvite blodceller kan indikere immunsvekkelse');
                } else if (wbc > 11.0) {
                    results.push({ type: 'warning', text: `Hvite blodceller: ${wbc} ×10³/μL - Høyt` });
                    advice.push('Forhøyede hvite blodceller kan indikere infeksjon eller betennelse');
                } else {
                    results.push({ type: 'good', text: `Hvite blodceller: ${wbc} ×10³/μL - Normalt` });
                }
            }

            // Platelets
            const plt = parseFloat(data.platelets);
            if (plt && !isNaN(plt)) {
                if (plt < 150) {
                    results.push({ type: 'warning', text: `Blodplater: ${plt} ×10³/μL - Lavt` });
                    advice.push('Lave blodplater øker blødningsrisiko - følg opp med lege');
                } else if (plt > 450) {
                    results.push({ type: 'warning', text: `Blodplater: ${plt} ×10³/μL - Høyt` });
                    advice.push('Høye blodplater kan øke risiko for blodpropp');
                } else {
                    results.push({ type: 'good', text: `Blodplater: ${plt} ×10³/μL - Normalt` });
                }
            }

            // Ferritin
            const ferritin = parseFloat(data.ferritin);
            if (ferritin && !isNaN(ferritin)) {
                if (ferritin < 30) {
                    results.push({ type: 'danger', text: `Ferritin: ${ferritin} ng/mL - Lavt (jernmangel)` });
                    advice.push('Ta jerntilskudd og spis jernrike matvarer som rødt kjøtt og spinat');
                } else if (ferritin > 300) {
                    results.push({ type: 'warning', text: `Ferritin: ${ferritin} ng/mL - Høyt` });
                    advice.push('Høyt ferritin kan indikere jernopphopning eller betennelse');
                } else {
                    results.push({ type: 'good', text: `Ferritin: ${ferritin} ng/mL - Normalt` });
                }
            }
        }

        function analyzeDiabetes(data, results, advice) {
            // HbA1c
            const hba1c = parseFloat(data.hba1c);
            if (hba1c && !isNaN(hba1c)) {
                if (hba1c < 5.7) {
                    results.push({ type: 'good', text: `HbA1c: ${hba1c}% - Normalt` });
                } else if (hba1c < 6.5) {
                    results.push({ type: 'warning', text: `HbA1c: ${hba1c}% - Prediabetes` });
                    advice.push('Reduser karbohydrater og øk fysisk aktivitet for å forebygge diabetes');
                } else {
                    results.push({ type: 'danger', text: `HbA1c: ${hba1c}% - Diabetes` });
                    advice.push('Konsulter lege for diabetesbehandling og kostholdsplan');
                }
            }

            // Fasting glucose
            const glucose = parseFloat(data.bloodSugar);
            if (glucose && !isNaN(glucose)) {
                if (glucose < 100) {
                    results.push({ type: 'good', text: `Fastende glukose: ${glucose} mg/dL - Normalt` });
                } else if (glucose < 126) {
                    results.push({ type: 'warning', text: `Fastende glukose: ${glucose} mg/dL - Prediabetes` });
                    advice.push('Kontroller kosthold og vurder HbA1c test');
                } else {
                    results.push({ type: 'danger', text: `Fastende glukose: ${glucose} mg/dL - Diabetes` });
                    advice.push('Søk medisinsk oppfølging for diabetes umiddelbart');
                }
            }
        }

        function analyzeKidneyLiver(data, results, advice) {
            // Creatinine & eGFR
            const creatinine = parseFloat(data.creatinine);
            const egfr = parseFloat(data.egfr);
            
            if (egfr && !isNaN(egfr)) {
                if (egfr >= 90) {
                    results.push({ type: 'good', text: `eGFR: ${egfr} mL/min/1.73m² - Normal nyrefunksjon` });
                } else if (egfr >= 60) {
                    results.push({ type: 'warning', text: `eGFR: ${egfr} mL/min/1.73m² - Lett redusert nyrefunksjon` });
                    advice.push('Overvåk nyrefunksjon og kontroller blodtrykk');
                } else if (egfr >= 30) {
                    results.push({ type: 'warning', text: `eGFR: ${egfr} mL/min/1.73m² - Moderat nedsatt nyrefunksjon` });
                    advice.push('Konsulter nefrolog for oppfølging av nyresykdom');
                } else {
                    results.push({ type: 'danger', text: `eGFR: ${egfr} mL/min/1.73m² - Sterkt nedsatt nyrefunksjon` });
                    advice.push('Trenger spesialist oppfølging - alvorlig nyresvikt');
                }
            }

            // ALT (liver enzyme)
            const alt = parseFloat(data.alt);
            if (alt && !isNaN(alt)) {
                if (alt <= 40) {
                    results.push({ type: 'good', text: `ALT: ${alt} U/L - Normal leverfunksjon` });
                } else if (alt <= 80) {
                    results.push({ type: 'warning', text: `ALT: ${alt} U/L - Lett forhøyet` });
                    advice.push('Reduser alkoholinntak og kontroller leverenzymer om 3 måneder');
                } else {
                    results.push({ type: 'danger', text: `ALT: ${alt} U/L - Betydelig forhøyet` });
                    advice.push('Undersøk årsak til leverenzymstigning med lege');
                }
            }
        }

        function analyzeHormonesVitamins(data, results, advice) {
            // TSH (thyroid)
            const tsh = parseFloat(data.tsh);
            if (tsh && !isNaN(tsh)) {
                if (tsh >= 0.27 && tsh <= 4.2) {
                    results.push({ type: 'good', text: `TSH: ${tsh} mIU/L - Normal skjoldbruskkjertelfunksjon` });
                } else if (tsh < 0.27) {
                    results.push({ type: 'warning', text: `TSH: ${tsh} mIU/L - Lavt (mulig hypertyreose)` });
                    advice.push('Undersøk skjoldbruskkjertelen med fT4 og fT3');
                } else {
                    results.push({ type: 'warning', text: `TSH: ${tsh} mIU/L - Høyt (mulig hypotyreose)` });
                    advice.push('Vurder behandling for underaktiv skjoldbruskjertel');
                }
            }

            // Vitamin D
            const vitD = parseFloat(data.vitaminD);
            if (vitD && !isNaN(vitD)) {
                if (vitD >= 30) {
                    results.push({ type: 'good', text: `Vitamin D: ${vitD} ng/mL - Tilstrekkelig` });
                } else if (vitD >= 20) {
                    results.push({ type: 'warning', text: `Vitamin D: ${vitD} ng/mL - Utilstrekkelig` });
                    advice.push('Øk D-vitamintilskudd til 1000-2000 IE daglig');
                } else {
                    results.push({ type: 'danger', text: `Vitamin D: ${vitD} ng/mL - Mangel` });
                    advice.push('Ta høydose D-vitamintilskudd og få mer sollys');
                }
            }

            // B12
            const b12 = parseFloat(data.b12);
            if (b12 && !isNaN(b12)) {
                if (b12 >= 300) {
                    results.push({ type: 'good', text: `Vitamin B12: ${b12} pg/mL - Normalt` });
                } else {
                    results.push({ type: 'warning', text: `Vitamin B12: ${b12} pg/mL - Lavt` });
                    advice.push('Ta B12-tilskudd og spis mer kjøtt, fisk og meieriprodukter');
                }
            }

            // CRP (inflammation)
            const crp = parseFloat(data.crp);
            if (crp && !isNaN(crp)) {
                if (crp < 3.0) {
                    results.push({ type: 'good', text: `CRP: ${crp} mg/L - Lav betennelse` });
                } else if (crp < 10.0) {
                    results.push({ type: 'warning', text: `CRP: ${crp} mg/L - Moderat betennelse` });
                    advice.push('Vurder anti-inflammatorisk kosthold med omega-3');
                } else {
                    results.push({ type: 'danger', text: `CRP: ${crp} mg/L - Høy betennelse` });
                    advice.push('Undersøk årsak til betennelse - kan indikere infeksjon eller sykdom');
                }
            }
        }

        document.getElementById('analyzeBtn').addEventListener('click', function() {
            const formData = {
                // Cardiovascular
                totalCholesterol: document.getElementById('totalCholesterol').value,
                ldlCholesterol: document.getElementById('ldlCholesterol').value,
                hdlCholesterol: document.getElementById('hdlCholesterol').value,
                triglycerides: document.getElementById('triglycerides').value,
                bloodPressureSystolic: document.getElementById('bloodPressureSystolic').value,
                bloodPressureDiastolic: document.getElementById('bloodPressureDiastolic').value,
                
                // Blood status
                hemoglobin: document.getElementById('hemoglobin').value,
                hematocrit: document.getElementById('hematocrit').value,
                wbc: document.getElementById('wbc').value,
                platelets: document.getElementById('platelets').value,
                ferritin: document.getElementById('ferritin').value,
                ironSaturation: document.getElementById('ironSaturation').value,
                
                // Diabetes
                hba1c: document.getElementById('hba1c').value,
                bloodSugar: document.getElementById('bloodSugar').value,
                
                // Kidney & Liver
                creatinine: document.getElementById('creatinine').value,
                egfr: document.getElementById('egfr').value,
                alt: document.getElementById('alt').value,
                ast: document.getElementById('ast').value,
                
                // Hormones & Vitamins
                tsh: document.getElementById('tsh').value,
                vitaminD: document.getElementById('vitaminD').value,
                b12: document.getElementById('b12').value,
                crp: document.getElementById('crp').value
            };

            const analysis = analyzeHealth(formData);
            displayResults(analysis);
        });

        function displayResults(analysis) {
            const resultsDiv = document.getElementById('results');
            const statusContainer = document.getElementById('statusContainer');
            const adviceContainer = document.getElementById('adviceContainer');

            // Show results
            statusContainer.innerHTML = '';
            if (analysis.results && analysis.results.length > 0) {
                analysis.results.forEach(result => {
                    const statusDiv = document.createElement('div');
                    statusDiv.className = `health-status status-${result.type}`;
                    statusDiv.textContent = result.text;
                    statusContainer.appendChild(statusDiv);
                });
            }

            // Show advice
            if (analysis.advice && analysis.advice.length > 0) {
                adviceContainer.innerHTML = `
                    <div class="advice-section">
                        <div class="advice-title">💡 Personlige helseråd</div>
                        <ul class="advice-list">
                            ${analysis.advice.map(tip => `<li>${tip}</li>`).join('')}
                        </ul>
                    </div>
                    <div class="disclaimer">
                        ⚠️ <strong>Viktig:</strong> Denne informasjonen er kun til informasjonsformål og erstatter ikke profesjonell medisinsk rådgivning. 
                        Konsulter alltid en kvalifisert helsepersonell for personlige helseråd og behandling.
                    </div>
                `;
            }

            resultsDiv.style.display = 'block';
            resultsDiv.scrollIntoView({ behavior: 'smooth' });
        }

        // Add loading animations
        document.addEventListener('DOMContentLoaded', function() {
            const formSections = document.querySelectorAll('.form-section');
            formSections.forEach((section, index) => {
                section.style.opacity = '0';
                section.style.transform = 'translateY(20px)';
                setTimeout(() => {
                    section.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
                    section.style.opacity = '1';
                    section.style.transform = 'translateY(0)';
                }, index * 200);
            });
        });
    </script>

</body></html>
