---
author: jnHs
Description: When you create a new IAP (in-app product) in the Windows Dev Center dashboard, you'll need to specify a product type and assign it a product ID.
title: Set your IAP product type and product ID
ms.assetid: 59497B0F-82F0-4CEE-B628-040EF9ED8D3D
---

# Set your IAP product type and product ID

An IAP must be associated with an app that you've created in the dashboard already (even if you haven't submitted it yet). You can find the button to **Create a new IAP** on either your app's **Overview** page or its **IAPs** page.

Once you've clicked the button, you'll see the **Create a new IAP** page. Here, you'll need to specify a product type and assign it a product ID.

## Product type

First, you'll need to indicate which type of IAP you are offering. This selection refers to how the customer can use your IAP.

> **Note** You won't be able to change the product type after you save this page to create the IAP. If you did choose the wrong product type, you can always delete your in-progress IAP submission and start over by creating a new IAP.

Select the product type that is appropriate for your IAP:

- Consumable: A product that can be purchased, used (consumed), and then purchased again. Consumable IAPs are often used for things like in-game currency (gold, coins, etc.) which can be purchased in set amounts and then used up by the customer.
- Durable: A product that’s bought and owned by the buyer for a specified period of time. Durable IAPs are often used to unlock additional functionality in an app. Durable IAPs are not consumed, but you can set the **Product lifetime** so that they expire after a set duration (with options from 1-365 days). The default **Product lifetime** for a durable IAP is **Forever**, which means the IAP never expires. You can change this to a different duration in the [IAP properties](enter-iap-properties.md) step of the IAP submission process.

## Product ID

Enter a unique product ID for your IAP. This is the same identifier that you will need to reference in [your app's code to call the IAP](https://msdn.microsoft.com/library/windows/apps/mt219684).

Here are a few things to keep in mind when choosing a product ID:

-   Customers won't see this product ID. (Later, you can enter a [title and description](create-iap-descriptions.md) to be displayed to customers.)
-   You can’t change or delete an IAP's product ID after it's been published.
-   A product ID can't be more than 100 characters in length.
-   A product ID cannot include any of the following characters: **&lt;&gt;\* % & : \\ ? + ,**
-   To offer your IAP on all devices, you must only use alphanumeric characters, periods, and/or underscores. If you use any other types of characters, the IAP will not be available for purchase to customers running Windows Phone 8.1 or earlier.
-   A product ID doesn't have to be unique within the Windows Store, but it must be unique to your developer account.
 






<!--HONumber=Jun16_HO3-->


