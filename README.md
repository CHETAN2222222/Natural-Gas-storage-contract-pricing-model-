# Natural Gas Storage Contract Pricing Model

## Overview
A pricing model for natural gas storage contracts that calculates contract value by evaluating injection costs, withdrawal revenues, storage costs, and operational constraints.

## Key Features
- Multiple injection/withdrawal dates support
- Dynamic pricing for each transaction
- Storage cost calculation (daily rate × volume)
- Constraint validation (capacity, rates, volume balance)
- Detailed cash flow and storage profile tracking

## Pricing Formula
```
Contract Value = Sale Revenue - Purchase Cost - Storage Cost
```

## Quick Start

```python
from gas_storage_pricing import GasStorageContractPricer

pricer = GasStorageContractPricer()

result = pricer.price_contract(
    injection_dates=['2024-07-01'],
    withdrawal_dates=['2024-12-01'],
    injection_prices=[2.50],           # $/MMBtu
    withdrawal_prices=[5.00],          # $/MMBtu
    injection_volumes=[10000],         # MMBtu
    withdrawal_volumes=[10000],        # MMBtu
    max_storage_volume=15000,          # MMBtu capacity
    storage_cost_per_unit_per_day=0.01 # $/MMBtu/day
)

print(f"Contract Value: ${result['contract_value']:,.2f}")
```

## Output
Returns dictionary with:
- `contract_value`: Net value
- `total_purchase_cost`: Injection costs
- `total_sale_revenue`: Withdrawal revenues
- `total_storage_cost`: Storage costs
- `is_feasible`: Constraint satisfaction status
- `warnings`: Any violations detected

## Assumptions
- No transport delays
- Zero interest rates
- No market holidays
- Linear storage costs

## Use Case
Designed for trading desks to price storage contracts with manual oversight before production deployment.
