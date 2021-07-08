### Reserve IT capacity by creating a capacity pool

To be able to deploy workloads on the TF Grid, a user first needs to have reserved some IT capacity from a farmer. To do so, a user can create a pool of capacity which contains a certain amount of [cloud units](threefold:cloud_units). 
For each workload deployed, a certain amount of cloud units will be deducted from the pool as long as the workloads are alive.

Further details about capacity pool is available at: [Capacity pool](capacity_pool).

Here is an example code snippet on how to create a capacity pool and the payment for it:

```python
# Get a reference to the 0-OS SAL
zos = j.sals.zos.get()

# Create a capacity pool with 50 compute units and 50 storage units on the farm called "farm_name".
# Currencies contains a list of currency you are willing to use to pay for the capacity.
# This function returns an object container the detail of the payment to be made to reserve the capacity.
payment_detail = zos.pools.create(cu=50, su=50, farm="farm_name", currencies=["TFT", "FreeTFT"])

# Get a reference to your TFT wallet
wallet = j.clients.stellar.get('my_wallet')

# Proceed to the payment of the capacity.
# This function will create and send a transaction to the explorer.
# It returns the hash of the stellar transaction created.
txs = zos.billing.payout_farmers(wallet, payment_detail)

# Once the transaction is sent, it could take up to 2 minutes to see the pool populated with the cloud units.

# Get the pool detail.
pool = zos.pools.get(payment_detail.reservation_id)
print("compute units available:", pool.cus)
print("storage units available:", pool.sus)
```

### Extend a capacity pool

A capacity pool (in our example with id 62) could also be extended with new capacity. The instruction is similar to the creation of the pool, the difference is the `pool_id` that needs to specified. 

```bash
# Get a reference to the 0-OS SAL
zos = j.sals.zos.get()

# Extend a capacity pool with 50 compute units and 50 storage units on the farm called "farm_name".
# Currencies contains a list of currency you are willing to use to pay for the capacity.
# This function returns an object containing details of the payment to be made to reserve the capacity.
payment_detail = zos.pools.extend(pool_id=62,cu=10,su=10,currencies=["TFT", "FreeTFT"])

# Get a reference to your TFT wallet.
wallet = j.clients.stellar.get('my_wallet')

# Proceed to the payment of the extended capacity.
# This function will create and send a transaction to the explorer.
# Tt returns the hash of the stellar transaction created.
txs = zos.billing.payout_farmers(wallet, payment_detail)

# Once the transaction is sent, it could take up to 2 minutes to see the pool populated with the cloud units.

# Get the updated pool detail.
pool = zos.pools.get(payment_detail.reservation_id)
print("compute units available:", pool.cus)
print("storage units available:", pool.sus)
```
```