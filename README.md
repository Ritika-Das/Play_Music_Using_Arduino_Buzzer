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
<H3>Components Required :</H3>

• 1 Arduino Uno R3 (a microcontroller board based on the ATmega328P)<br>
• Arduino Software (open-source IDE) from https://www.arduino.cc/en/Main/Software (Installed Software or Web Editor)<br>
• 1 Piezoelectric Buzzer (preferably 5V rated to be compatible with your Arduino Uno R3)<br>
• 1 kΩ resistor (to reduce noise)<br>
• 3 Jumper Wires (1 Male-to-Female for Arduino pin to buzzer leg, 1 Female-to-Female for resistor to buzzer leg, 1 Male-to-Female for Arduino pin to resistor)<br>

Alternatively, if you want to use a breadboard (highly recommended), your list would be :<br>

• 1 Arduino Uno R3 (a microcontroller board based on the ATmega328P)<br>
• Arduino Software (open-source IDE) from https://www.arduino.cc/en/Main/Software (Installed Software or Web Editor)<br>
• 1 Piezoelectric Buzzer (preferably 5V rated to be compatible with your Arduino Uno R3)<br>
• 1 kΩ resistor (to reduce noise)<br>
• 1 Mini Breadboard<br>
• 2 Jumper Wires (1 Male-to-Male for Arduino pin to buzzer leg's line on breadboard, 1 Male-to-Male for Arduino pin to resistor's line on breadboard)<br><br>

## Extra Applications/Features (Recommended)

• Note Recognizer (Android App) from https://play.google.com/store/apps/details?id=nl.robertloeberdevelopment&hl=en_IN
• Stopwatch feature (Available in the Clock App for most phones) 

## Getting Started

Chances are that you might have come across a project online where the creator is playing music using an Arduino, and brownie points for you if you have even come across the actual code that went into it. Let me debunk it for you here.

### Getting The Notes Right - Sampling
<img src="https://res.cloudinary.com/ritikadas/image/upload/v1596311660/My_Images/ezgif-6-806bb3d9aa80_ylpgpn.gif" align="left" height="200px">First, you want to make up your mind about the song you are planning to make Arduino "sing" for you. As it's your first time, settle on choosing one which has fairly less melodies, but which you really love. Hints - Jingle Bells, Hallelujah, Fur Elise or even Despacito. Something which has tunes really stuck in your head.
Now you need to get down to the musical notes which will give shape to your code. You can do so using the Note Recognizer App (assuming you might have trouble figuring out musical notes instantly). You just need to hum into the microphone piece of your phone or hands-free and voilà! It tells you what each note is called, and you are ready to hold the humming notes for a while and jot the names down. Even a sneeze or a snore has a note, so don't worry. You'll also see a decimal number being displayed upwards along with your note name; it's not needed right now, so we'll visit that later.



### Getting The Note Durations Right - 

<img src="https://res.cloudinary.com/ritikadas/image/upload/v1596314104/My_Images/ezgif-6-2042206637bd_fiyjcy.gif" align="center" height="200px">**Some notes last longer, some notes last shorter.** THIS is the slightly tricky part. Let me give you an example. In the song Despacito, you might notice that the parts DES and PA are longer than the fast CI and TO parts. On average, if you sing it out, DES took 0.27 seconds (270 milliseconds), PA also took 0.27 seconds (270 milliseconds), CI took 0.19 seconds (190 milliseconds) and TO also took 0.19 seconds (190 milliseconds). How did I time these? Using the Stopwatch feature in my phone. You know how the song goes, you have jotted down the notes too; now time each note out and jot down the milliseconds (if you notice a 0M00S.00 format, you'll get something in 0.XY seconds, now multiply that by 1000, there you have your XY0 milliseconds!). We'll be needing all these data in the next section.



## Almost There!



## Takeaways and Possible Quagmire
