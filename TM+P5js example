//Rollover mouseY to change size of grid
//Click anywhere to change background
//Roll mouse over the boxes on the left to create gradient
//Cover camera with hand to blank out screen 

var on = true;
let sun;
let moon;
let video;
let flipVideo;
let classifier;
let modelURL = 'https://teachablemachine.withgoogle.com/models/jyvJ7fjry/'
//testing up down left right cover TM
//let modelURL = 'https://teachablemachine.withgoogle.com/models/eO6EUHoha/'
///code not working with new TM
let move;
let label = "Good day/night";
//set bg variable after porting in chalkboard.jpg
let bg;
let bg2;

function preload() {
  sun = loadImage('sun.gif');
  moon = loadImage('moon.gif')
  //loads bg image
  bg = loadImage('chalkboard.jpg')
  bg2 = loadImage('tennis.png')
  classifier = ml5.imageClassifier(modelURL + 'model.json');
}

function setup() {
  createCanvas(720, 480);
  image(sun, 104, 0)
  image(moon, 104, 0)
  video = createCapture(VIDEO);
  video.size(720, 480);
  video.hide();
  flipVideo = ml5.flipImage(video);

  classifyVideo();

}

function classifyVideo() {
  flipVideo = ml5.flipImage(video);
  classifier.classify(flipVideo, gotResults);
}

function draw() {
  textSize(32);
  textAlign(CENTER, CENTER);
  textFont('Georgia');
  fill(255)
  noStroke();

  if (on) {
    background(sun);
    text('Good Afternoon', 360, 50)
  } else {
    background(moon);
    text('Good Night', 360, 50)
  }

  stroke(255);
  strokeWeight(4);
  noFill();

  if (mouseX > 4 && mouseX < 104 && mouseY > 4 && mouseY < 104) {
    fill(255, 0, 0);
  }

  rect(4, 4, 100, 100);

  if (mouseX > 4 && mouseX < 104 && mouseY > 108 && mouseY < 208) {
    fill(255, 69, 0);
  }

  rect(4, 104, 100, 100);

  if (mouseX > 4 && mouseX < 104 && mouseY > 208 && mouseY < 308) {
    fill(255, 99, 71);
  }

  rect(4, 204, 100, 100);

  if (mouseX > 4 && mouseX < 104 && mouseY > 308 && mouseY < 412) {
    fill(255, 127, 80);
  }

  rect(4, 304, 100, 100);

  stroke(0);
  strokeWeight(4);
  noFill();

  sun.loadPixels();
  const stepSize = round(constrain(mouseY / 6, 9, 72));
  for (let y = 0; y < height; y += stepSize) {
    for (let x = 108; x < width; x += stepSize) {
      const i = y * width + x;
      const darkness = (50 - sun.pixels[i * 2]) / 255;
      const radius = stepSize * darkness;
      rect(x, y, width, height);
    }
  }

 if (label === 'Cover') {
    //background(255, 0, 0);
      background(bg);
    //background(bg2);
 } else if (label === 'No Cover') {
    
    //testing other TM
  //} else (label === 'Up'||label ==='Down'|| label ==='Left'|| label ==='Right') {
 // } else if (label === 'Up') {
    
  }
    noFill();
  }


function mousePressed() {
  on = !on
}




function gotResults(error, results) {
  if (error) {
    console.error(error);
    return;
  }
  label = results[0].label;
  classifyVideo();
}
