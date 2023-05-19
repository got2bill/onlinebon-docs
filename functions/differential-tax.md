# Differential Tax

This function is used when buying second hand goods like a car. 

### 1. Create new Buying Invoice (OPTIONAL)
The Shop can create a buying invoice where the amount is negative with the serial number.

### 2. Create a new invoice
Add a new item with a **Buying Price (Anschaffungswert)**. You can only provide a Buying Price (Anschaffungswert) for an invoice item if you activated these 
options when creating this product. You always provide the buying value per quantity unit.

You can provide the Buying price in **two ways**:

| Searching for a serial number | Manually entering a buying value |
|---|---|
| that you provided before at a buying invoice. If you find a buying invoice with the provided serial number, it will automatically populate the buying value into the field.  | If you do not create a buying invoice or you did not provide a serial, you can enter the buying value on your manually.  |
|   |   |

### 3. Cart Preview

### 4. Receipt Preview & Receipt

### 5. Completions

On the completions, we print an extra section that is displaying a list of all receipts that included items with differential tax.

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