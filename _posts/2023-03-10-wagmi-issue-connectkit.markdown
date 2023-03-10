---
layout: post
title:  "zkSyncEra∎Hack: Argent integration with ConnectKit"
date:   2023-03-10 14:41:19 +0100
categories: 
---

![Argent Wallet button](/zkSync-Era-Hack0/media/button-login.png)

# WalletConnect V2 issue 10/03/2023

With the launch of WalletConnect V2 and wagmi update to 0.12 version, integrating a custom wallet to ConnectKit has become more difficult. 

This is because the new version of Wagmi now `requires a projectId from WalletConnect`. As a result, users are having a anyone using their own client configuration will experience issues.

ConnectKit developper decided to delay the update until they find a 
suitable stategy to overcome this problem.

See [this PR](https://github.com/family/connectkit/pull/148) for more details.

# Consequences

ConnectKit did not update to [wagmi@0.12.0](https://github.com/wagmi-dev/wagmi/releases/tag/wagmi%400.12.0)

So no wagmi@0.12 custom wallet using Wc V2 can be added directly to ConnectKit.

My Argent Custom WalletConnector uses wagmi@0.12 so it can't be added directly, for now at least.


# Solutions

Wait until connectkit devs integrate wagmi@0.12 version.
  
