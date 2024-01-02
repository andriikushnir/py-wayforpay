# py-wayforpay

Module for interacting with the Wayforpay payment system for Python.

Official Website: [https://wayforpay.com/uk](https://wayforpay.com/uk)\
Documentation: [https://wiki.wayforpay.com/](https://wiki.wayforpay.com/)


## Project status
In developing

## Installation Instructions


```bash
# for Windows
pip install requirements.txt

#for Linux
pip3 install requirements.txt
```

## Usage

### Creating an Invoice

```python
from wayforpay import WayForPay


key = 'YOUR KEY'
domain_name = 'YOUR DOMAIN NAME'
merchantAccount = 'YOUR MERCH' #test_merch_n1

wayforpay = WayForPay(key=key, domain_name=domain_name)

result = wayforpay.create_invoice(
    merchantAccount=merchantAccount,
    merchantAuthType='SimpleSignature',
    amount=132.44,
    currency='UAH',
    productNames=["Ui", "Mafia"],
    productPrices=[110, 12.44],
    productCounts=[1, 5]
)

print(result.invoiceUrl)
print(result.json())
```

### Check status

```python
result = wayforpay.check_invoice(
    merchantAccount=merchantAccount,
    orderReference='ORDER REFERENCE'
)

print(result.json())
print(result.reasonCode)
```

### Delete Invoice

```python
result = wayforpay.delete_invoice(
    merchantAccount=merchantAccount,
    orderReference='ORDER REFERENCE'
)
```