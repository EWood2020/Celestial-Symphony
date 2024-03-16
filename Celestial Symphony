function setup() {
  createCanvas(1920, 1080);
  noLoop(); // Disable continuous drawing
}

function draw() {
  background(0); // Black background for deep space effect
  let matrixSize = 10; // Defines the size of the matrix
  let spacingX = width / matrixSize; // Horizontal spacing between fractals
  let spacingY = height / matrixSize; // Vertical spacing between fractals

  // Determine the size and depth of the fractals
  let len = 50; // Length of the initial branch
  let depth = 7; // Depth of recursion
  let branches = 4; // Number of branches per split

  // Loop through the matrix positions
  for (let i = 0; i < matrixSize; i++) {
    for (let j = 0; j < matrixSize; j++) {
      // Calculate the position for each fractal
      let x = (i + 0.5) * spacingX; // Center in the cell
      let y = (j + 0.5) * spacingY; // Center in the cell

      // Draw each fractal without rotation
      push(); // Isolates the drawing settings for each fractal
      translate(x, y); // Moves the origin to the fractal's calculated location
      drawComplexFractal(0, 0, len, -PI / 2, depth, branches); // Keep the vertical axis unrotated
      pop(); // Restores previous drawing settings
    }
  }
}

function drawComplexFractal(x, y, len, angle, depth, branches) {
  if (depth == 0) {
    return;
  }

  let lenShrink = 0.67; // Length shrink factor per iteration, fixed for uniformity
  let angleOffset = PI / 6; // Angle variation between branches, fixed for a consistent look

  for (let i = 0; i < branches; i++) {
    let newAngle = angle + random(-angleOffset, angleOffset);
    let newLen = len * lenShrink;
    let newX = x + cos(newAngle) * newLen;
    let newY = y + sin(newAngle) * newLen;

    let col = lerpColor(color(255, 100, 0, 150), color(0, 100, 255, 150), depth / 10);
    stroke(col);
    strokeWeight(depth); 
    line(x, y, newX, newY);

    drawComplexFractal(newX, newY, newLen * lenShrink, newAngle, depth - 1, branches);
  }
}
