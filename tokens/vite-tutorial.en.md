# Vite Token Profile Submission Guideline

## Requirements

### Information Preparation

Prepare submission documents under the following requirements.

`LOGO IMAGE`

- Image format: `png`
- Image size: `200x200 pixels`

![Icon Specification](../assets/images/icon-specification.jpg)


`JSON FILE`

| field | necessity |description | schema type |
|:------------:|:-----:|:-----------:|:-----:|
| tokenId | necessary | tokenId on Vite BlockChain | String |
| overview | necessary | introduction of your token | Map<String,String> |
| links | optional | website,whitepaper,github, and other media links. | Map<String,List<String>> |
| initialPrice | optional | the initial price of your token to the base currency | String |

> Filename should be your token ID in all `lowercase` letters, same name for both .json and .png (Including capitalization), eg: tti_b90c9baffffc9dae58d1f33f.json, tti_b90c9baffffc9dae58d1f33f.png

#### Keyword in the field  Map-Value above.

* `links`

    * **website** 
    * **whitepaper** 
    * **github** 
    * explorer
    * email
    * twitter
    * facebook
    * reddit
    * instagram
    * steemit
    * coinmarketcap
    * youtube
    * telegram
    * discord
    * linkedin
    * medium
    * blog

    > Note: We consider projects that fill in the `website`,`whitepaper`,`github` fields to be generally reliable gateways that do not give warning messages in ViteX.

* `overview`
    
    * **en** 
    * zh

    > Note: Providing an English version is essential.

* `initialPrice`
    
    * btc
    * eth
    * usd

> Note: you must use the right key name, and all must be `lowercase`.


##### Example:

```json 
{
    "tokenId": "tti_b90c9baffffc9dae58d1f33f",
    "overview":{
        "en":"Bitcoin (BTC) is a consensus network that enables a new payment system and a completely digital currency. Powered by its users, it is a peer to peer payment network that requires no central authority to operate."
    },
    "links":{
        "website":["https://bitcoin.org/en/"],
        "whitepaper":["https://bitcoin.org/bitcoin.pdf"],
        "explorer":["https://www.blockchain.com/explorer/"],
        "github":["https://github.com/bitcoin/"]
    },
    "initialPrice":{
        "usd": "11363.0394858",
        "eth": "53.51367153483174",
        "btc": "1.00000000"
    }
}

```


## Steps to upload

We recommend that you complete the procedures with your developers, or you can follow [Github Guideline](../github-tutorial.en.md) to operate on github web page.

1. Fork the repo to your own github account

2. Clone the repo from your own account, please note: do no clone the origin one directly, but clone the repo you forked
```
git clone https://github.com/[your-own-repo]/crypto-info.git
cd crypto-info/
```

3. Create a new branch (file) and switch to a new branch named by your token symbol
  For example:
```
git branch token-[tti_xxx]
git checkout token-[tti_xxx]
```

4. Please ensure to use UTF-8 encoding in the json file to avoid Travis-CI build error. Please check the template file to fill in the complete token information: [$template.json](../tokens/$template.json)


5. Create the directory with the name of your tokenSymbol under the directory `tokens` if not exist. Add your token json file and logo image to the directory created, named by your tokenId(tokenAddress). 
  For example:
```
tokens/btc/

tti_b90c9baffffc9dae58d1f33f.json
ti_b90c9baffffc9dae58d1f33f.png
```

7. Commit and push the information to your repo
  For example:
```
git add -A
git commit -m "add token [token_symbol] [tti_xxx]"
git push origin token-[tti_xxx]
```

8. Under your repo page, click the "New pull request" button. Then, attach the detailed token project information, this includes but not limited to the following: (Project basic information; Project team background; Purpose of coinage; Contact information).

   Sample PR: https://github.com/vitelabs/crypto-info/pull/xxx

9. We will review your PR as soon as possible. If there is no problem with your PR, we will merge it into our master branch. And then your token profile will display in the current Vite App

