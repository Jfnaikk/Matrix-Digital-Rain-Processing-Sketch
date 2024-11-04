//In this sketch we changed 1 0 to DMI + . & size of the blocks while demonstrating this inside the class.



import processing.video.*;

Capture video;
PFont font;

void setup() {
  size(640, 480);
  frameRate(30);
  video = new Capture(this, width, height);
  video.start();
  font = createFont("Courier", 16);  // Using a monospaced font
  textFont(font);
  textSize(4);
}

void draw() {
  if (video.available()) {
    video.read();
    video.loadPixels();

    background(0);

    // Loop over every block of 20x20 pixels in the video
    for (int x = 0; x < video.width; x += 5) {
      for (int y = 0; y < video.height; y += 5) {
        int index = x + y * video.width;
        float bright = brightness(video.pixels[index]); // Get brightness
        fill (random (256), 255, 0); // Matrix green color

        if (bright > 128) {
          text("DMI", x, y);
        } else {
          text(".", x, y);
        }
      }
    }
  }
}
