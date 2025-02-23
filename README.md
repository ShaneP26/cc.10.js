class Product {
  constructor(name, id, price, stock) {
    this.name = name;
    this.id = id;
    this.price = price; 
    this.stock = stock;
  }getDetails() {
    return `Product: ${this.name}, ID: ${this.id}, Price: $${this.price}, Stock: ${this.stock}`;
  }
 updateStock(quantity) {
    this.stock -= quantity;
  }
}const prod1 = new Product("Laptop", 101, 1200, 10);
console.log(prod1.getDetails());

class Order {
  constructor(orderId, product, quantity) {
    this.orderId = orderId;
    this.product = product; // instance of Product class
    this.quantity = quantity;this.product.updateStock(this.quantity);
  }this.product.updateStock(this.quantity);
  }getOrderDetails() {
    const totalPrice = this.product.price * this.quantity;
    return `Order ID: ${this.orderId}, Product: ${this.product.name}, Quantity: ${this.quantity}, Total Price: $${totalPrice}`;
  }
}
const prod1 = new Product("Laptop", 101, 1200, 10);
const order1 = new Order(501, prod1, 2);
console.log(order1.getOrderDetails());

class Inventory {
  constructor() {
    this.products = []; // Array to store Product instances
  }
addProduct(product) {
    this.products.push(product);
  }listProducts() {
    this.products.forEach(product => {
      console.log(product.getDetails());
    });
  }
}const inventory = new Inventory();
const prod1 = new Product("Laptop", 101, 1200, 10);
inventory.addProduct(prod1);
inventory.listProducts();
class Inventory {
  constructor() {
    this.products = []; // Array to store Product instances
    this.orders = []; // Array to store Order instances
  }

   addProduct(product) {
    this.products.push(product);
  }listProducts() {
    this.products.forEach(product => {
      console.log(product.getDetails());
    });
  }placeOrder(orderId, product, quantity) {
    if (product.stock >= quantity) {
      const order = new Order(orderId, product, quantity);
      this.orders.push(order);
    } else {
      console.log("Not enough stock available to place the order.");
    }
  } listOrders() {
    this.orders.forEach(order => {
      console.log(order.getOrderDetails());
    });
  }
}
const inventory = new Inventory();
const prod1 = new Product("Laptop", 101, 1200, 5);
inventory.addProduct(prod1);
class Inventory {
  constructor() {
    this.products = []; // Array to store Product instances
    this.orders = []; // Array to store Order instances
  }addProduct(product) {
    this.products.push(product);
  }listProducts() {
    this.products.forEach(product => {
      console.log(product.getDetails());
    });
  }placeOrder(orderId, product, quantity) {
    if (product.stock >= quantity) {
      const order = new Order(orderId, product, quantity);
      this.orders.push(order);
    } else {
      console.log("Not enough stock available to place the order.");
    }
  }listOrders() {
    this.orders.forEach(order => {
      console.log(order.getOrderDetails());
    });
  }restockProduct(productId, quantity) {
    const product = this.products.find(prod => prod.id === productId);
    if (product) {
      product.stock += quantity;
      console.log(`Product ID: ${productId} restocked by ${quantity} units.`);
    } else {
      console.log("Product not found.");
    }
  }
}const inventory = new Inventory();
const prod1 = new Product("Laptop", 101, 1200, 3);
inventory.addProduct(prod1);
