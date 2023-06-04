---
title: Passkey Development
layout: post
categories: ['programming']
---
When you are developing Passkey and you do not want to mess around with your own browser passkey, you can use a virtual authenticator.

In Google Chrome or Microsoft Edge
1. Open the devtool
2. Click on the icon with 3 vertical dots.
3. Click **More tools**
4. Select **WebAuthn**

In the WebAuthn tab.
1. Select Protocol **ctap2**
2. Select Transport **internal**
3. Select **Supports resident keys**, **Supports user verification**, **Supports large blog**
4. Click **Add**

Now you have a virtual authenticator to work with.