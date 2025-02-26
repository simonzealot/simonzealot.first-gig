import { useState } from 'react';
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";

const products = [
  { id: 1, name: 'Shea Butter Hair Cream', price: 5000, image: '/images/shea-butter.jpg' },
  { id: 2, name: 'Coconut Oil Conditioner', price: 7000, image: '/images/coconut-oil.jpg' },
  { id: 3, name: 'Herbal Hair Growth Oil', price: 8500, image: '/images/herbal-oil.jpg' },
];

export default function ZeazeeNatural() {
  const [cart, setCart] = useState([]);

  const addToCart = (product) => {
    setCart([...cart, product]);
  };

  return (
    <div className="p-6 bg-white min-h-screen">
      <header className="text-center mb-10">
        <h1 className="text-4xl font-bold text-green-600">Zeazee Natural</h1>
        <p className="text-lg mt-2">Made with Love in Nigeria</p>
      </header>

      <section className="grid grid-cols-1 md:grid-cols-3 gap-8">
        {products.map((product) => (
          <Card key={product.id} className="p-4 rounded-2xl shadow-lg">
            <img src={product.image} alt={product.name} className="w-full h-48 object-cover rounded-xl" />
            <CardContent className="mt-4">
              <h2 className="text-2xl font-semibold">{product.name}</h2>
              <p className="text-lg text-gray-700">₦{product.price}</p>
              <Button className="mt-4 bg-green-600 text-white" onClick={() => addToCart(product)}>Add to Cart</Button>
            </CardContent>
          </Card>
        ))}
      </section>

      <footer className="mt-16 text-center">
        <p className="text-gray-600">&copy; {new Date().getFullYear()} Zeazee Natural. All rights reserved.</p>
      </footer>
    </div>
  );
}
