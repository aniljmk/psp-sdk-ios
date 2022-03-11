# Omini_Pay_iOS

# OMINI PAY
Easy Safe and Secure Payment gatway 

This repository implements pod for OminiPay’s iOS Framework.

# Usage
To run the example project, clone the repo, and run pod install from the Example directory first. Or you can simply download the project and install pods and run project.

# Installation | Docs
Through  Cocoa pods

```sh
pod ‘OminiPay’
```
# Manual

Drag n Drop the  ‘**Framework**’  folder into your project.

**Note**: If you will face any error , you can simply go to  Build Settings set **Enable Bitcode** to **NO**


# How to Use

View controller where you want to set payment import OminiPay library like below:

```sh
import OminiPay
```

# Create OminiPay Object

```sh
let obj = OminiPay.initWith(key: “Your OminiPa’sy Account key”)
```

# Set Delegate to view controller

obj.delegate = self

# Call CheckoutMethod For Simple Payment

```sh
 obj.checkOutRequestWith(param)
```

**Note:** param is the variable in which you set your card details:

## Parameter Sample Formate

```sh
let param = [
    "name" : "John",
    "email" : "johndoe@mailinator.com",
    "amount" : "100.0",
    "currency" : "SAR",
    "order_id" : "123",
    "card_number" : "5151515151515151",
    "exp_month" : "12",
    "exp_year" : "26",
    "cvv" : "123",
    "card_type" : "C"
]
```

# For Subscription call method 'subscriptionRequestWith(_)'

```sh
 obj.subscriptionRequestWith(param)
```

**Note:** param is the variable in which you set your subscription details along with your card:

## Parameter Sample Formate

```sh
let param : [String:Any] =
        ["name":"Raj",
         "email":"raj@mailiinator.com",
         "amount":10.00,
         "currency":"SAR",
         "order_id":420,
         "card_number":"5105105105105100",
         "exp_month":"12",
         "exp_year":"23",
         "cvv":"999",
         "remark":"This payment is done by card ios",
         "subscription_plan" : "1", //{1=>daily, 2=>weekly, 3=>monthly, 4=>yearly}
         "interval" : "1",
        ]
```
here if you choose subscription_plan = 3 and interval = 1 then it means your subscription is per month

lets have another example 
---------------

subscription = 3
interval = 3
payment will be deduct every 3 months

OR 

subscription = 4
interval = 1
payment will be deduct yearly

OR

subscription = 5
interval = 6
payment will be deduct every six month

# For Cancel Subscription call method 'cancelSubscriptionRequestWith(_)'

```sh
 obj.cancelSubscriptionRequestWith(param)
```

## Parameter Sample Formate
```sh
let cancelParam:[String:Any] = ["user_id":"2"]
```

# Add Delegate methods to ViewControler
```sh
 func paymentDoneWith(success: Bool, data: [String : Any]?)
 ```

# Example
```sh
extension ViewController : OminiResponseDelegate {
    func paymentDoneWith(success: Bool, data: [String : Any]?) {
        if success {
               //Success Block
        }else{
		//Failure
        }
    }
}
```



