Author: Jawad Farooq Naik
Date: Sunday, Nov 3, 2024
Location: Boston, MA, USA
Project: Matrix Digital Rain in Processing
Class: Elements of Media
Professor: Prof. Fred Wolflink
University: Massachusetts College of Art & Design
Department: DMI Dynamic Media Institute 

Description
This Processing sketch creates a visual effect similar to the iconic "Matrix" code rain, using a webcam feed to generate a matrix of "1"s and "0"s that react to the brightness of each pixel. The "Matrix Effect" captures live video from a webcam, processes it into blocks, and displays the binary numbers in a monospaced font, where the appearance of "1" or "0" is based on the brightness of each section of the video.
The effect is achieved by dividing the video into 20x20 pixel blocks, analyzing the brightness of each block, and displaying either "1" or "0" in a green font to mimic the famous green code look.
To run this sketch, ensure you have the Video Library installed in Processing.

Setup Instructions
	1.	Install Processing 4: Ensure that Processing 4 is installed on your computer. Download it from Processing.org.
	2.	Enable the Video Library:
	◦	Go to Sketch > Import Library > Add Library…
	◦	Search for "Video" and click "Install" to add the Video Library to your Processing environment.
	3.	Run the Sketch:
	◦	Once the library is installed, connect your webcam, and run the sketch by clicking the Run button in Processing.

 
Code Overview
 
Importing the Video Library
 
import processing.video.*;
The Processing Video library allows the sketch to access and manipulate video input from the webcam.
Variable Definitions
Capture video;  // Defines the webcam video capture object
PFont font;     // Defines the font for the text display
	•	Capture: This object is responsible for capturing frames from the webcam in real-time.
	•	PFont: This object sets the font to a monospaced style, giving the output a retro "matrix" look.
 
setup() Function
 
void setup() {  
size(640, 480);                 // Sets the window size to match webcam dimensions
  frameRate(30);                  // Sets frame rate to 30 FPS
  video = new Capture(this, width, height); // Initializes video capture at the window dimensions
  video.start();                  // Starts the video stream
  font = createFont("Courier", 16);  // Sets up the font
  textFont(font);                 // Applies the font to the text output
  textSize(16);                   // Sets the text size for readability
}
	•	size(640, 480): Sets the window size to match the resolution of the webcam input, which may vary depending on your camera.
	•	frameRate(30): Sets a frame rate of 30 FPS, ensuring smooth video processing.
	•	video = new Capture(...): Instantiates the Capture object with dimensions matching the window size.
	•	video.start(): Begins capturing video from the default webcam.
	•	createFont(): Creates a monospaced "Courier" font with a size of 16 pixels for a digital look.
	•	textFont() and textSize(): Apply the font and size to the text display for uniformity.
 
draw() Function
 
void draw() {
  if (video.available()) {
    video.read();
    video.loadPixels();
    
    background(0);
    fill(0, 255, 0);  // Sets the color to "Matrix" green
 
    // Loop over every block of 20x20 pixels in the video
    for (int x = 0; x < video.width; x += 20) {
      for (int y = 0; y < video.height; y += 20) {
        int index = x + y * video.width;       // Index for pixel array
        float bright = brightness(video.pixels[index]);  // Brightness value at pixel
       
        // Displays "1" or "0" based on brightness threshold
        text(bright > 128 ? "1" : "0", x, y); 
      }
    }
  }
}
	•	video.available(): Checks if a new frame is available from the video feed.
	•	video.read(): Loads the new frame into the video object.
	•	video.loadPixels(): Updates the array of pixel values for processing.
	•	background(0): Clears the screen with a black background, creating contrast.
	•	fill(0, 255, 0): Sets the fill color to green, mimicking the Matrix's iconic aesthetic.
 
Nested Loops for Pixel Blocks
The nested for loops divide the video into 20x20 pixel blocks, determining the "1" or "0" to display based on brightness:
	•	for (int x = 0; x < video.width; x += 20) and for (int y = 0; y < video.height; y += 20):
	◦	These loops move in steps of 20, creating blocks that represent sections of the video input.
	◦	x and y specify the coordinates of each text block.
	•	Brightness Calculation:
	◦	int index = x + y * video.width: Calculates the position in the pixels[] array.
	◦	float bright = brightness(video.pixels[index]): Gets the brightness of the pixel at the specified index.
	•	Conditional Text Display:
	◦	text(bright > 128 ? "1" : "0", x, y);: Displays "1" if brightness is above the threshold of 128, otherwise "0".

 
Customization Options
 
	1.	Change Block Size: Adjust the size of each block in the loops. Smaller values create a denser effect (e.g., 10x10), while larger ones give a more spaced-out look.
 
for (int x = 0; x < video.width; x += 10) { ... }
for (int y = 0; y < video.height; y += 10) { ... }
 
	2.	Adjust Brightness Threshold: Modify the brightness threshold (128) to create different effects depending on lighting or visual preference. Lower values may show more "1"s in dimmer light.
 
text(bright > 100 ? "1" : "0", x, y); // Lower threshold for dimmer effect
 
 
	3.	Text Size & Color: Customize the text size or color to alter the effect’s appearance.
textSize(12); // Smaller text for denser appearance
fill(0, 255, 128); // Lighter green for a different shade
 
 
	4.	Switch Characters: Use different symbols (e.g., "#" and ".") to experiment with alternative looks.
text(bright > 128 ? "#" : ".", x, y); // Symbol-based effect

Acknowledgments
This sketch is part of an exploration in the Processing for the Elements of Media class at MassArt. Special thanks to Prof. Fred Wolflink for guiding the project and inspiring me to experiment with visual media.

Feel free to experiment with the customization options to create unique effects! This sketch serves as a foundation to explore how real-time video can be transformed into digital art inspired by classic sci-fi visuals.
 
