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


Visualization 2:

 let table, data, dropdown;

function preload() {
  table = loadTable("data.csv", "csv", "header");
}

function setup() {
  createCanvas(800, 400);

  dropdown = createSelect();
  dropdown.position(20, 20);
  dropdown.option("January");
  dropdown.option("February");
  dropdown.changed(updateSubset);

  data = getMonthData("January");
  drawBarChart(data);
}

function getMonthData(month) {
  return table.getColumn(month);
}

function updateSubset() {
  let month = dropdown.value();
  data = getMonthData(month);
  redraw();
}

function drawBarChart(data) {
  background(255);
  for (let i = 0; i < data.length; i++) {
    let value = map(data[i], 0, max(data), height - 50, 50);
    rect(i * 20, height - value, 15, value);
  }
}
