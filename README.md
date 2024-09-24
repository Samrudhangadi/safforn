const express = require('express');
const app = express();
const port = 3000;

app.use(express.json());

// Sample menu data
let menu = [
  { id: 1, name: 'Cappuccino', price: 3.5 },
  { id: 2, name: 'Espresso', price: 2.5 },
  { id: 3, name: 'Cheese Sandwich', price: 5.0 },
  { id: 4, name: 'Pasta Alfredo', price: 8.5 }
];

// Endpoint to get menu
app.get('/menu', (req, res) => {
  res.json(menu);
});

// Endpoint to add new item to the menu
app.post('/menu', (req, res) => {
  const newItem = req.body;
  menu.push(newItem);
  res.json(menu);
});

// Endpoint to handle orders (basic)
app.post('/order', (req, res) => {
  const orderDetails = req.body;
  // Handle the order logic here (e.g., save it to the database)
  res.json({ message: 'Order received', orderDetails });
});

app.listen(port, () => {
  console.log(`Saffron restaurant app backend running on http://localhost:${port}`);
});
