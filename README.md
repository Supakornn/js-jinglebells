# 🔔 Jingle Bells

## 📝 Description

This project plays the "Jingle Bells" song using the Web Audio API 🎵

### 🎹 Usage in the Project

In this project, we use AudioContext to generate the notes for the "Jingle Bells" song. Here's how it works:

1. 🎼 Create an AudioContext:
   ```javascript
   const audioContext = new (window.AudioContext || window.webkitAudioContext)();
   ```
2. 🎵 The `playNote` function is used to play a note:

   ```javascript
   const playNote = (frequency, duration = 0.3, startTime = 0) => {
     const oscillator = audioContext.createOscillator();
     const gainNode = audioContext.createGain();

     oscillator.type = "sine";
     oscillator.frequency.setValueAtTime(frequency, startTime);

     oscillator.connect(gainNode);
     gainNode.connect(audioContext.destination);

     gainNode.gain.setValueAtTime(1, startTime);
     gainNode.gain.exponentialRampToValueAtTime(0.001, startTime + duration);

     oscillator.start(startTime);
     oscillator.stop(startTime + duration);
   };
   ```

3. 🎶 Define the frequencies of the notes:
   ```javascript
   const noteFrequencies = {
     C4: 261.63,
     D4: 293.66,
     E4: 329.63,
     F4: 349.23,
     G4: 392.0,
     A4: 440.0,
     B4: 493.88,
     C5: 523.25
   };
   ```
4. 🎄 Sequence of notes in the "Jingle Bells" song:
   ```javascript
   const jingleBells = [
     { note: "E4", duration: 0.3 },
     { note: "E4", duration: 0.3 },
     { note: "E4", duration: 0.6 }
     // ...other notes...
   ];
   ```
