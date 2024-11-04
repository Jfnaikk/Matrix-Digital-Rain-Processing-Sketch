Author: Jawad Farooq Naik
Date: Sunday, Nov 3, 2024
Location: Boston, MA, USA 
Project: Matrix Digital Rain in Processing
Class: Elements of Media
Professor: Fred Wolflink 
University: Massachusetts College of Art & Design
Department: DMI Dynamic Media Institute

Description This Processing sketch creates a visual effect similar to
the iconic "Matrix" code rain. The "Matrix Effect" captures live video
from a webcam, processes it into blocks, and displays the binary numbers
in a monospaced font, where the appearance of "1" or "0" is based on the
brightness of each section of the video. The effect is achieved by
dividing the video into 20x20 pixel blocks, analyzing the brightness of
each block, and displaying either "1" or "0" in a green font to mimic
the famous green code look. To run this sketch, ensure you have the
Video Library installed in Processing.

Setup Instructions

1. Install Processing 4. Download it from Processing.org.
2. Enable the Video Library
    Go to Sketch > Import Library > Add Library... Search for "Video"
and
    click "Install" to add the Video Library to your Processing
    environment.

Customization Options

1. Change Block Size: Adjust the size of each block in the loops.
    Smaller values create a denser effect
    (e.g., 10x10), while larger ones give a more spaced-out look.

    Modify these lines:
      for (int x = 0; x < video.width; x += 10) { ... }
      for (int y = 0; y < video.height; y += 10) { ... }

2. Adjust Brightness Threshold: Modify the brightness threshold (128) to
create different effects depending on lighting or visual preference.
Lower values may show more "1"s in dimmer light.

     text(bright > 100 ? "1" : "0", x, y); // Lower threshold = dimmer

3. Text Size & Color: Customize the text size or color to alter the
appearance.

     textSize(12); // Smaller text for denser appearance
     fill(0, 255, 128); // Lighter green for a different shade

4. Switch Characters: Use different symbols (e.g., "#" and ".") to
experiment with alternative looks.

     text(bright > 128 ? "#" : ".", x, y); // Symbol-based effect

Acknowledgments This sketch is part of an exploration in the Processing
for the Elements of Media class at MassArt. Special thanks to Prof. Fred
Wolflink for guiding the project and inspiring me to experiment with
visual media.

Feel free to experiment with the customization options to create unique
effects! This sketch serves as a foundation to explore how real-time
video can be transformed into digital art inspired by classic sci-fi
visuals.
