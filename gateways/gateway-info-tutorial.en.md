# Vite Gateways Submission Guideline

## Requirements

### Information Preparation

Prepare submission documents under the following requirements.

`LOGO IMAGE`

- Image format: `png`
- Image size: `200x200 pixels`

![Icon Specification](../assets/images/icon-specification.jpg)

`JSON FILE`

| field | value required |description | schema type |
|:------------:|:-----:|:-----------:|:-----:|
| name | necessary | gateway name | String |
| policy | necessary | Terms of service, terms of exchange, restrictions and privacy policies | Map<String, String> |
| overview | necessary | introduction of your token | Map<String, String> |
| links | necessary | website, whitepaper, github, and other media links | Map<String, List<String>> |
| support | necessary | customer service can be provided through Discord or Telegram | String |
| gatewayTokens | necessary | details of cross-chain coin | Map<String, GatewayMappedTokenDetail> |
| selfCertification | necessary | self-certification status. It should be YES (see below for more details) | String |

> The logo and json file names should both be your gateway name, and written in all `lowercase` letters. If the original name contains space, replace with `-`. Example: if your gateway name is Vite Labs, your file names should be vite-labs.json and vite-labs.png.

#### Self-Certification
	
Gateway applicants should self-certify that the following guidelines have been met.

- The cross-chain gateway has been set up and running for at a minimum of 1 month without known issues
- Internal policy on securing the original assets, such as managing custody with hot/cold wallet approach, safeguarding keys to ensure they are not stolen
- Unit Tests to make sure deposit/withdraw works well (try with edge cases)
- Code Review of the gateway code by a trusted third-party (without sharing the code with a potential attacker looking to exploit the code)
	
**_Ultimately the gateway is solely responsible for customer funds, and ViteX bears no liability for any loss._**
	

#### Gateway Cross-chain Token ("Mapped Token") Detail

| field | necessity |description | schema type |
|:------------:|:-----:|:-----------:|:-----:|
| mappedSymbol | necessary | symbol of the cross-chain coin, eg: UNI | String |
| mappedNet | necessary | category of the cross-chain coin, eg: ETH | String |
| mappedTokenId | necessary | unique key of the cross-chain coin, eg: 0x1b793E49237758dBD8b752AFC9Eb4b329d5Da016 | String |
| url | necessary | apiUrl for your gateway | String |

> Note: To learn more about the API specification for the field `url`, see this tutorial: [Gateway Profile Guideline](apiurl-tutorial.en.md)

#### Keyword in the field  Map-Value above.

* `gatewayTokens`
    tti_[xxxxxxxxxxxxxxxxxxxxxxxx]


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

* `overview`
    
    * **en** 
    * zh
  
    > Note: Providing an English version is essential.

* `policy`
    
    * **en** 
    * zh

    > Note: Providing an English version is essential.

> Note: you must use the right key name, and all must be `lowercase`.


##### Example:

```json
{
    "name":"Vite Labs",
    "policy":{
    	"en":"https://x.vite.net/privacy.html"
    },
    "overview":{
    	"zh":"Vite Labs官方网关，负责BTC、ETH、USDT(ERC20)、GRIN四种代币跨链服务",
    	"en":"The gateway provided by Vite Labs, running cross-chain services for four coins: BTC, ETH, USDT(ERC20)"
    },
    "links": {
      "website":["https://vite.org"],
      "explorer":["https://explorer.vite.net"],
      "whitepaper":[
        "https://github.com/vitelabs/whitepaper/blob/master/vite_en.pdf",
        "https://github.com/vitelabs/whitepaper/blob/master/vite_cn.pdf"
        ]
    },
    "support":"gateway@vite.org",
    "gatewayTokens":{
    	"tti_687d8a93915393b219212c73":{
			"mappedSymbol": "ETH",
			"mappedNet": "ETH",
			"mappedTokenId": "",
			"url": "https://xxxx/gateway/eth/"
    	},
    	"tti_b90c9baffffc9dae58d1f33f":{
			"mappedSymbol": "BTC",
			"mappedNet": "BTC",
			"mappedTokenId": "",
			"url": "https://xxxx/gateway/btc/"
    	},
    	"tti_80f3751485e4e83456059473":{
			"mappedSymbol": "USDT",
			"mappedNet": "ETH",
			"mappedTokenId": "0xdac17f958d2ee523a2206206994597c13d831ec7",
			"url": "https://xxxx/gateway/eth/"
    	},
    	"tti_289ee0569c7d3d75eac1b100":{
			"mappedSymbol": "GRIN",
			"mappedNet": "GRIN",
			"mappedTokenId": "GRIN",
			"url": "https://xxxx/gateway/grin/"
    	}
    }
}

```


### Steps to upload

We recommend that you complete the procedures with your developers, or you can follow [Github Guideline](../github-tutorial.en.md) to operate on github web page.

1. Fork the repo to your own github account

2. Clone the repo from your own account, please note: do no clone the origin one directly, but clone the repo you forked
```
git clone https://github.com/[your-own-repo]/crypto-info.git
cd crypto-info/
```

3. Create a new branch (file) and switch to a new branch named by your gateway name
  For example:
```
git branch gateway-[gatewayname]
git checkout gateway-[gatewayname]
```

4. Please ensure to use UTF-8 encoding in the json file to avoid Travis-CI build error. Please check the template file to fill in the complete gateway information: [$template.json](../gateways/$template.json)


5. Create the directory with the name of your gateway name with the required format under the directory `gateways` if not exist. Add your gateway json file and logo image to the directory created, named by your gateway name. 
  For example:
```
gateways/vite-labs/

vite-labs.json
vite-labs.png
```

7. Commit and push the information to your repo
  For example:
```
git add -A
git commit -m "add gateway [Gateway Name]"
git push origin gateway-[gatewayname]
```

8. Under your repo page, click the "New pull request" button. Then, attach the detailed gateway informatio, this includes but not limited to the following: 
  * Name of gateway
  * Applicant's legal name of gateway
  * Legal name of submitter
  * Contacts

   Sample PR: https://github.com/vitelabs/crypto-info/pull/xxx

9. We will review your PR as soon as possible. If there is no problem with your PR, we will merge it into our master branch. And then your token profile will display in the current Vite App

