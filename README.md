## Problem definition

Dear Terra Classic Community. Juris Protocol is a third party project that wants to build a lending protocol on the Terra Classic network in the medium term. The project had planned to use an existing token as the governance token for the protocol. This token is (or was?) called the Rakoff Token. The token was a tribute to the real judge Jed S. Rakoff. Apparently, the real Rakoff felt offended by the token and was able to delist the token from Coinhall via court order. The original vision of Juris Protocol to use the token as a governance token is now over. End of story. Please, move on, there's nothing to see here...

But... wait. There is a way out of this mess. How about continuing the existing token and renaming it so that the judge can sit back and relax? To accomplish this, we need the full support of the Terra Classic community. Let's dive into it. Fasten your seat belts, it's gonna be technical.

## Technical background

Rakoff Token is a smart contract on the Terra Classic blockchain. The token implements a distributed ledger on Terra Classic's smart contract platform. Smart contracts on Terra Classic usually have an administrator account. This admin has the right to change the underlying code of the token at his will. This process is called code migration. During the code migration, a handler is executed that initiates all possible steps to ensure a smooth transition from the old contract logic to the new contract logic. In the case of Rakoff Token, administration rights have been renounced to ensure the integrity and immutability of the token itself

We call this “good practice”.

Juris Protocol wants to continue using the Rakoff token as a governance token, but this is prevented by Judge Jed S Rakoff's court order. Well... what would a governance token be if you can't even trade it on leading frontend platforms because a US citizen feels offended by it? One solution to this is a token rebrand from Rakoff Token to Juris Protocol. Juris Protocol's team does not see giving up the existing token, withdrawing the liquidity and simply launching a new token with a different name as a solution. That would be tantamount to a rugpull. No, we want to change the name (and token ticker) of the existing token. Since the protocol is called Juris Protocol, we propose “Juris Protocol” as well. Ticker: “JURIS”.

Why is this change necessary? For frontend applications (e.g. Coinhall), tokens are normally listed by assigning a name and a symbol to the token contract address in special asset repositories. This means that these frontends do not normally access the on-chain name/ticker of the token in order to display a name/ticker in the frontend. Partially, these repository listings have been already changed by the Juris Protocol team to reflect the rebrand. However, there are special exceptions, where the frontend rebrand is not sufficient. For example, if someone creates a new trading pair on Terraport and wants to pair their token “A” with “B”, then the Coinhall frontend will automatically list this pair, accessing the on-chain name/symbol of the tokens involved. If Juris Protocol were to come along and change the name from “Rakoff” to “Juris” in all frontends, then new listings and token pairings would not be affected by this change and would have to be updated manually every time. The same applies, for example, to listings of the Juris Protocol Token on new chains via Wormhole.

However, the change of the on-chain name from “Rakoff Token” to “Juris Protocol” cannot be carried out by the Juris Protocol team because they have renounced their administration right for reasons of “good practice” as mentioned before. We now need the permission of the delegators and validators of the Terra Classic network to make the corresponding on-chain changes to the token to reflect the rebrand. This is what this proposal is about. By the way: The corresponding changes to the contract are automatically obtained when this very proposal is accepted.

## Proposal

The Juris Protocol team asks the delegators and validators of the Terra Classic network for permission to migrate the code for the contract terra1vhgq25vwuhdhn9xjll0rhl2s67jzw78a4g2t78y5kz89q9lsdskq2pxcj2 (formerly “Rakoff Token”, in future “Juris Protocol”) to code ID 9257. If this proposal is accepted, a migration handler will be executed during the migration that sets the on-chain name/ticker of the contractact to “Juris Protocol” / “JURIS”. The source code from which the above code ID was compiled can be viewed here: https://github.com/fragwuerdig/cw20-taxed/tree/v1.1.0%2Btaxed003/contracts/cw20-taxed. The code hash for that id is 8ff9f7840b71cab402c35b305b7edbb46dbb4da51f3dc8281277bbf62765739e

## Verification (For Technical Folks)

For the verification we assume a Linux system with the corresponding installations of developer programs. Technical personnel will be able to recognize from the following sequence of commands which requirements must be met in order to verify that the on-chain deployment (code id 9257) is actually a build result from the above repository.

The code id hash mentioned above can be checked independently by first calculating the hash of the on-chain deployment (code id 9257). this can be extracted with the following command

```
curl “https://terra-classic-lcd.publicnode.com/cosmwasm/wasm/v1/code/9257” | jq -r .data | base64 --decode | shasum -a 256 -
```

The calculated hash should match the output of the following command sequence:

```
git clone https://github.com/fragwuerdig/cw20-taxed
cd cw20-taxed
git checkout v1.1.0+taxed003
./build.sh
shasum -a 256 artifacts/cw20_taxed.wasm
```

## Implications / Risks / Opportunities

there are no implications for holders and participants in the token as a result of this proposal. the contract address remains the same. the account balances of the addresses are transferred 1:1. the token can be traded in the usual terraport pool against LUNC. The liquidity remains the same. furthermore, there is no risk for the network as a result of the migration. Juris Protocol hopes that the rebrand will give it the freedom to list the token independently and automatically on frontend providers again. from the current perspective, no negative consequences of the rebranding are foreseeable. the independence of the future token under the name juris from its original meme template can also help to steer the project towards a serious external perception. but please let's not forget the fun. and if it does get boring, you know what to do: **#blamefrag**.
