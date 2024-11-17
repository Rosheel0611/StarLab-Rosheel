# StarLab-Rosheel
# My Code:

let bg
let starFill

// The breathing variables
let irOffset = 0;
let orOffset = 0;

function setup() {
  createCanvas(400, 400);
  changeBGColor();
  starFill = randomColor();
  fill(starFill);
  noStroke();
}

function draw() {
  background(bg);

  // Calculatations of "breathing" radii
  let ir = 40 + 10 * sin(irOffset);
  let or = 90 + 10 * cos(orOffset);

  irOffset += 0.05; 
  orOffset += 0.03; 

 
  drawStar(width / 2, height / 2, 7, ir, or);
}

// The parameterized star-drawing function
function drawStar(mx = width / 2, my = height / 2, numberOfSides = 7, ir = 50, or = 100) {
  let numberOfPoints = numberOfSides * 2;
  let dt = TWO_PI / numberOfPoints;

  beginShape();
  for (let i = 0; i < numberOfPoints; i++) {
    let radius = (i % 2 === 0) ? ir : or;
    let angle = dt * i;
    vertex(mx + radius * cos(angle), my + radius * sin(angle));
  }
  endShape(CLOSE);
}


function randomColor(avenues = true) {
  if (avenues) {
    return color(randomAvenuesColor());
  } else {
    return color(random(255), random(255), random(255));
  }
}

function changeBGColor(avenues = true) {
  bg = randomColor(avenues);
}


// Hex Codes for the Official Avenues Colors
const colors = {
  white: "#ffffff",
  black: "#000000",
  ash: "#B7B09C", 
  ochre: "#D3AE6F",
  indigo: "#3D68B2",
  moss: "#267355",
  pristineBlue: "#44C3D4",
  violet: "#9796C9",
  nimbus: "#CAC3BC",
  pistachio: "#C5D982",
  olive: "#8A916A",
  terracotta: "#C17E60",
  gold: "#F5CD64",
  clay: "#C3411E",
  grass: "#0D9A48",
  navy: "#273879"
};

function randomAvenuesColor() {
  return random(Object.values(colors));
}


function keyPressed() {
  if (key === 'b') {
    changeBGColor(); 
  }
  
      
 
}
