//Processing Sketch code by: Jawad Farooq Naik
//Date: Sunday, Nov 3 2024
//Location: Boston, MA, USA 
//Project: Matrix Digital Rain Effect Via Webcam.
//Code play for Elements of Media class taught by Prof. Fred Wolflink @MassArt
//While exploring Processing and experimenting with its capabilities, I created a sketch that replicates the iconic "01" matrix effect. 
//01 is a binary code represents text, computer processor instructions, or any other data using a two-symbol system.
//For this sketch to work you need to enable the video library inside processing by going to:
//Steps: Sketch, Import Library, Manage Libraries, search video and enable video library for processing 4
//Copy this code in processing sketch to work on it!
  
import processing.video.*; //Enabling Library for video input

Capture video; // Processing will capture video from camera 
PFont font; //Defining camera hardware

void setup() {
  size(640, 480);
  frameRate(30);
  video = new Capture(this, width, height);
  video.start();
  font = createFont("Courier", 16);  // Using a monospaced font
  textFont(font);
  textSize(16);
}

void draw() {
  if (video.available()) {
    video.read();
    video.loadPixels();

    background(0);

    // Loop over every block of 20x20 pixels in the video
    for (int x = 0; x < video.width; x += 20) {
      for (int y = 0; y < video.height; y += 20) {
        int index = x + y * video.width;
        float bright = brightness(video.pixels[index]); // Get brightness
        fill(0, 255, 0); // Matrix green color

        if (bright > 128) {
          text("1", x, y);
        } else {
          text("0", x, y);
        }
      }
    }
  }
}
