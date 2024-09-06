<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>MoM with Speech Recognition, Details, Toggling, Email, and Row Management</title>
    <style>

#recordingIndicator {
            width: 100%;
            height: 5px;
            background-color: #e0e0e0;
            position: fixed;
            top: 0;
            left: 0;
            overflow: hidden;
        }
        #recordingIndicator.active::before {
            animation: floatWave 1.5s linear infinite;
        }
        #recordingIndicator::before {
            content: '\'''\'';
            display: block;
            position: absolute;
            width: 100%;
            height: 100%;
            background: repeating-linear-gradient(
                to right,
                #007BFF 0%,
                #e0e0e0 10%,
                #007BFF 20%
            );
            transform: translateX(-100%);
        }
        @keyframes floatWave {
            from { transform: translateX(-100%); }
            to { transform: translateX(0%); }
        }
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            padding: 20px;
            border: 1px solid #ddd;
            width: 80%;
            margin: 0 auto;
        }
        .btn {
            padding: 5px 10px;
            margin: 5px 0;
            color: white;
            background-color: #4CAF50;
            border: none;
            cursor: pointer;
        }
        .delete-btn {
            color: #f44336;
            background-color: transparent;
            border: 1px solid #f44336;
            padding: 5px 10px;
            margin-left: 10px;
            cursor: pointer;
        }
        .transcript-section, .input-section {
            margin-top: 20px;
            border: 1px solid #ccc;
            padding: 10px;
            background-color: #f9f9f9;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 10px;
        }
        th, td {
            border: 1px solid #999;
            padding: 8px;
            text-align: left;
        }
        td[contenteditable="true"], input, textarea {
            background-color: #e9ecef;
            cursor: text;
            width: 95%;
            padding: 5px;
            margin-top: 5px;
            margin-bottom: 5px;
            box-sizing: border-box;
        }
        h3 {
            color: #333;
            cursor: pointer;
        }
        .toggle-btn {
            color: blue;
            text-decoration: underline;
        }
		.delete-btn-cell {
    border: none !important; 
}

    </style>
</head>
<body>
    <h3 class="toggle-btn" onclick="toggleSection('\''raw-transcript'\'')">Raw Transcript:</h3>
    
	<div id="recordingIndicator"></div>
<div id="timer">00:00:00</div>
<ul id="recordingsList"></ul>
    <button id="start-btn" class="btn">Start Listening</button>
    <button id="stop-btn" class="btn">Stop Listening</button>
<div id="raw-transcript" class="transcript-section" style="display: none;"></div>

    <h3 class="toggle-btn" onclick="toggleSection('\''meeting-details'\'')">Meeting Details:</h3>
    <div id="meeting-details" class="input-section" style="display: none;">
        <table >
<tr>
                <th>Agenda</th>
                <td><input type="checkbox" id="hide-controls" style=" text-align:left"/><input type="text" id="meeting-agenda" placeholder="Main topics"></td>
            </tr>
            <tr>
                <th>Date</th>
                <td><input type="date" id="meeting-date"><input type="time" id="meeting-time"></td>
            </tr>
            <tr>
                <th>Attendees</th>
                <td><input type="text" id="meeting-attendees" placeholder="Names"></td>
            </tr>

        </table>
    </div>

    <h3 class="toggle-btn" onclick="toggleSection('\''structured-mom'\'')">Key Decision Points:</h3>
    <div id="structured-mom" class="transcript-section" style="display: none;">
        <table id="key-decision-table">
            <thead>
                <tr>
                    <th>No</th>
                    <th>Details</th>
                </tr>
            </thead>
            <tbody>
            </tbody>
        </table>
        <button id="add-decision-btn" class="btn">Add Key Decision Point</button>
    </div>

    <h3 class="toggle-btn" onclick="toggleSection('\''action-items'\'')">Action Items:</h3>
    <div id="action-items" class="transcript-section" style="display: none;">
        <table id="action-items-table">
            <thead>
                <tr>
                    <th>No</th>
                    <th>Details</th>
                    <th>PIC</th>
                    <th>Target Date</th>
                </tr>
            </thead>
            <tbody>
            </tbody>
        </table>
        <button id="add-action-btn" class="btn">Add Action Item</button>
    </div>

    <button id="send-email-btn" class="btn" onclick="sendEmail()">Send MOM Email</button>

    <script>
        let recognition;
		if (navigator.permissions && navigator.permissions.query) {
    navigator.permissions.query({ name: '\''microphone'\'' })
      .then(function(permissionStatus) {
        if (permissionStatus.state === '\''granted'\'') {
            
            startSpeechRecognition(); 
        } else {
            
        }
    });
}

 if (window.SpeechRecognition || window.webkitSpeechRecognition) {
    const recognition = new (window.SpeechRecognition || window.webkitSpeechRecognition)();
    recognition.lang = '\''en-US'\'';
    recognition.interimResults = false;
    recognition.continuous = true; 

    recognition.onresult = (event) => {
        
        for (let i = event.resultIndex; i < event.results.length; ++i) {
            if (event.results[i].isFinal) {
                const transcript = event.results[i][0].transcript;
                const p = document.createElement('\''p'\'');
                p.textContent = transcript;
                document.getElementById('\''raw-transcript'\'').appendChild(p);
            }
        }
    };

    recognition.onend = () => {
        console.log('\''Speech recognition service disconnected, attempting to restart'\'');
        recognition.start(); 
    };

    document.getElementById('\''start-btn'\'').addEventListener('\''click'\'', () => recognition.start());
    document.getElementById('\''stop-btn'\'').addEventListener('\''click'\'', () => {
        recognition.stop();
        recognition.onend = null; 
    });
} else {
    console.warn('\''Speech recognition not supported in this browser.'\'');
    
}


        document.getElementById('\''start-btn'\'').addEventListener('\''click'\'', () => { recognition.start(); });
        document.getElementById('\''stop-btn'\'').addEventListener('\''click'\'', () => { recognition.stop(); });

       function addRow(tableId) {
    const tableBody = document.getElementById(tableId).querySelector('\''tbody'\'');
    const newRowNumber = tableBody.rows.length + 1; 
    const newRow = tableBody.insertRow();

    let cellCount;
    let detailsCellIndex;

    
    if (tableId === '\''key-decision-table'\'') {
        cellCount = 3; 
        detailsCellIndex = 1; 
    } else if (tableId === '\''action-items-table'\'') {
        cellCount = 5; 
        detailsCellIndex = 3; 
    }

    for (let i = 0; i < cellCount - 1; i++) { 
        const cell = newRow.insertCell(i);
        if (i === 0) { 
            cell.textContent = newRowNumber; 
        } else {
            cell.setAttribute('\''contenteditable'\'', '\''true'\'');
        }
    }

    
    const deleteCell = newRow.insertCell(cellCount - 1);
    const deleteBtn = document.createElement('\''button'\'');
    deleteBtn.textContent = '\''Delete'\'';
    deleteBtn.className = '\''delete-btn'\'';
    deleteBtn.onclick = function() {
        newRow.remove();
    };
    deleteCell.appendChild(deleteBtn);
    
    deleteCell.style.border = '\''none'\'';
}


        document.getElementById('\''add-decision-btn'\'').addEventListener('\''click'\'', function() { addRow('\''key-decision-table'\''); });
        document.getElementById('\''add-action-btn'\'').addEventListener('\''click'\'', function() { addRow('\''action-items-table'\''); });

function sendEmail() {
    const agenda = document.getElementById('\''meeting-agenda'\'').value;
    const date = document.getElementById('\''meeting-date'\'').value;

    let emailBody = `Discussion Points from "${agenda}" held on ${date}.\n\n`;

  
    emailBody += "\nThanks,\nYour Name";

    
    let subject = `MOM - ${agenda} - ${date}`;
    let mailtoLink = `mailto:?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(emailBody)}`;
    window.open(mailtoLink, '\''_blank'\'');
}



document.getElementById('\''hide-controls'\'').addEventListener('\''change'\'', function() {
    const isChecked = this.checked;
    
    document.querySelectorAll('\''#start-btn, #stop-btn, #send-email-btn, #add-decision-btn, #add-action-btn,#recordingIndicator,#timer'\'').forEach(el => {
        el.style.display = isChecked ? '\''none'\'' : '\''inline-block'\'';
    });
    
    document.querySelectorAll('\''.delete-btn'\'').forEach(btn => {
        btn.style.display = isChecked ? '\''none'\'' : '\''inline-block'\'';
    });
    
    document.querySelector('\''.toggle-btn'\'').style.display = isChecked ? '\''none'\'' : '\''block'\'';
    document.getElementById('\''raw-transcript'\'').style.display = isChecked ? '\''none'\'' : '\''block'\'';
});


        function toggleSection(sectionId) {
            const section = document.getElementById(sectionId);
            section.style.display = section.style.display === "none" ? "block" : "none";
        }

document.addEventListener('\''DOMContentLoaded'\'', function() {
    const startBtn = document.getElementById('\''start-btn'\'');
    const stopBtn = document.getElementById('\''stop-btn'\'');
    const recordingsList = document.getElementById('\''recordingsList'\'');
    const recordingIndicator = document.getElementById('\''recordingIndicator'\'');
    const timerDisplay = document.getElementById('\''timer'\'');

    let mediaRecorder;
    let audioChunks = [];
    let startTime, interval;

    function updateTimer() {
        const elapsedTime = Date.now() - startTime;
        const seconds = Math.floor((elapsedTime / 1000) % 60).toString().padStart(2, '\''0'\'');
        const minutes = Math.floor((elapsedTime / (1000 * 60)) % 60).toString().padStart(2, '\''0'\'');
        timerDisplay.textContent = `${minutes}:${seconds}`;
    }

    async function startRecording() {
        recordingIndicator.classList.add('\''active'\'');
        audioChunks = [];
        const stream = await navigator.mediaDevices.getUserMedia({ audio: true });
        mediaRecorder = new MediaRecorder(stream);
        mediaRecorder.start();
        startTime = Date.now();
        interval = setInterval(updateTimer, 1000);

        mediaRecorder.ondataavailable = e => audioChunks.push(e.data);
        mediaRecorder.onstop = () => handleRecordingStopped();

        startBtn.disabled = true;
        stopBtn.disabled = false;
    }

    function stopRecording() {
        mediaRecorder.stop();
        clearInterval(interval);
        timerDisplay.textContent = '\''00:00:00'\'';
        startBtn.disabled = false;
        stopBtn.disabled = true;
    }

    function handleRecordingStopped() {
        recordingIndicator.classList.remove('\''active'\'');
        const audioBlob = new Blob(audioChunks, { type: '\''audio/mp3'\'' });
        const audioUrl = URL.createObjectURL(audioBlob);
        const audioElement = new Audio(audioUrl);
        audioElement.controls = true;
        recordingsList.appendChild(audioElement);
        audioChunks = [];
    }

    startBtn.addEventListener('\''click'\'', startRecording);
    stopBtn.addEventListener('\''click'\'', stopRecording);
});

    </script>
</body>
</body>
  </html>
  
