# Play_Music_Using_Arduino_Buzzer
## Introduction
Welcome dear reader! 

This will guide you on how to play musical notes of any song on a piezoelectric buzzer, using Arduino Uno R3, a resistor and some connecting wires.
This project can be attempted by complete beginners of Arduino as well as others, so jump into the details!
## Overview and Prerequisites
We will be referring to piano notes only (for clarity). You are free to choose any instrument that you are comfortable with, examples - flute, saxophone, guitar, harmonium etc.

An 88-keys piano keyboard has the keys (in order) :

<center><code>A0, A0#, B0, </code><br>
<code>C1, C1#, D1, D1#, E1, F1, F1#, G1, G1#, A1, A1#, B1, </code><br>
<code>C2, C2#, D2, D2#, E2, F2, F2#, G2, G2#, A2, A2#, B2, </code><br>
<code>C3, C3#, D3, D3#, E3, F3, F3#, G3, G3#, A3, A3#, B3, </code><br>
<code>C4, C4#, D4, D4#, E4, F4, F4#, G4, G4#, A4, A4#, B4, </code><br>
<code>C5, C5#, D5, D5#, E5, F5, F5#, G5, G5#, A5, A5#, B5, </code><br>
<code>C6, C6#, D6, D6#, E6, F6, F6#, G6, G6#, A6, A6#, B6, </code><br>
<code>C7, C7#, D7, D7#, E7, F7, F7#, G7, G7#, A7, A7#, B7, </code><br>
<code> C8</code><br>
<br></center>
where A0 and C8 are the lowest and highest pitches possible respectively.
You can hear the notes of such a piano at https://pianu.com/ (Click on "Full Piano" and click the keys).<br><br>
<br><img src="https://res.cloudinary.com/ritikadas/image/upload/v1596050238/My_Images/Arduino_Notes_bn7u8t.png" align="center">
<br>Piezoelectric buzzers or simply piezo buzzers are used mainly in alarm circuits to serve as a beeping or security alerting device mechanism. You can generally find them at any electronics shop at a price range from ₹20 to ₹70, i.e. 0.27$ to 0.94$. It is tiny (~ 1.2 cm), available in voltage ratings from 3.3V to 12V (5V is most common), and can produce frequencies from about 31 Hz to 65535 Hz. Good for the "20 Hz to 20000 Hz" hearing beings, we aren't missing out much on frequencies!
<H3>Components/Software Required :</H3>
<a href="#Schematic">Click here to skip to the schematic.</a><br>
• 1 Arduino Uno R3 (a microcontroller board based on the ATmega328P)<br>
• Arduino Software (open-source IDE) from https://www.arduino.cc/en/Main/Software (Installed Software or Web Editor)<br>
• 1 Piezoelectric Buzzer (preferably 5V rated to be compatible with your Arduino Uno R3)<br>
• 1 kΩ resistor (to reduce noise)<br>
• 3 Jumper Wires (1 Male-to-Female for Arduino pin to buzzer leg, 1 Female-to-Female for resistor to buzzer leg, 1 Male-to-Female for Arduino pin to resistor)<br>

<br>Alternatively, if you want to use a breadboard (highly recommended), your list would be :<br>

• 1 Arduino Uno R3 (a microcontroller board based on the ATmega328P)<br>
• Arduino Software (open-source IDE) from https://www.arduino.cc/en/Main/Software (Installed Software or Web Editor)<br>
• 1 Piezoelectric Buzzer (preferably 5V rated to be compatible with your Arduino Uno R3)<br>
• 1 kΩ resistor (to reduce noise)<br>
• 1 Mini Breadboard<br>
• 2 Jumper Wires (1 Male-to-Male for Arduino pin to buzzer leg's line on breadboard, 1 Male-to-Male for Arduino pin to resistor's line on breadboard)<br>

## Extra Applications/Features (Recommended)

• Note Recognizer (Android App) from https://play.google.com/store/apps/details?id=nl.robertloeberdevelopment&hl=en_IN<br>
• Stopwatch feature (Available in the Clock App for most phones) 

## Getting Started

Chances are that you might have come across a project online where the creator is playing music using an Arduino, and brownie points for you if you have even come across the actual code that went into it. Let me debunk it for you here.

### Getting The Notes Right - Sampling
<img src="https://res.cloudinary.com/ritikadas/image/upload/v1596311660/My_Images/ezgif-6-806bb3d9aa80_ylpgpn.gif" align="left" height="200px">First, you want to make up your mind about the song you are planning to make Arduino "sing" for you. As it's your first time, settle on choosing one which has fairly less melodies, but which you really love. Hints - Jingle Bells, Hallelujah, Fur Elise or even Despacito. Something which has tunes really stuck in your head.
Now you need to get down to the musical notes which will give shape to your code. You can do so using the Note Recognizer App (assuming you might have trouble figuring out musical notes instantly). You just need to hum into the microphone piece of your phone or hands-free and voilà! It tells you what each note is called, and you are ready to hold the humming notes for a while and jot the names down. Even a sneeze or a snore has a note, so don't worry. You'll also see a decimal number being displayed upwards along with your note name; it's not needed right now, so we'll visit that later.
To see the GIF clearly, you may <a href="https://camo.githubusercontent.com/59081a946e7ea2d2b16c2b9cd268fe638f4c062c/68747470733a2f2f7265732e636c6f7564696e6172792e636f6d2f726974696b616461732f696d6167652f75706c6f61642f76313539363331313636302f4d795f496d616765732f657a6769662d362d3830366262336439616138305f796c7067706e2e676966">click here</a>.


### Getting The Note Durations Right - Approximation
<img src="https://res.cloudinary.com/ritikadas/image/upload/v1596314104/My_Images/ezgif-6-2042206637bd_fiyjcy.gif" align="left" height="200px">Some notes last longer, some notes last shorter. THIS is the slightly tricky part. Let me give you an example. In the song Despacito, you might notice that the parts DES and PA are longer than the fast CI and TO parts. On average, if you sing it out, DES took 0.27 seconds (270 milliseconds), PA also took 0.27 seconds (270 milliseconds), CI took 0.19 seconds (190 milliseconds) and TO also took 0.19 seconds (190 milliseconds). How did I time these? Using the Stopwatch feature in my phone. You know how the song goes, you have jotted down the notes too; now time each note out and jot down the milliseconds (if you notice a 0M00S.00 format, you'll get something in 0.XY seconds, now multiply that by 1000, there you have your XY0 milliseconds!). We'll be needing all these data in the next section.<br>
To see the GIF clearly, you may <a href="https://camo.githubusercontent.com/42de300b300cee329d1708f3717c2b5d5a825f88/68747470733a2f2f7265732e636c6f7564696e6172792e636f6d2f726974696b616461732f696d6167652f75706c6f61642f76313539363331343130342f4d795f496d616765732f657a6769662d362d3230343232303636333762645f6669796a63792e676966">click here</a>.

## Almost There!
Now it's time to open the file Baianá_by_Bakermat.ino in this repository (or <a href="https://github.com/Ritika-Das/Play_Music_Using_Arduino_Buzzer/blob/master/Baian%C3%A1_by_Bakermat.ino">click here</a> for it!). Wanna have a listen? Here is the <a href="https://www.youtube.com/watch?v=iaGjz4dtr3o">original song</a> that I have butchered (for educational purposes). Superglued my ears to this song!<br>
### Basics
• If we look at lines 10 to 98 - those are the defined notes with frequencies (in Hz). Our Arduino would be connected to a buzzer. A buzzer can't understand code! It is instructed by the microprocessor to play certain frequencies according to our code. Just as humans talk with fundamental frequency from 85 to 180 Hz (average adult male) or from 165 to 255 Hz (average adult female), every musical note is based upon a certain frequency. If you use Arduino IDE to compile your code, you can make it compact by replacing these lines of code with the "pitches.h" library in Arduino <code>#include "pitches.h"</code><br>
<br>• If we look at lines 99 to 119 - we see <code>int melody[]</code>, where melody is an integer array. It consists of all the musical notes we jotted down for our Arduino song. But wait, what are those 0s doing? We didn't jot them down! Well, those are called <code>rest notes</code>. Rest notes are used to denote pauses in between the notes, and indicate the frequency 0 Hz. It might be those parts when you sang the highest note in the climax of the song, then take a few milliseconds of rest to catch up on breath, and proceed to sing the next notes. *Don't add the rest notes (0s) to the melody[] now!* For now, just type in the jotted notes. Remember - <code>A#4</code> from the app is typed as <code>NOTE_AS4</code> and so on.<br>
<br>• If we look at lines 121 to 140 - we see <code>int durations[]</code>, where durations is also an integer array. It consists of the durations of all the musical notes in milliseconds, which we have jotted down as well. Line 122 is <code>400,20, 600,20, 210,20, 210,20, 210,20, 210,20,</code>, which corresponds to the durations for notes in line 101 <code>NOTE_F5,0, NOTE_D5,0, NOTE_A5,0, NOTE_C6,0, NOTE_A5,0, NOTE_D6,0, </code>. See the 20s? Those are the durations for the rest notes. The 400, 600 and the four 210s are the durations of the notes F5, D5, A5, C6, A5, D6 respectively. For now, type in the durations of the notes excluding the rest notes.<br>
### Going Deeper
• Now count the number of elements (entries separated by commas) in each array (melody[] and durations[]) and compare them. Are they same? If yes, great job! If not, check the note/duration you missed while typing. Since notes/melodies and durations correspond to each other, both the arrays must have the same number of elements. When you are done, squeeze in the rest notes (0s) in the melody[] array and add appropriate durations to them while timing them on Stopwatch. If there are no rest notes in your song, mark the corresponding duration with 0 milliseconds in the durations[] array.<br>
<br>• If we look at lines 141 to 147 - we see <code>int songLength = sizeof(melody)/sizeof(melody[0]);</code> on line 141. Here <code>sizeof(melody)</code> denotes the size of the entire melody array of notes, i.e. (integer size) X (total number of notes). ------------(1) On the other hand, <code>sizeof(melody[0])</code> denotes the size of the first note element in the array, i.e. simply (integer size) X (number of notes) = (integer size) X 1 = (integer size). ------------(2) Dividing (1) by (2), we'll get (total number of notes) as the <code>int songLength</code>.<br>In the other lines having <code>void setup()</code>, there's nothing to set up. You may leave it as it is.<br>
<br>• If we look at lines 148 to 156 - we encounter the <code>void loop()</code> portion. This function is used when you want your song to loop (definitely try this one for the song to sound catchy!), that is, play over and over. Line 149 has <code>for (int thisNote = 0; thisNote < songLength; thisNote++)</code>, which ensures that all your notes from the beginning to the endnote are successfully played. Line 151 has <code>tone(8, melody[thisNote], duration);</code>, where the number "8" indicates the Arduino pin that the negative terminal of the buzzer is connected to. This is also found in line 154 as <code>noTone(8);</code>. If you wish to connect the Buzzer to another Arduino pin (i.e. other than 8), make sure to change the number in these two lines.<br>

## Takeaways and Possible Quagmire
<a id="Schematic">The connection can be followed as in this image :</a><br>
<br><a href="https://www.tinkercad.com/things/bhkltIIL1Fd-music-using-piezoelectric-buzzer-and-arduino/editel"><img src="https://res.cloudinary.com/ritikadas/image/upload/v1596320065/My_Images/buzzer_e8bd0b.jpg" alt="Schematic" height="420px" float="center"></a><br><br>• If you wish to virtually simulate this project due to unavailability of components, go ahead and click on the above picture! It'll take you where you'll have the options of <br><nbsp><nbsp>• "Start Simulation" - if you directly want to see what it's like, and <br><nbsp><nbsp>• "Tinker This" - if you want to create a copy for yourself without altering the original project, tweak the code and then start simulation.<br>
<br>• Did you know that the note recognition range for the Note Recognizer App is E2 - G7? That is, no whistle notes.<br>
<br>• If you think that your final Arduino song sounds a bit low on the pitch, just change all the musical notes in <code>int melody[]</code> up one scale : change <code>NOTE_CS4</code> to <code>NOTE_CS5</code>, <code>NOTE_G5</code> to <code>NOTE_G6</code> and so on, keeping the durations same. Trust me, it will automatically sound better! Or maybe close to this : <br><br>
  <img src="https://res.cloudinary.com/ritikadas/image/upload/v1596321690/My_Images/H61c528c8e2e64a8cbc8182c17718b04ba_xi1lan.jpg" align="center" height="200px">
