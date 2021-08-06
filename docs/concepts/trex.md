---
sidebar_position: 3
---

# Application : T-REX tokens

## The T-REX Token Standard

The main goal of the T-REX standard is to create a set of global tools, fully based on blockchain technologies, to allow frictionless and compliant issuance and use of tokenized securities on a peer to peer basis or through marketplaces. Whilst in full compliance with regulations and issuers requirements, embedding, controls, and mechanisms in the tokens themselves. With T-REX, we are implementing a “Compliance by Design” approach where it is simply impossible for an investor to buy a security without being compliant. The regulator itself can verify the compliance of the Issuer through the auditing of the smart contracts that support the Security Token life cycle.

The management of compliant transactions through T-REX backed permission tokens will be based on 3 main pillars creating a decentralized Validator: 

- OnchainID, a blockchain-based identity management system, allowing the creation of a globally accessible identity for every stakeholder. 
- A set of claims, as described in the [ERC-734](https://github.com/ethereum/EIPs/issues/734) and 
[ERC-735](https://github.com/ethereum/EIPs/issues/735) standards.
- A transfer manager whose role is to act as a filter of all the transactions of tokenized securities and which will check the claims of the stakeholders, and essentially it will check that the receiver has the rights to receive the tokens following the specific compliance rules and issuer requirements applicable for this specific asset. The transfer manager will block the transaction if the receiver misses a mandatory claim and will notify him about the failure causes. 

These 3 key elements allow issuers to use a decentralized Validator to control transfers and enforce compliance on the holders of the security token he has issued. The Validator includes rules for the whole offering (e.g. managing the max number of holders allowed in a specific market, when such rule apply), and rules for each investor (e.g. KYC or issuer-defined eligibility criteria) thanks to the identity management system.

## Constraints for Tokenized Securities

Although so far, the rules applicable to issuing and holding utility tokens were largely undefined - or at least very vague - in most countries, an STO consists in the issuance of a security that uses the blockchain technology as its registry, proof of ownership and transfer infrastructure. Such an instrument is regulated in every country and, as a consequence, STOs have to comply with the related regulations of the country where the security token is issued as well as those of the countries where it is distributed (sold). 

Characteristics | Utility Token | Security Token
:---: | :---: | :---:
Purpose | Usage | Investment
Regulation | Non existing or vague in most cases | Stringent as existing securities laws should be taken as reference
Lifecycle | Simple | As complex as a security
Secondary Market | Nearly no constraints | As complex as a security

Another significant difference between ICOs and STOs is related to the token lifecycle. ICOs - dealing with utility tokens - result in the
issuance of tokens having a relatively simple life cycle: once the token is shared among a decentralized network, its governance is mostly 
the results of its token economics. As to security tokens, it is quite different, as the issuer - or its appointed agent - generally remains liable for applying a number of controls to his token after issuance and during the entire “life” of its security token. In 
addition, he might need to apply a number of corporate actions (dividend/interests payments, … ) or corporate events (calling for an 
AGM/EGM, …) to its token which further increase the need for the issuer to keep in touch with (keep some control on) the investors in his 
token.

One could identify two main types of control requirements related to the issuance, the holding and the transfer of security tokens:
- One relates to regulations applicable to the security considered, that are independent of the security token itself (i.e. general rules). For example, the need to identify the investor, to collect a proof of his identity, to check his name against blacklists, i.e. generally speaking, control requirements related to AML/KYC, or other applicable regulatory rules.
- Then some controls might be explicitly related to the security that is issued, for example, restrictions about the investor type and 
location or about the amount of money that can be invested in a certain period. These might be linked to the regulatory environment under 
which the issuer has decided to issue his token or simply linked to eligibility criteria defined by the issuer for instance, for 
commercial reasons (e.g. restricting the access of a certain share class, having specific fees characteristics, to investors of a specific 
country).

Addressing these different control requirements will require a high level of reusability and flexibility when designing the token. 
The T-REX standard has been developed for this reason. It  provides a set of generic tools helping token issuers to apply and manage the 
necessary controls and permissions to security tokens through a flexible, decentralized validation system (the transfer manager), allowing 
them to add all the rules that need to be addressed to approve holding and transacting in their tokens.

## Necessity of Permissioned Tokens

All the experts of the sector agree on the point that only permissioned tokens are suitable to issue security tokens because there cannot be a total, uncontrolled, freedom of the transaction in such instruments and, investors need to comply with a number of criteria- either by regulation or imposed by the issuer himself in order to be eligible for holding the tokens. The main technical difference between standard [ERC-20](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-20.md) tokens and T-REX permissioned tokens resides in the transfer function of T-REX tokens being made conditional,  the condition for a transaction to be executed is that the transfer manager approves it according to the governance criteria defined for the token in question. However, despite this modification of the transfer function of the token, it is to be highlighted that, as the token structure is ERC-20 based, it remains fully compatible with it and all the available exchanges and tools based on ERC-20 tokens. 

Most of the “Security token protocols” promoted in the industry so far are permissioned tokens. The transfer function is modified and requests a transfer approval from an external validator service to control the transfer of tokens. 
T-REX involves an on-chain identity management system (OnchainID), allowing issuers to control the transfer of ownership directly on-chain.

### On-chain identity management

As mentioned before, by essence, a security token being subject to stringent governance, its distribution has to follow all the applicable regulations and, in particular, those aspects related to KYC rules. In that respect, we believe that identity management is key to implement such compliance on the blockchain.

As the ownership of a security token is registered on the blockchain, it is necessary to have a way to track the token ownership and to prohibit illicit transactions directly on the blockchain. This is why there is a need to make a link between wallet addresses and identities and to manage rights through an identity contract directly on the blockchain. In addition, it is also needed to ensure the privacy of those identities to comply with personal data related regulation. For this reason, personal data should not be stored directly on the blockchain but only the validation certificates (claims) issued by trusted third parties (KYC provider, government, lawyer,…) having checked these data. Those certificates (claims), stored in the identities of parties to a transaction will be used by the transfer manager to validate whether those parties are held and transact a specific security token, or not.

Linking an investor's wallet and his identity can bring significant added value to stakeholders in the nascent security tokens market. For example, it will allow a token issuer to replace the tokens of an investor if the investor loses access to his wallet (which happens pretty often and generally results in the loss of the owner's assets ), by verifying that his on-chain identity fits with off-chain data linked to the identity contract corresponding to the lost wallet. After the identity of the investor is confirmed, the issuer can burn the lost tokens and mint new tokens on the new wallet of the investor.

Also, on-chain identities and the certificates (claims) they store can potentially be re-used for passing KYC's for other security tokens than the one for which those claims were originally provided or even for other purposes than investments (e.g. account opening at an exchange, identification with compatible web services, …). If Google and Facebook accounts are the identities of most people on the internet of information, OnchainID's on-chain identities can be the ones of the internet of value. They are owned and controlled by their owner.