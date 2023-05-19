# Differential Tax

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
