# IT capacity provisioning flow

Reservation of capacity happens according a standard process :
- Farmer sets a price
- User searches capacity
- User requests reservation
- Payment process
- Automated provisioning process of the workload towards the nodes

If all OK : 
- Confirmation of the provisioning and complete payment to the farmer
- Further deployment instruction to the user

In case of an error in the provision flow : 
- Reporting of the error
- Refund to the user

![grid_provisioning2](https://raw.githubusercontent.com/Threefoldtech/zos/master/assets/grid_provisioning2.png)

## Reservation object

```json
reservation = {
    // NOTE: state is not accepted in user requests. The state is completely managed by
    // the network. hence creating a reservation does not accept any values assigned to the
    // state object.
    // it's part of the reservation object thought because the API will always return a valid
    // state object.
    // Some changes to the state are accepted from the user, but only via the defined API
    // end points
    "state": [state object],
    "contract": [contract object],

    ...: [reservation params]
}
```