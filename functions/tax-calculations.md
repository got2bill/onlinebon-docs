# Tax calculations

## Gross / Net / Tax Calculations of a receipt

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

## Differential Tax

This function is used when buying second hand goods like a car. 

### 1. Create new Buying Invoice (OPTIONAL)
The Shop can create a buying invoice where the amount is negative with the serial number.
![Screenshot 2023-05-19 at 12 30 33](https://github.com/got2bill/onlinebon-docs/assets/9700679/58c2d4a1-ca4b-468e-85cf-cdbe65b2609a)


### 2. Create a new invoice
Add a new item with a **Buying Price (Anschaffungswert)**. You can only provide a Buying Price (Anschaffungswert) for an invoice item if you activated these 
options when creating this product. You always provide the buying value per quantity unit.

You can provide the Buying price in **two ways**:

| Searching for a serial number | Manually entering a buying value |
|---|---|
| that you provided before at a buying invoice. If you find a buying invoice with the provided serial number, it will automatically populate the buying value into the field.  | If you do not create a buying invoice or you did not provide a serial, you can enter the buying value on your manually.  |
| ![Screenshot 2023-05-19 at 12 30 42](https://github.com/got2bill/onlinebon-docs/assets/9700679/10f2fb30-6229-4056-84ec-43cd282fe191) | ![Screenshot 2023-05-19 at 12 30 47](https://github.com/got2bill/onlinebon-docs/assets/9700679/154f73dd-216d-4b11-8796-dc78ee7d9dd2)|

### 3. Cart Preview
![Screenshot 2023-05-19 at 12 30 53](https://github.com/got2bill/onlinebon-docs/assets/9700679/ff547ad1-3cec-455c-874e-51e4d7900eb1)

### 4. Receipt Preview & Receipt
![Screenshot 2023-05-19 at 12 31 00](https://github.com/got2bill/onlinebon-docs/assets/9700679/35782606-5207-4b2d-a4fa-98d52df41562)

### 5. Completions

On the completions, we print an extra section that is displaying a list of all receipts that included items with differential tax.

![Screenshot 2023-05-19 at 12 31 11](https://github.com/got2bill/onlinebon-docs/assets/9700679/d8de130a-21c6-4633-ae6a-77ae3d368398)


The tax amount will be calculated based on the **profit** and the **taxRate of the sold item**.

#### For example:

```typescript
function calculateTaxOnNetProfit(buyingValue: number, soldValue: number, taxRate: number): number {
  const grossProfit = soldValue - buyingValue
  const netProfit = profitGross - (profitGross * (taxRate / 100));
  const taxOnNetProfit = netProfit * (taxRate / 100);

  return taxOnNetProfit;
}

// Example usage
const buyingValue = 3000;
const soldValue = 5000;
const taxRate = 20;

const taxOnNetProfit = calculateTaxOnNetProfit(buyingValue, soldValue, taxRate);

console.log("Tax on Net Profit:", taxOnNetProfit); // Output: 333

```