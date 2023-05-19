# Currency Values

In a POS System, a lot of currency values are exchanged between the Server and the Client. 
The API expectes and send currency values in a **eurocent**. The client is responsible for converting these eurocents values to a **formatted currency string** to display it to the user.

### Currency
The Currency is NOT part of the information you have to provider and you can expect from the API. At the moment, we assume all currency values are in the currency **EUR**. 

### Conversion

#### Convert currency value to eurocent
```typescript
function convertEuroToEurocent(euro: string): number {
    const euroValue = parseFloat(euro.replace(',', '.'));
    return Math.round(euroValue * 100);
}
```
This function will convert **22,78** to a eurocent value of **2278**. It will always round the eurocent value to the next full number to ensure we just consider **2 comma digits** in every calculation.

#### Convert eurocent values to formatted currency value 
```typescript
function convertEurocentToEuro(eurocent: number): string {
    return (eurocent / 100).toFixed(2).replace('.', ',') + ' €';
}
```
This function will convert  **2278** to a a formatted euro string **22,78 €**