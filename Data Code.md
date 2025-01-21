Sorry, I couldn't find the demo:

Visualization 1:

 let table;

function preload() {
  table = loadTable("data.csv", "csv", "header");
}
function setup() {
  createCanvas(800, 400);
  let x = 50;
  let y = height - 50;
  let data = table.getColumn("mean_temperature");

  beginShape();
  for (let i = 0; i < data.length; i++) {
    let temp = map(data[i], min(data), max(data), height - 100, 50);
    vertex(x + i * 10, temp);
  }
  endShape();
}


