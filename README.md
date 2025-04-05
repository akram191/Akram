import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";

export default function Dashboard() {
  const [milkPurchases, setMilkPurchases] = useState([
    { supplier: "Ramesh", liters: 100, rate: 50, date: "2025-04-05" },
    { supplier: "Suresh", liters: 80, rate: 52, date: "2025-04-05" },
  ]);

  const [paneerSales, setPaneerSales] = useState([
    { customer: "Hotel Taj", kg: 300, rate: 220, date: "2025-04-05" },
    { customer: "Sweet Mart", kg: 250, rate: 210, date: "2025-04-05" },
  ]);

  const totalMilkCost = milkPurchases.reduce((sum, m) => sum + m.liters * m.rate, 0);
  const totalPaneerSale = paneerSales.reduce((sum, p) => sum + p.kg * p.rate, 0);
  const profit = totalPaneerSale - totalMilkCost;

  return (
    <div className="p-6 grid gap-4 md:grid-cols-3">
      <Card>
        <CardContent className="p-4">
          <h2 className="text-xl font-bold">Milk Purchases</h2>
          <p>Total Cost: ₹{totalMilkCost}</p>
          <ul className="mt-2 text-sm text-muted-foreground">
            {milkPurchases.map((m, i) => (
              <li key={i}>
                {m.date} – {m.supplier}: {m.liters}L @ ₹{m.rate}
              </li>
            ))}
          </ul>
        </CardContent>
      </Card>

      <Card>
        <CardContent className="p-4">
          <h2 className="text-xl font-bold">Paneer Sales</h2>
          <p>Total Sales: ₹{totalPaneerSale}</p>
          <ul className="mt-2 text-sm text-muted-foreground">
            {paneerSales.map((p, i) => (
              <li key={i}>
                {p.date} – {p.customer}: {p.kg}kg @ ₹{p.rate}
              </li>
            ))}
          </ul>
        </CardContent>
      </Card>

      <Card>
        <CardContent className="p-4">
          <h2 className="text-xl font-bold">Profit Summary</h2>
          <p>Estimated Profit: ₹{profit}</p>
        </CardContent>
      </Card>
    </div>
  );
}
npm start
