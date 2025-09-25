<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CampusWell - Student Health Platform</title>
    <style>
        :root {
            --primary: #1976d2;
            --primary-dark: #1565c0;
            --secondary: #26a69a;
            --accent: #ff7043;
            --background: #fafafa;
            --surface: #ffffff;
            --text-primary: #212121;
            --text-secondary: #757575;
            --error: #d32f2f;
            --success: #388e3c;
            --warning: #f57c00;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: var(--background);
            color: var(--text-primary);
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        header {
            background: var(--primary);
            color: white;
            padding: 1rem 0;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: bold;
        }

        nav ul {
            list-style: none;
            display: flex;
            gap: 2rem;
        }

        nav a {
            color: white;
            text-decoration: none;
            padding: 0.5rem 1rem;
            border-radius: 4px;
            transition: background 0.3s;
        }

        nav a:hover {
            background: var(--primary-dark);
        }

        nav a.active {
            background: var(--secondary);
        }

        .main-content {
            padding: 2rem 0;
            min-height: 70vh;
        }

        .section {
            background: var(--surface);
            padding: 2rem;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
            margin-bottom: 2rem;
        }

        .hidden {
            display: none;
        }

        h2 {
            color: var(--primary);
            margin-bottom: 1rem;
        }

        h3 {
            color: var(--secondary);
            margin-bottom: 1rem;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        label {
            display: block;
            margin-bottom: 0.5rem;
            color: var(--text-primary);
            font-weight: 500;
        }

        input, select, textarea {
            width: 100%;
            padding: 0.75rem;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 1rem;
        }

        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 2px rgba(25, 118, 210, 0.2);
        }

        button {
            background: var(--primary);
            color: white;
            border: none;
            padding: 0.75rem 1.5rem;
            border-radius: 4px;
            cursor: pointer;
            font-size: 1rem;
            transition: background 0.3s;
        }

        button:hover {
            background: var(--primary-dark);
        }

        button.secondary {
            background: var(--secondary);
        }

        button.secondary:hover {
            background: #1e887e;
        }

        button.accent {
            background: var(--accent);
        }

        button.accent:hover {
            background: #f4511e;
        }

        .card {
            background: var(--surface);
            padding: 1.5rem;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
            margin-bottom: 1rem;
        }

        .health-score {
            text-align: center;
            padding: 2rem;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            border-radius: 8px;
            margin: 2rem 0;
        }

        .score-value {
            font-size: 3rem;
            font-weight: bold;
            margin: 0.5rem 0;
        }

        .score-label {
            font-size: 1.2rem;
            opacity: 0.9;
        }

        .bmi-result {
            padding: 1.5rem;
            border-left: 4px solid var(--primary);
            background: #e3f2fd;
            margin: 1rem 0;
        }

        .risk-info {
            background: #fff3e0;
            padding: 1rem;
            border-radius: 4px;
            margin: 1rem 0;
            border-left: 4px solid var(--warning);
        }

        .success-info {
            background: #e8f5e8;
            padding: 1rem;
            border-radius: 4px;
            margin: 1rem 0;
            border-left: 4px solid var(--success);
        }

        .emergency-button {
            background: var(--error);
            color: white;
            padding: 1rem 2rem;
            border-radius: 8px;
            text-align: center;
            margin: 1rem 0;
            cursor: pointer;
            font-weight: bold;
        }

        .emergency-button:hover {
            background: #c62828;
        }

        .breathing-animation {
            width: 100px;
            height: 100px;
            background: var(--secondary);
            border-radius: 50%;
            margin: 2rem auto;
            animation: breathe 8s infinite ease-in-out;
        }

        @keyframes breathe {
            0%, 100% { transform: scale(0.8); opacity: 0.7; }
            50% { transform: scale(1.2); opacity: 1; }
        }

        footer {
            background: var(--primary);
            color: white;
            text-align: center;
            padding: 2rem 0;
            margin-top: 4rem;
        }

        @media (max-width: 768px) {
            nav ul {
                flex-direction: column;
                gap: 0.5rem;
            }
            
            .header-content {
                flex-direction: column;
                text-align: center;
            }
            
            .section {
                padding: 1rem;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <div class="header-content">
                <div class="logo">CampusWell</div>
                <nav>
                    <ul>
                        <li><a href="#" class="active" onclick="showSection('dashboard')">Dashboard</a></li>
                        <li><a href="#" onclick="showSection('mental')">Mental Health</a></li>
                        <li><a href="#" onclick="showSection('physical')">Physical Health</a></li>
                        <li><a href="#" onclick="showSection('disease')">Disease Awareness</a></li>
                    </ul>
                </nav>
            </div>
        </div>
    </header>

    <div class="container">
        <main class="main-content">
            <!-- Dashboard Section -->
            <section id="dashboard" class="section">
                <h2>Student Health Dashboard</h2>
                
                <div class="health-score">
                    <div class="score-label">Your Health Score</div>
                    <div class="score-value" id="healthScore">85</div>
                    <div class="score-label">Keep up the good work!</div>
                </div>

                <div class="card">
                    <h3>Recent Check-ins</h3>
                    <div id="recentCheckins">
                        <p>No recent check-ins yet. Start tracking your health!</p>
                    </div>
                </div>

                <div class="card">
                    <h3>Quick Actions</h3>
                    <button onclick="showSection('mental')" class="secondary">Mood Check-in</button>
                    <button onclick="showSection('physical')" class="secondary">BMI Calculator</button>
                    <button onclick="showSection('disease')" class="secondary">Symptom Checker</button>
                </div>
            </section>

            <!-- Mental Health Section -->
            <section id="mental" class="section hidden">
                <h2>Mental Wellness Support</h2>
                
                <div class="card">
                    <h3>Daily Mood Check-in</h3>
                    <div class="form-group">
                        <label>How are you feeling today?</label>
                        <select id="moodLevel">
                            <option value="5">😊 Great</option>
                            <option value="4">🙂 Good</option>
                            <option value="3">😐 Okay</option>
                            <option value="2">😕 Stressed</option>
                            <option value="1">😔 Difficult</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label>Any specific concerns?</label>
                        <textarea id="moodNotes" placeholder="Share what's on your mind..."></textarea>
                    </div>
                    <button onclick="saveMoodCheckin()">Save Check-in</button>
                </div>

                <div class="card">
                    <h3>Stress Relief Techniques</h3>
                    <div class="breathing-animation"></div>
                    <p><strong>4-7-8 Breathing Exercise:</strong> Inhale for 4 seconds, hold for 7 seconds, exhale for 8 seconds. Repeat 4 times.</p>
                    <button onclick="startBreathingGuide()">Start Guided Breathing</button>
                </div>

                <div class="card">
                    <h3>Mental Health Resources</h3>
                    <p><strong>Campus Counseling:</strong> Available Mon-Fri 9AM-5PM</p>
                    <p><strong>Crisis Hotline:</strong> 988 (Available 24/7)</p>
                    <p><strong>Wellness Tips:</strong> Regular exercise, adequate sleep, and social connections support mental health</p>
                </div>
            </section>

            <!-- Physical Health Section -->
            <section id="physical" class="section hidden">
                <h2>Physical Health Monitoring</h2>
                
                <div class="card">
                    <h3>BMI Calculator</h3>
                    <div class="form-group">
                        <label>Age</label>
                        <input type="number" id="bmiAge" min="18" max="30" placeholder="Your age">
                    </div>
                    <div class="form-group">
                        <label>Gender</label>
                        <select id="bmiGender">
                            <option value="male">Male</option>
                            <option value="female">Female</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label>Weight (kg)</label>
                        <input type="number" id="bmiWeight" step="0.1" placeholder="Weight in kilograms">
                    </div>
                    <div class="form-group">
                        <label>Height (cm)</label>
                        <input type="number" id="bmiHeight" placeholder="Height in centimeters">
                    </div>
                    <button onclick="calculateBMI()">Calculate BMI</button>
                    
                    <div id="bmiResult" class="hidden">
                        <div class="bmi-result">
                            <h3>Your BMI: <span id="bmiValue"></span></h3>
                            <p>Category: <span id="bmiCategory"></span></p>
                        </div>
                        <div id="bmiImplications"></div>
                    </div>
                </div>

                <div class="card">
                    <h3>Symptom Tracker</h3>
                    <div class="form-group">
                        <label>Report Symptoms</label>
                        <select id="symptomType">
                            <option value="headache">Headache</option>
                            <option value="fatigue">Fatigue</option>
                            <option value="fever">Fever</option>
                            <option value="cough">Cough</option>
                            <option value="other">Other</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label>Notes</label>
                        <textarea id="symptomNotes" placeholder="Describe your symptoms..."></textarea>
                    </div>
                    <button onclick="logSymptom()">Log Symptom</button>
                </div>

                <div class="emergency-button" onclick="handleEmergency()">
                    🚨 Emergency Medical Alert
                </div>
            </section>

            <!-- Disease Awareness Section -->
            <section id="disease" class="section hidden">
                <h2>Disease Awareness & Prevention</h2>
                
                <div class="card">
                    <h3>Symptom Checker</h3>
                    <p>Select symptoms you're experiencing:</p>
                    <div class="form-group">
                        <label><input type="checkbox" value="fever"> Fever (≥38°C)</label>
                        <label><input type="checkbox" value="cough"> Persistent cough</label>
                        <label><input type="checkbox" value="fatigue"> Severe fatigue</label>
                        <label><input type="checkbox" value="breathing"> Difficulty breathing</label>
                        <label><input type="checkbox" value="headache"> Severe headache</label>
                    </div>
                    <button onclick="checkSymptoms()">Analyze Symptoms</button>
                    <div id="symptomAnalysis" class="hidden">
                        <div class="risk-info">
                            <h4>Recommendation</h4>
                            <p id="symptomRecommendation"></p>
                        </div>
                    </div>
                </div>

                <div class="card">
                    <h3>Vaccination Reminders</h3>
                    <div class="form-group">
                        <label>Last flu vaccination date</label>
                        <input type="date" id="lastVaxDate">
                    </div>
                    <div class="form-group">
                        <label>Set reminder for next vaccination</label>
                        <input type="date" id="nextVaxDate">
                    </div>
                    <button onclick="setVaccinationReminder()">Set Reminder</button>
                </div>

                <div class="card">
                    <h3>Prevention Guidelines</h3>
                    <div class="success-info">
                        <h4>🦠 Flu Prevention</h4>
                        <ul>
                            <li>Get annual flu vaccination</li>
                            <li>Wash hands frequently with soap</li>
                            <li>Avoid touching face with unwashed hands</li>
                            <li>Stay home when sick</li>
                        </ul>
                    </div>
                    
                    <div class="success-info">
                        <h4>❤️ Heart Health</h4>
                        <ul>
                            <li>30 minutes of daily exercise</li>
                            <li>Eat balanced diet with fruits/vegetables</li>
                            <li>Limit processed foods and sugars</li>
                            <li>Manage stress through relaxation techniques</li>
                        </ul>
                    </div>
                </div>
            </section>
        </main>
    </div>

    <footer>
        <div class="container">
            <p>CampusWell - Student Health Platform | Confidential and Secure | Not a substitute for professional medical advice</p>
            <p>If you're experiencing a medical emergency, please call 911 or your local emergency number</p>
        </div>
    </footer>

    <script>
        // Navigation
        function showSection(sectionId) {
            // Hide all sections
            document.querySelectorAll('.section').forEach(section => {
                section.classList.add('hidden');
            });
            
            // Show selected section
            document.getElementById(sectionId).classList.remove('hidden');
            
            // Update active nav link
            document.querySelectorAll('nav a').forEach(link => {
                link.classList.remove('active');
            });
            event.target.classList.add('active');
        }

        // Health Score Calculation
        function calculateHealthScore() {
            // Simplified health score based on recent check-ins
            const recentMood = localStorage.getItem('lastMood') || 3;
            const recentBMI = localStorage.getItem('lastBMI') || 22;
            
            let score = 80; // Base score
            
            // Adjust based on mood (1-5 scale, 5 is best)
            score += (recentMood - 3) * 5;
            
            // Adjust based on BMI (18.5-24.9 is ideal)
            if (recentBMI < 18.5 || recentBMI > 24.9) {
                score -= 10;
            } else if (recentBMI >= 18.5 && recentBMI <= 24.9) {
                score += 5;
            }
            
            document.getElementById('healthScore').textContent = Math.max(0, Math.min(100, score));
        }

        // Mental Health Functions
        function saveMoodCheckin() {
            const moodLevel = document.getElementById('moodLevel').value;
            const moodNotes = document.getElementById('moodNotes').value;
            
            localStorage.setItem('lastMood', moodLevel);
            localStorage.setItem('lastMoodNotes', moodNotes);
            localStorage.setItem('lastCheckin', new Date().toISOString());
            
            alert('Mood check-in saved! Your wellness is important.');
            calculateHealthScore();
        }

        function startBreathingGuide() {
            alert('Starting breathing exercise... Inhale slowly for 4 seconds... (Guide would continue with timed prompts)');
        }

        // BMI Calculator with Medical Accuracy
        function calculateBMI() {
            const age = parseInt(document.getElementById('bmiAge').value);
            const gender = document.getElementById('bmiGender').value;
            const weight = parseFloat(document.getElementById('bmiWeight').value);
            const height = parseFloat(document.getElementById('bmiHeight').value) / 100; // Convert cm to m
            
            if (!age || !weight || !height) {
                alert('Please fill in all fields');
                return;
            }
            
            const bmi = weight / (height * height);
            const category = getBMICategory(bmi);
            const implications = getBMIImplications(bmi, age, gender);
            
            document.getElementById('bmiValue').textContent = bmi.toFixed(1);
            document.getElementById('bmiCategory').textContent = category;
            document.getElementById('bmiImplications').innerHTML = implications;
            document.getElementById('bmiResult').classList.remove('hidden');
            
            localStorage.setItem('lastBMI', bmi);
            calculateHealthScore();
        }

        function getBMICategory(bmi) {
            if (bmi < 18.5) return 'Underweight';
            if (bmi < 24.9) return 'Normal weight';
            if (bmi < 29.9) return 'Overweight';
            return 'Obesity';
        }

        function getBMIImplications(bmi, age, gender) {
            const category = getBMICategory(bmi);
            let implications = '';
            
            switch(category) {
                case 'Underweight':
                    implications = `
                        <div class="risk-info">
                            <h4>Health Considerations</h4>
                            <p>Being underweight can indicate:</p>
                            <ul>
                                <li>Nutritional deficiencies</li>
                                <li>Weakened immune system</li>
                                <li>Increased risk of osteoporosis</li>
                                <li>Potential fertility issues</li>
                            </ul>
                            <p><strong>Recommendation:</strong> Consult with healthcare provider about healthy weight gain strategies.</p>
                        </div>
                    `;
                    break;
                    
                case 'Normal weight':
                    implications = `
                        <div class="success-info">
                            <h4>Excellent Health Status</h4>
                            <p>Maintaining a healthy weight reduces risk of:</p>
                            <ul>
                                <li>Heart disease</li>
                                <li>Type 2 diabetes</li>
                                <li>Certain cancers</li>
                                <li>Joint problems</li>
                            </ul>
                            <p><strong>Keep it up:</strong> Continue balanced diet and regular exercise.</p>
                        </div>
                    `;
                    break;
                    
                case 'Overweight':
                    implications = `
                        <div class="risk-info">
                            <h4>Health Considerations</h4>
                            <p>Overweight status increases risk of:</p>
                            <ul>
                                <li>High blood pressure (2-3x higher risk)</li>
                                <li>Type 2 diabetes (3-7x higher risk)</li>
                                <li>Heart disease (1.5-2x higher risk)</li>
                                <li>Sleep apnea and breathing problems</li>
                            </ul>
                            <p><strong>Recommendation:</strong> Gradual weight loss through diet and exercise can significantly reduce these risks.</p>
                        </div>
                    `;
                    break;
                    
                case 'Obesity':
                    implications = `
                        <div class="risk-info">
                            <h4>Significant Health Risks</h4>
                            <p>Obesity substantially increases risk of:</p>
                            <ul>
                                <li>Severe heart disease (2-4x higher risk)</li>
                                <li>Stroke (2x higher risk)</li>
                                <li>Type 2 diabetes (10-20x higher risk)</li>
                                <li>Certain cancers (1.5-3x higher risk)</li>
                                <li>Reduced life expectancy</li>
                            </ul>
                            <p><strong>Urgent Recommendation:</strong> Consult healthcare provider for comprehensive weight management plan.</p>
                        </div>
                    `;
                    break;
            }
            
            return implications;
        }

        // Symptom Tracking
        function logSymptom() {
            const symptomType = document.getElementById('symptomType').value;
            const symptomNotes = document.getElementById('symptomNotes').value;
            
            const symptoms = JSON.parse(localStorage.getItem('symptoms') || '[]');
            symptoms.push({
                type: symptomType,
                notes: symptomNotes,
                date: new Date().toISOString()
            });
            
            localStorage.setItem('symptoms', JSON.stringify(symptoms));
            alert('Symptom logged successfully');
        }

        function handleEmergency() {
            if (confirm('This is for emergency situations only. Are you experiencing a medical emergency?')) {
                alert('Please call 911 or your local emergency number immediately.\n\nCampus security: [Campus-specific number]\nStudent health services: [Campus-specific number]');
            }
        }

        // Disease Awareness
        function checkSymptoms() {
            const selectedSymptoms = Array.from(document.querySelectorAll('input[type="checkbox"]:checked'))
                .map(checkbox => checkbox.value);
            
            let recommendation = '';
            
            if (selectedSymptoms.includes('fever') && selectedSymptoms.includes('cough')) {
                recommendation = 'You appear to have flu-like symptoms. Please:\n- Rest and hydrate\n- Monitor temperature\n- Consider contacting student health services if symptoms worsen\n- Avoid contact with others to prevent spread';
            } else if (selectedSymptoms.includes('breathing')) {
                recommendation = 'Difficulty breathing requires immediate attention. Please seek medical care promptly.';
            } else if (selectedSymptoms.length > 0) {
                recommendation = 'Your symptoms suggest mild illness. Rest, hydrate, and monitor. Contact healthcare if symptoms persist beyond 3 days.';
            } else {
                recommendation = 'No significant symptoms selected. Continue preventive measures like hand washing and vaccination.';
            }
            
            document.getElementById('symptomRecommendation').textContent = recommendation;
            document.getElementById('symptomAnalysis').classList.remove('hidden');
        }

        function setVaccinationReminder() {
            const nextVaxDate = document.getElementById('nextVaxDate').value;
            if (nextVaxDate) {
                localStorage.setItem('nextVaccination', nextVaxDate);
                alert('Vaccination reminder set! Recommended: Annual flu vaccine for all students.');
            }
        }

        // Initialize
        document.addEventListener('DOMContentLoaded', function() {
            calculateHealthScore();
            // Load any saved data
            const lastCheckin = localStorage.getItem('lastCheckin');
            if (lastCheckin) {
                document.getElementById('recentCheckins').innerHTML = `
                    <p>Last check-in: ${new Date(lastCheckin).toLocaleDateString()}</p>
                    <p>Mood level: ${localStorage.getItem('lastMood')}/5</p>
                `;
            }
        });
    </script>
</body>
</html>
