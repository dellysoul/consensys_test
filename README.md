# Intro

Welcome one, welcome all to the cryptokitty whisperer

The live file can be viewed @ cryptokittywhisperer.herokuapp.com

To reproduce
npm install
install metamask chrome extension
npm start

# How Abhishek Solved the Problem

## the start

* read README
* npm i & start
* created skeleton UI & logic (controlled input, etc)

## get ABI

"wtf is an ABI"
Attempt 1- (more than 5 minutes)

* researched web3 docs
* found bytecode via contract address via async web3.eth call , stored in bytecode file in contracts folder
* decompiled bytecode into a sludge of bytecode and contract code , stored in contract file in contracts folder
* ran bytecode on remix
* didnt compile
* googled- found etherscan- d'oh!

Attempt 2- (less than 5 minutes)

* went to etherscan
* put in address
* literally found contract ABI right there
* lol'd
* stored the abi part as a json

## build simple UI

* tested web3.contract.methods.getKitty() method on console
* created logic dispatched onClick of button
* store callback into state
* if data exists, display core info

## add kitty image

* Got api
* Added logic
* Added UI

## add randomizer

* Added function
* Added button
* Added logic

## Add error handling

* added regexp to ensure only numbers are passed in and app doesn't crash
* added api error handler
* shows alert

## Design

* material-ui
* plug in components

![](https://i.imgur.com/A7D2gMb.png)

[CryptoKitties](http://cryptokitties.co) is one of the most popular distributed apps on the Ethereum Network. It's a game that allows players to purchase, collect, breed and sell various types of virtual cats.

To be able to run CryptoKitties on your browser you'll need to install [Metamask](http://metamask.io/) or use a dedicated Ethereum browser like Mist or Parity.

For this challenge you will create a simple UI that will be able to interact with the Ethereum Blockchain, using web3.js and the [drizzle](https://truffleframework.com/docs/drizzle/getting-started) library. This UI will allow the user to type in a CryptoKitty's ID, and will display information about that Kitty.

# Requirements to complete this challenge

* Use the code provided in this repo as a starting point to build your solution
* Given the address for the CryptoKitties Smart Contract: `0x06012c8cf97bead5deae237070f9587f8e7a266d` Find its _ABI_ (You will need it to complete the challenge)
* Build a simple UI where the user can type in an ID and display the following information about a Kitty:
  * Genes
  * Birth time
  * Generation
* You will get extra points if you also display the Kitty's picture. 🏅
* You will get extra points if you create a "Fetch random Kitty" button. 🏅
* Feel free to customize the styles as you wish or use any extra libraries that you need

## The result should look somethig like this:

![kitty browser](https://i.imgur.com/YQdKma5.png)

# Hints

* You will need to use the `drizzle` instance available on React's context (See components/Browser.js)
* You will need to explore the smart contract `methods` to find out which one will get you the kitty's info (This operation won't require spending any ether)

# Setting up your dev environment

* Install and setup Metamask in your browser
* Clone this repo, to be used as a starting point for your solution
* Install the dependencies and run the development server

# Code Overview

This repo contains a few components that will be useful for you to complete this project. These components are based on the [drizzle-react](https://github.com/trufflesuite/drizzle-react) examples

### containers/Loading.js

Shows a Loading message while drizzle is being initialized or an error message if the browser is not _web3 enabled_

```Javascript
if (window.web3 === undefined || this.props.web3.status === 'failed') {
      return(
        // Display a web3 warning.
        <div className="warning">
          <p>This browser has no connection to the Ethereum network. </p>
          <p>Please use the Chrome/FireFox extension MetaMask, or dedicated Ethereum browsers Mist or Parity.</p>
        </div>
      );
    }

    if (this.props.drizzleStatus.initialized) {
      // Load the dapp.
      return Children.only(this.props.children);
    }

    return(
      // Display a loading indicator.
      <div className="loading">
        <h1>Loading dapp...</h1>
        <img src="https://www.cryptokitties.co/images/loader.gif" width="120" alt="loading" />
      </div>
    );
```

## App.js

Initializes the `DrizzleProvider` and wraps your app with the `Loading` component.

```Javascript
class App extends Component {
  render() {
    const drizzleOptions = {
      contracts: []
    };

    return (
      <DrizzleProvider options={drizzleOptions}>
        <Loading>
          <Browser />
        </Loading>
      </DrizzleProvider>
    );
  }
}
```

## components/Browser.js

Once you have the Smart Contract's ABI, uncomment the lines you need to add the contract to the drizzle store, and start building your solution.

## Questions or comments

For any questions or comments please contact `Dragos Rizescu <dragos.rizescu@consensys.net>` or `Ruben Torres <ruben.torres@consensys.net>`
