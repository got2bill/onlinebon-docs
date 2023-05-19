## Gross / Net / Tax Calculations

These steps are performed to calculate the total amounts of the receipt. The nominal values of the products are always gross amounts.
Rounding is always done to the nearest whole number (cent). Up to 4, round down; 5 and above, round up.

### 1. Calculation of Gross / Net / Tax for each item

1.1. Calculation of the net amount for the item:
```Round(Product Nominal / (100 + Tax Rate) * 100)```

1.2. If there are item discounts, subtract the net discounts from the net amount of the item.

1.3. Calculation of the gross amount for the item:
```Round((Net Amount / 100) * (100 + Tax Rate))```

1.4. Calculation of the tax amount for the item:
```Round(Gross Amount - Net Amount)```

### 2. Summation of the item amounts to the total amount of the receipt

2.1. Grouping and summation of the tax amounts by tax rate

2.2. Summation of the gross amounts


### Examples
```ts
function calculateNetAmount(nominal: number, taxRate: number): number {
  const netAmount = Math.round((nominal / (100 + taxRate)) * 100);
  return netAmount;
}

function calculateGrossAmount(netAmount: number, taxRate: number): number {
  const grossAmount = Math.round((netAmount / 100) * (100 + taxRate));
  return grossAmount;
}

function calculateTaxAmount(grossAmount: number, netAmount: number): number {
  const taxAmount = Math.round(grossAmount - netAmount);
  return taxAmount;
}

// Example usage for Posten 1
const nominal1 = 149;
const taxRate1 = 10;

const netAmount1 = calculateNetAmount(nominal1, taxRate1);
const grossAmount1 = calculateGrossAmount(netAmount1, taxRate1);
const taxAmount1 = calculateTaxAmount(grossAmount1, netAmount1);

console.log("Posten 1:");
console.log("Nettobetrag:", netAmount1); // Output: 135
console.log("Bruttobetrag:", grossAmount1); // Output: 149
console.log("Steuerbetrag:", taxAmount1); // Output: 14

// Example usage for Posten 2
const nominal2 = 259;
const taxRate2 = 10;
const discount = 100;

const netDiscount = calculateNetAmount(discount, taxRate2);
const netAmount2 = calculateNetAmount(nominal2, taxRate2) - netDiscount;
const grossAmount2 = calculateGrossAmount(netAmount2, taxRate2);
const taxAmount2 = calculateTaxAmount(grossAmount2, netAmount2);

console.log("Posten 2:");
console.log("Nettobetrag:", netAmount2); // Output: 144
console.log("Bruttobetrag:", grossAmount2); // Output: 158
console.log("Steuerbetrag:", taxAmount2); // Output: 14

// Example usage for Gesamtbetrag
const totalGrossAmount = grossAmount1 + grossAmount2;
const totalTaxAmount = taxAmount1 + taxAmount2;

console.log("Gesamtbetrag:");
console.log("Bruttobetrag:", totalGrossAmount); // Output: 307
console.log("Steuerbeträge:", totalTaxAmount); // Output: 28

```