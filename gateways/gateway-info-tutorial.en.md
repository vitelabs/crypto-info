# Vite Gateways Submission Guideline

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
| name | necessary | gateway name | String |
| policy | necessary | Terms of service, terms of exchange, restrictions and privacy policies | Map<String,String> |
| overview | necessary | introduction of your token | Map<String,String> |
| links | optional | website,whitepaper,github, and other media links. | Map<String,List<String>> |
| support | necessary | customer service, eg: support@*****.com | String |
| gatewayTokens | necessary | details of extranet coin mapped | Map<String,GatewayMappedTokenDetail> |

> Filename should be your gateway name in all `lowercase` letters and the string must be join with `-`, same name for both .json and .png (Including capitalization), eg: Vite Labs -> vite-labs, vite-labs.json | vite-labs.png

#### GatewayMappedTokenDetail

| field | necessity |description | schema type |
|:------------:|:-----:|:-----------:|:-----:|
| mappedSymbol | necessary | symbol of the extranet coin mapped, eg: VITE | String |
| mappedNet | necessary | category of the extranet coin mapped, eg: ETH | String |
| mappedTokenId | necessary | unique key of the extranet coin mapped, eg: 0x1b793E49237758dBD8b752AFC9Eb4b329d5Da016 | String |
| url | necessary | apiUrl your gateway provided | String |

> Note: For more information about API specification for the field `url`, please refer to the tutorial here: [Gateway Profile Guideline](apiurl-tutorial.en.md)

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

    > Note: We consider projects that fill in the `website`,`whitepaper`,`github` fields to be generally reliable gateways that do not give warning messages in ViteX.

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

