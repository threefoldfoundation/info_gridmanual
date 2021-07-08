# Get a Hosted 3Bot

3Bot is your virtual system administrator which helps you to deploy solutions on top of the ThreeFold_Grid.

## How to Deploy your 3Bot

- For **Mainnet** Go to 3Bot [Deployer Website](https://deploy3bot.grid.tf)
- For **Testnet** Go to 3Bot [Testnet Deployer Website](https://deploy3bot.testnet.grid.tf)

## Create a 3Bot

In the welcome step you can either recover a previously created 3Bot or create a new one.

If you choose to create a new 3Bot, please go through following steps:

### Name Your 3Bot

This name will be used to identify this 3Bot. Keep in mind that this name will also be used as your 3Bot's subdomain (a part of your 3Bot's web address).

![](img/threebot_1_getname.png)

### Choose the 3Bot Configuration

The 3Bot comes in 3 sizes. Depending on the intensity you intend to use this hosted 3Bot, choose the flavor that best fits your needs. For example, if you intend to use the hosted development features, you might need more resources available. The flavor can be changed after deployment.

![](img/threebot_1b_deployer_info.png)

### Upload an SSH key (optional)

If you intend to ssh into your 3Bot container, you can provide an ssh key in the next step. It is also possible to add and remove ssh keys later through the 3Bot's Settings page.

![](img/threebot_1c_ssh_key.png)

### Select the Back Up & Restore Password

Your 3Bot has a backup and restore feature accessible on the dashboard. A password protects these capabilities, please store it safely or remember it well.

![](img/threebot_1a_recovery_secret_key.png)

### Choose How You Wish to Select the Deployment Location

The deployer is able to choose a deployment location for you automatically. If you have a specific farm or node in mind, choose the appropriate option and you'll have a chance to select it in the next step. Otherwise, just pick "Automatic" to have a farm and node chosen for you.

For now, deployments are limited to a certain set of farms and nodes. In the future, more farms will be available, allowing for greater choice in where your 3Bot lives for reasons of network performance or data sovereignty.

![](img/threebot_1e_location_policy.png)

### Choose the Deployment Location

If you opt for a specific farm or node, you have the option now to choose from available farms or nodes.

![](img/threebot_1d_deploy_location.png)

### Choose e-mail Settings

Your 3Bot can send alerts via email for certain events. To enable this feature, email server settings and credentials are required. Enter them on this page, or later from the Settings menu.

![](img/threebot_1f_email_settings.png)

### Setup and Initialization

Once all info is know, the deployment of your 3Bot can start.
Multiple steps happen now behind the scene:

- The infrastructure is prepared for a 3Bot deployment.
- A pre-funding of this capacity is done
- The right hardware capacity is selected, according to your choice.
- The network is generated.
- Gateways are being prepared.
- The 3Bot is deployed.
- The 3Bot is initialized so you can start working with it as soon as you have done the payment.

This process can take a while.

![](img/threebot_6_3bot_setup.png)
![](img/threebot_7_3bot_deploy.png)
![](img/threebot_8_3bot_init.png)

### Choose the 3Bot's Expiration Time

The expiration time determines your preference for how long you want to keep this 3Bot alive. This will calculate the amount of grid capacity you need to purchase in order to keep the 3Bot online. You can always extend your 3Bot's life span by extending your capacity reservation, or restart your 3Bot later if it's funding has run out.

![](img/threebot_2_expiry.png)

### Pay for Your Capacity by using a Stellar Wallet

You will be shown payment details as below. Send the required amount to the address shown, using a Stellar wallet. This can be done simply by scanning the QR code using your Threefold Connect app.

If you're entering the transaction manually without scanning the QR code, please do not forget to include the reservation ID as the memo text for the transaction. This is needed to link the payment to the specific reservation, and the payment will fail without it.

![](img/threebot_4_payment.png)

### Wait Until Your Payment Has Succeeded

Payment can take some time. The screen gives an overview of the amount, currency, destination wallet and reservation ID. Once processing the payment is detected, it goes to the next step.
![](img/threebot_5_pay_process.png)

### Set up Wireguard (optional)

Hosted 3Bots provide a web gateway for access to the browser based interface from any internet connected device.

If you want to access the 3Bot container directly or use ssh, you need to set up a Wireguard connection on your local computer. Download the configuration file and follow the instructions to do this.

![](img/threebot_y_container_access.png)

### Congratulations, Your Hosted 3Bot is Now Live!

Congratulations, your 3Bot has been successfully deployed.

You can access your 3Bot by following the link provided, or using the IP address if you've set up Wireguard.

![](img/threebot_z_success.png)

Log in here using your ThreeFold Connect app.

![](img/threebot_zz_url.png)

### Access Your Dashboard

After signing in and agreeing to terms and conditions, you'll see the 3Bot dashboard with some information about resource usage and currently running processes. Please note that the memory and disk usage refer to the whole node that your 3Bot is running on, not necessarily all resources available to the 3Bot.

![](img/threebot_admin_dashboard.png)

### Explore the 3Bot Admin Panel's Features

You can now access all the features of your 3Bot, such as the Code Server, Python Notebooks, Farm Management, and many more. Feel free to click on [the Dashboard](3bot_admin) section to learn more about your hosted 3Bot features.
