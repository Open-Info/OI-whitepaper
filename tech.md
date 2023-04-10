---
description: Irrefutable source of truth.
---

# 👾 Soulbound Certification

## Types of SNFTs

The Soulbound non-fungible token (SNFT) is a digital asset that is used by Open Info for verifying users, certifying information, and flagging malicious actors. Each is a specialized type of NFT that is designed to be tamper-proof and resistant to forgery, making it ideal for use in situations where trust and verification are critical.

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td>Verified Public Key:</td><td>Free to mint.</td><td>Requires a validate social media account.</td><td><a href=".gitbook/assets/vrfd.png">vrfd.png</a></td></tr><tr><td>Certified Public Key:</td><td>Unlocked through staking.</td><td>Requires KYC or proof of business trade.</td><td><a href=".gitbook/assets/crtfd.png">crtfd.png</a></td></tr><tr><td>Flagged Public Key:</td><td>Fees are redistributed as Bounty awards.</td><td>Proof of wrong-doing required.</td><td><a href=".gitbook/assets/flagged2.png">flagged2.png</a></td></tr></tbody></table>

## ERC721 and deviations

To ensure the interoperability of Soulbound NFTs across different platforms and ecosystems, the Open Info movement has adopted the ERC-721 standard with soulbound deviations. ERC-721 is a widely used standard for non-fungible tokens on the Ethereum blockchain, and it provides a set of guidelines and rules for creating and managing NFTs.

{% hint style="info" %}
<mark style="color:blue;">Soulbound NFTs</mark> are irrefutable:

* they can always be openly verified on the blockchain.&#x20;
* They are unique and&#x20;
* cannot be duplicated or transferred.&#x20;
{% endhint %}

The deviations from the ERC-721 standard are the owner's inability to transfer or burn the token from their address. The Open Info Custodian reserves the sole right to approve the minting or burning of any certified or flagged address. Users reserve the right to mint Verified for only themselves given they have linked a social account.&#x20;

### Modified ERC721 Functions:

#### safeMint

`safeMint` is a public write function that allows users to mint a new OI-verified SNFT, given that they have registered accordingly. In the case of certified or flagged SNFTs, only the contract owner may call this function. The function increments the `_tokenIdCounter` and emits a `Mint` event when the token is minted.&#x20;

#### safeMintMultiple

`safeMintMultiple` is a public function that allows the contract owner to mint multiple OI-verified tokens at once. The function increments the `_tokenIdCounter` for each token and emits a `Mint` event for each token that is minted.

#### revoke AKA burn

`revoke` AKA `burn` is a public write function that allows only the contract owner to burn an OI-verified, certified,  or flagged token. This function transfers the token from the owner's account to the zero address. It is acceptable to burn any given Soulbound NFT only under the following conditions.

1. It was successfully proven through a dispute claim that the given address was falsely flagged.&#x20;
2. The current terms under which the original Soulbound NFT was minted are no longer valid.
3. Under the owner's request to de-register.

### Unique SNFT Functions

#### beforeTokenTransfer

The `beforeTokenTransfer` function is called before any attempt to transfer a token. This function always fails if the sender is not equal to the zero address, which Soulbounds the token to its receiver. If the receiver is equal to the zero address (a burn attempt) the function only passes if it is called by the Open Info Custodian.

## Usecase

The use case for Soulbound NFTs is broad and includes areas such as education, finance, healthcare, and politics. For example, a university might use Soulbound NFTs to verify the completion of a degree program, ensuring that the information is accurate and trustworthy. Similarly, a bank might use Soulbound NFTs to verify the identity of its customers, preventing fraud and money laundering.

Open Info verifies individuals, organizations, and businesses that have met specific criteria and have proven healthy interactions with other addresses. The verification criteria include but are not limited to, proof of the following.

1. An active social account.
2. Successful delivery of goods or services.
3. Full KYC.

Open Info also tracks and monitors individuals or organizations through their perceived reputation. Those that have been (inter)acting maliciously, are flagged. Once an address is flagged with the Soulbound NFT, it cannot get rid of it. Additionally, users can second any given SNFT through a voting system, adding to the validity of the claim and a measurable weight to the classification.

## Metadata

By using the ERC-721 standard, Soulbound NFTs can also be easily integrated with other applications and platforms that support ERC-721 tokens, expanding their usefulness and potential applications.&#x20;

The standard metadata JSON for an Open Info Verified, Certified or Flagged Soulbound NFT:

```json
{
  "image": "https://vrfd.info/[ADDRESS]",
  "external_url": "https://vrfd.info/[ADDRESS]",
  "name": "[ADDRESS || ENS-DOMAIN].VRFD",
  "description": "[ADDRESS] has been [verified || flagged] by Open-Info, with a Souldbound-NFT.",
  "Attributes": [
    {
      "trait_type": "VRFD?",
      "value": "['VRFD 🗸' || 'CRTFD $' || 'FLAGGED X']"
    },
    {
      "trait_type": "upvotes",
      "value": "22"
    },
    {
      "trait_type": "downvotes",
      "value": "12"
    },
    {
      "trait_type": "Reported By",
      "value": "[ADDRESS]"
    }
  ]
}
```

## Source

\[1] See the [Git repository](https://github.com/Open-Info/Soulbound-NFTs) containing the source code of the smart contracts used by Open Info.

