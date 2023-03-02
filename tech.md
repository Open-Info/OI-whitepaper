---
description: Irrefutable source of truth.
---

# 👾 Soulbound NFTs

## The benefits

The Soulbound non-fungible token (NFT) is a **unique** digital asset that is used by the Open Information movement for certification, verifying information, and flagging malicious actors. It is a specialized type of NFT that is designed to be tamper-proof and resistant to forgery, making it ideal for use in situations where trust and verification are critical.

## `ERC-721` and deviations

To ensure the interoperability of Soulbound NFTs across different platforms and ecosystems, the Open Information movement has adopted the ERC-721 standard with soulbound deviations. ERC-721 is a widely used standard for non-fungible tokens on the Ethereum blockchain, and it provides a set of guidelines and rules for creating and managing NFTs.

{% hint style="info" %}
<mark style="color:blue;">Soulbound NFTs</mark> are irrefutable:

* they can always be openly verified on the blockchain.&#x20;
* They are unique and&#x20;
* cannot be duplicated or transferred.&#x20;
{% endhint %}

The deviations from the ERC-721 standard are the owner's inability to transfer or burn the token from their address. Open Information reserves the sole right to approve the minting or burning of any given address. The contract owner is referred to here as the Open Information Custodian. The following standard ERC-721 functions have been changed to only be callable by the Open Information Custodian:

#### safeMint & safeMintMultiple

`safeMint` is a public write function that allows only the contract owner to mint a new OI-verified/flagged token. The function increments the `_tokenIdCounter` and emits a `Mint` event when the token is minted. `safeMintMultiple` is a public function that allows the contract owner to mint multiple OI-verified tokens at once. The function increments the `_tokenIdCounter` for each token and emits a `Mint` event for each token that is minted.

#### revoke AKA burn

`revoke` AKA `burn` is a public write function that allows only the contract owner to burn an OI-verified/flagged token. This function removes the token from the owner's account. It is acceptable to burn a given Soulbound NFT only under the following conditions.

1. After a dispute, it was successfully proven that the given address was misclassified.&#x20;
2. The current terms under which the original Soulbound NFT was minted are no longer valid.
3. The user requested their current information be redacted for ethical reasons.

## Usecase

The use case for Soulbound NFTs is broad and includes areas such as education, finance, healthcare, and politics. For example, a university might use Soulbound NFTs to verify the completion of a degree program, ensuring that the information is accurate and trustworthy. Similarly, a bank might use Soulbound NFTs to verify the identity of its customers, preventing fraud and money laundering.

Open Info verifies individuals, organizations, and businesses that have met specific criteria and have proven healthy interactions with other addresses. The verification criteria include, but is not limited to, the following checks

1. A social account.
2. Successful delivery of goods or services.
3. Full KYC.

Open Info also tracks and monitors individuals or organizations through their perceived reputation. Those that have been (inter)acting maliciously, are flagged. Once an address is flagged with the Soulbound NFT, it cannot get rid of it. Additionally, users can second any given verification or flag, adding to the validity of the claim.

## Metadata

By using the ERC-721 standard, Soulbound NFTs can also be easily integrated with other applications and platforms that support ERC-721 tokens, expanding their usefulness and potential applications.&#x20;

The standard metadata JSON for an Open Information Verified or Flagged Soulbound NFT:

```json
{
  "image": "https://vrfd.info/[ADDRESS]",
  "external_url": "https://vrfd.info/[ADDRESS]",
  "name": "[ADDRESS || ENS-DOMAIN].VRFD",
  "description": "[ADDRESS] has been [verified || flagged] by Open-Info, with a Souldbound-NFT.",
  "Attributes": [
    {
      "trait_type": "VRFD?",
      "value": "['VRFD 🗸' || 'FLAGGED X']"
    },
    {
      "trait_type": "upvotes",
      "value": "22"
    },
    {
      "trait_type": "downvotes",
      "value": "12"
    }
  ]
}
```

## Source

\[1] See the [Git repository](https://github.com/Open-Info/Soulbound-NFTs) containing the source code of the smart contracts used by Open Information

