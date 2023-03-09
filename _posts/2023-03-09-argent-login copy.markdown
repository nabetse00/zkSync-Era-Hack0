---
layout: post
title:  "zkSyncEra∎Hack: Argent integration with web3modal V2"
date:   2023-03-09 14:24:07 +0100
categories: 
---

![Argent Wallet button](/zkSync-Era-Hack0/media/media/button-login.png)

# Intro
If you're developing a website or web application that involves cryptocurrency transactions, integrating a login button for the Argent wallet can be a convenient way to allow users to sign in and interact with your platform. In this blog post, we'll provide a step-by-step guide for creating an Argent wallet login button using the Web3Modal library.

Web3Modal is a library that allows you to connect your website to the Ethereum blockchain and interact with smart contracts and decentralized applications. In this blog post, we will walk you through the steps of adding an Argent wallet login button using Web3Modal

# Step 1: Install Web3Modal

To get started, you'll need to install the Web3Modal library. You can install it using npm by running the following command:

```bash
Copy code
npm install web3modal
```

# Step 2: Import Web3Modal
```ts
import {
  EthereumClient,
  modalConnectors,
  walletConnectProvider,
} from "@web3modal/ethereum";
import { Web3Modal } from "@web3modal/react";
import { configureChains, createClient, WagmiConfig } from "wagmi";
import { arbitrum, mainnet, polygon } from "wagmi/chains";
```

# Configure

```ts
const chains = [arbitrum, mainnet, polygon];

// Wagmi client
const { provider } = configureChains(chains, [
  walletConnectProvider({ projectId: "<YOUR_PROJECT_ID>" }),
]);
const wagmiClient = createClient({
  autoConnect: true,
  connectors: modalConnectors({
    projectId: "<YOUR_PROJECT_ID>",
    version: "1", // or "2"
    appName: "web3Modal",
    chains,
  }),
  provider,
});

// Web3Modal Ethereum Client
const ethereumClient = new EthereumClient(wagmiClient, chains);
```

# Add to Components
```ts
function App() {
  return (
    <>
      <WagmiConfig client={wagmiClient}>
        <HomePage />
      </WagmiConfig>

      <Web3Modal
        projectId="<YOUR_PROJECT_ID>"
        ethereumClient={ethereumClient}
      />
    </>
  );
}
```

```ts
import { Web3Button } from "@web3modal/react";

export const YourApp = () => {
  return <Web3Button />;
};
```

You can now use react hooks and components with this button.

# So nothing todo ?

With this solution you connect your argent wallet through WalletConnect API.

If we want to connect directly to Argent Wallet we need to use `Argen login provider`
from `npm i @argent/login`

This was done adding a custom wagmi wallet connector.

# Source code and details

Refer to:

- [Argent Wagmi Custom Connector Source code](https://github.com/nabetse00/argent-wagmi-connector)
- [Example of usage from a react-ts template](https://github.com/nabetse00/test-argent-wagmi-connector)




