# Play_Music_Using_Arduino_Buzzer
## Introduction
Welcome dear reader! 

This will guide you on how to play musical notes of any song on a piezoelectric buzzer, using Arduino Uno R3, a resistor and some connecting wires.
This project can be attempted by complete beginners of Arduino as well as others, so jump into the details!
## Overview
We will be referring to piano notes only (for clarity). You are free to choose any instrument that you are comfortable with, examples - flute, saxophone, guitar, harmonium etc.

An 88-keys piano keyboard has the keys (in order) :

<center><code>A0, A0#, B0, <br>
C1, C1#, D1, D1#, E1, F1, F1#, G1, G1#, A1, A1#, B1, <br>
C2, C2#, D2, D2#, E2, F2, F2#, G2, G2#, A2, A2#, B2, <br>
C3, C3#, D3, D3#, E3, F3, F3#, G3, G3#, A3, A3#, B3, <br>
C4, C4#, D4, D4#, E4, F4, F4#, G4, G4#, A4, A4#, B4, <br>
C5, C5#, D5, D5#, E5, F5, F5#, G5, G5#, A5, A5#, B5, <br>
C6, C6#, D6, D6#, E6, F6, F6#, G6, G6#, A6, A6#, B6, <br>
C7, C7#, D7, D7#, E7, F7, F7#, G7, G7#, A7, A7#, B7, <br>
  C8<br></code></center>

where A0 and C8 are the lowest and highest pitches possible respectively.
You can hear the notes of such a piano at https://pianu.com/ (Click on "Full Piano" and click the keys).
<img src="https://res.cloudinary.com/ritikadas/image/upload/v1596050238/My_Images/Arduino_Notes_bn7u8t.png" align="center">
Piezoelectric buzzers or simply piezo buzzers are used mainly in alarm circuits to serve as a beeping or security alerting device mechanism. You can generally find them at any electronics shop at a price range from ₹20 to ₹70, i.e. 0.27$ to 0.94$. It is tiny (~ 1.2 cm), available in voltage ratings from 3.3V to 12V (5V is most common), and can produce frequencies from about 31 Hz to 65535 Hz. Good for the "20 Hz to 20000 Hz" hearing beings, we aren't missing out much on frequencies!
