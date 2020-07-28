# User centric advertising network

## Introduction
Personalized advertising aims at fostering users' awareness of brands, products and services that match their interests in ways that cultivate positive engagement and brand recognition. By funding content providers and publishers, personalized advertising enables free access to a wide and varied array of content and services ranging from social media platforms to news, investigation journalism or weather forecasts. As of today, it is impractical for users to assess how the media they consume is brought to them and to what extent this consumption comes at odds or not with their privacy preferences. 

This proposal for a user-centric advertising network, adopts the viewpoint that users should benefit from a vast, open and mostly free internet ecosystem in ways that cater to their individual preferences in terms of level of personalized interactions they seek to enjoy online, from each of the businesses they engage with.

## Design Principles
We propose a design which grants full and easy control to the user to manage a revocable and editable privacy profile, with confidence their preferences are acted. upon.

Our thinking is guided by 3 acknowledgements : 
1/ As of today, online identity management is decentralized ; meaning each advertiser, publishers or tech vendor can create its own identity space, tying web browsing systems to anonymous identifiers. This fragmentation of identifiers generates friction with end users when it comes to personalized advertising, the users being unable to easily detach themselves from the array of identifiers that their web browsing could have been attached to nor are they able to get a perspective about their digital footprint. Fragmentation is creating obfuscation.
2/ Although the identifiers are decentralized ; these identifiers can be stitched together and lead to the creation of rich web browsing profiles. Privacy issues do not come from identifiers being leaked but do arise when personal information or information that can create harm to its owner is exposed. It's the data that counts not the identifier.
3/ There is no unique view of what constitutes privacy-safe browsing experience. Users preferences vary in the way each judge what is and what is not acceptable service. Users should be granted voice and choice about how they seek to enjoy their online activity.

With these in mind, the following principles guide our design:
* centralization of user privacy preferences: the users’ privacy profile should be cross-browser/device/environment/OS,
* separation of purpose: identifier used for advertising use should not be the same as ones used for other purposes (say as a login to B2C services),
* ubiquity for accessing & altering user preferences: users should be one click away to be able manage their preferences,
* transparency and auditability: users choices enforceability and respect should be ensured.


Several designs were studied to enforce those principles. Each comes with its own way of storing the user identifier and its own pros and cons:

| Design options  | Identifier storage location | Description | Pros | Cons |
|---|---|---|---|---|
| #1 (current state) | Decentralized | Identifier is collected, stored and shared by each advertiser/publisher/vendors and based on PII | <ul><li>Smooth user browsing experience</li></ul> | <ul><li>No centralization of user privacy preferences</li><li>No clear separation of purpose</li><li>Capacity to scale (PII-only)</li><li>Few auditability</li></ul> |
| #2 | Browser | Identifier is created, stored and shared by browsers which acts as brokers to publishers/advertisers/SSPs/DSPs | <ul><li>Centralization of user privacy preferences</li><li>Clear separation of purpose</li><li>Auditability</li><li>Smooth user browsing experience</li></ul> | <ul><li>None</li></ul> |
| #3 | Browser plugin | Identifier is created, stored and shared by a browser's plugin installed manually by the end user | <ul><li>Centralization of user privacy preferences</li><li>Clear separation of purpose</li><li>Smooth user browsing experience</li><li>Auditability</li></ul> | <ul><li>Capacity to scale (require plugin-install)</li></ul> |
| #4 | Identity providers | Identifier is created, stored and shared by Identity Providers and is linked to PII | <ul><li>Smooth user browsing experience</li><li>Clear separation of purpose</li><li>Auditability</li></ul> | <ul><li>Support required from all identity providers to manage an Identifier</li><li>Requirement for advertisers/publishers to adopt SSOs as login provider</li><li>Capacity to scale (PII-only)</li></ul> |
| #5 | Third-party entity | Identifier is created and stored by a third-party independent entity at user sign-up time or consent time. Identifier can be shared across advertisers, publishers and tech vendors upon user choice | <ul><li>Centralization of user privacy preferences</li><li>Ubiquity for accessing & altering user preferences</li><li>Clear separation of purpose</li><li>Auditability</li></ul> | <ul><li>Lesser user experience</li></ul> |

Options 1, 3 and 4 seem difficult to scale ; option 2, although most elegant, requires endorsement from browser vendors which is uncertain at present time. Therefore, we will detail option 5 in the following proposal.

## Proposal
We introduce:
* a revocable user identifier called Identifier For Advertising,
* a network of advertisers, publishers and ad tech companies (referred to as "the network" in the rest of this document),
* ad preferences,
* a central entity called Network Controller.

### Definitions

#### Identifier For Advertising (IFA)
The Identifier For Advertising is a unique identifier that represents the end user for network participants.

It's a pseudonymous identifier (UUID) which has a finite lifetime and which can be revoked at any time by the user.

#### Ad Preferences
Ad Preferences are a set of controls attached to the Identifier For Advertising to manage their consent both at global and granular levels.

The global level of controls enables/disables personalized advertising for the whole network.

Granular levels of controls can be offered to users, for instance enabling/disabling personalized advertising for categories of publishers/advertisers or specific ones.

#### Network Controller
The Network Controller is an independent entity.

End users can create an account on the Network Controller and access the following services :
* revoking IFA upon request,
* reviewing and updating their ad preferences, 
* providing a portal to review user data collected by Network participants (referred to as my-advertising-services.com below).

The Network Controller also provides the following services to network participants:
* enabling cross-domain user identification for advertising through the IFA if the ad preferences allow it,
* reading the ad preferences that apply to their website.

### User workflows
This section aims at describing user workflows on publishers and advertisers that are participants of the network to enable identity resolution and personalized advertising.

We define three different workflows based on the state of the user:
* the user is not authenticated on the network participant and is not authenticated on the Network Controller,
* the user is not authenticated on the network participant and is authenticated on the Network Controller,
* the user is authenticated on the network participant (and is or is not authenticated on the Network Controller).

Workflows differ from one another in terms of:
* user experience on advertiser/publisher websites,
* solution for the storage of IFA,
* communication between the advertiser/publisher and the Network controller.

| Workflow ID | User's state | IFA storage | First communication between network participant and network controller  |
|---|---|---|---|
| #1 | <ul><li>The user is not authenticated on the network participant</li><li>The user is not authenticated on the Network Controller</li></ul> | <ul><li>Network Participant:1st-party cookie</li><li>Network Controller: 1st-party cookie</li></ul> | Direct interaction from network participant to Network Controller through dedicated window on Network Controller's web domain (similar to SSO login) |
| #2 | <ul><li>The user is not authenticated on the network participant</li><li>The user is authenticated on the Network Controller</li></ul> | <ul><li>Network Participant: 1st-party cookie </li><li>Network Controller: server-side database</li></ul> | Direct interaction from network participant to Network Controller through dedicated window on Network Controller's web domain (similar to SSO login) |
| #3 | <ul><li>The user is already authenticated on the network participant or is signing-up on the network participant</li><li>The user is or is not authenticated on the Network Controller</li></ul> | <ul><li>Network Participant : 1st-party cookie</li><li>Network Controller: server-side database</li></ul> | Implicit HTTP call from network participant to Network Controller to retrieve IFA in exchange of encrypted PII |

Each network participant is free to choose which workflow(s) to implement on its website.

#### Description of each workflow

<details>
  <summary>Workflow #1: user is not authenticated on network participant and is not authenticated on the Network Controller</summary>

  <ins>Advertiser side</ins>:
  Suppose a user is a visitor of my-localstore.com, but choose not to have an account on this website or my-localstore.com doesn't require any authentication.

  When visiting my-localstore.com, the latter displays to the user a widget, freely positioned by the advertiser on its website, asking him whether he would be interested in getting personalized ads as part of my-advertising-services.com (sketch name for the website operated by the Network Controller). 

  If the user does not click on it, then the user continues visiting the website but will not get personalized ads from my-localstore.com.

  If the user clicks on it, then the user is redirected through a pop-up towards my-advertising-services.com where he is asked in a prompt to consent to personalized advertising from my-localstore.com.

  The prompt clearly states that:
  * user interest data can be collected to perform personalized advertising,
  * ad preferences can be updated at any time,
  * user may leave the program at any time.

  If the user accepts, then a first-party cookie with the IFA is created and stored by the Network Controller in the user's browser.

  This IFA is also passed to my-localstore.com, which can collect user interest data linked to this IFA. This provides to users a pseudonymous and temporary IFA relying on cookie lifetime.

  The storage in a first-party cookie is the most immediate way to move forward but we can imagine other storage solutions in the future (e.g. storage by the browser, cf. design options described above).

  ![workflow_1_adv_fix](https://user-images.githubusercontent.com/4519242/88676397-4b281a00-d0ec-11ea-99ba-97c948378821.png)

  <ins>Publisher side</ins>:
  The user goes to my-news.com where he does not have an account either. Similarly to the user experience on my-localstore.com, my-news.com displays to the user a widget asking her whether she would be interested in getting personalized ads as part of my-advertising-services program. The widget is freely positioned by the publisher on its website.

  If the user clicks on it, then the user is redirected through a pop-up towards my-advertising-services.com where he is asked in a prompt to consent to personalized advertising on my-news.com.

  If the user accepts, then a first-party cookie with the IFA is created and stored by the Network Controller in the user's browser (or retrieved if the user already went through this workflow with another network participant). This IFA is also passed to my-news.com, which can pass this identifier to the advertising value chain through ad bid request, enabling personalized advertising based on user interest on its property (for example, from my_localstore.com). The storage in a first-party cookie is the most immediate way to move forward but we can imagine other storage solutions in the future (e.g. storage by the browser).

  ![workflow_1_pub](https://user-images.githubusercontent.com/4519242/88651749-4ce0e600-d0ca-11ea-8a20-71745a50b6ca.png)
</details>

<details>
<summary>Workflow #2: user is not authenticated on network participant and is authenticated on the Network Controller</summary>
  
  <ins>Advertiser side</ins>:
  Suppose a user is a visitor of my-localstore.com, but choose not to have an account on this website or my-localstore.com doesn't require any authentication.

  When visiting my-localstore.com, the latter displays to the user a widget, freely positioned by the advertiser on its website, asking him whether he would be interested in getting personalized ads as part of my-advertising-services.com (sketch name for the website operated by the Network Controller). 

  If the user does not click on it, then the user continues visiting the website but will not get personalized ads from my-localstore.com.

  If the user clicks on it, then the user is redirected through a pop-up towards my-advertising-services.com where he is asked in a prompt to consent to personalized advertising from my-localstore.com.

  The prompt clearly states that:
  * user interest data can be collected to perform personalized advertising,
  * ad preferences can be updated at any time,
  * user may leave the program at any time.

  If the user accepts, then the IFA associated with her Network Controller profile is retrieved. The IFA is also passed to my-localstore.com, which can collect user interest data linked to this IFA.

  ![workflow_2_adv_fix](https://user-images.githubusercontent.com/4519242/88676405-4e230a80-d0ec-11ea-8588-9e9951058bf4.png)

  <ins>Publisher side</ins>:
  The user goes to my-news.com where he does not have an account either. Similarly to the user experience on my-localstore.com, my-news.com displays to the user a widget asking her whether she would be interested in getting personalized ads as part of my-advertising-services program. The widget is freely positioned by the publisher on its website.

  If the user clicks on it, then the user is redirected through a pop-up towards my-advertising-services.com where he is asked in a prompt to consent to personalized advertising on my-news.com.

  If the user accepts, then the IFA associated with her Network Controller profile is retrieved. This IFA is also passed to my-news.com, which can pass this identifier to the advertising value chain through ad bid request, enabling personalized advertising based on user interest on its property (for example, from my_localstore.com).

  ![workflow_2_pub](https://user-images.githubusercontent.com/4519242/88651787-5702e480-d0ca-11ea-8da0-1e61a7d4748c.png)
</details>

<details>
<summary>Workflow #3: user is authenticated on network participant or is signing-up on network participant</summary>
  
  <ins>Advertiser side</ins> (example here: user is signing-up on network participant):
  Suppose a user is a regular browser of my-localstore.com, and is creating an account on this website. This workflow is integrated with the existing authentication on the website (either their own and/or an SSO).

  During the sign-up process on my-localstore.com, the user gets a prompt to accept personalized advertising with my-advertising-services.com program (sketch name for the website operated by the Network Controller).

  The prompt clearly states that:
  * user interest data can be collected to perform personalized advertising,
  * ad preferences can be updated at any time,
  * user may leave the program at any time.

  The user chooses to join the program. An IFA linked to the user email address is created and stored by the Network Controller. This IFA is passed to my-localstore.com's DSP, which can collect user interest data linked to this IFA.

  ![workflow_3_adv](https://user-images.githubusercontent.com/4519242/88651823-6124e300-d0ca-11ea-8032-ed1ce92d2dfc.png)

  <ins>Publisher side</ins> (example here: user is already authenticated on network participant):
  The user goes to my-news.com, and has already an account on this website.

  The user being already signed on my-news.com, my-news.com sends a request to the Network Controller, asking whether the user has already joined my-advertising-services.com. 

  Answer is yes and the user gets a prompt asking whether she authorizes user interest data collection and personalized advertising from my-advertising-services.com on my-news.com.

  The user chooses to agree, and the IFA linked to the user email address that is shared by the Network Controller to my-news.com.

  my-news.com can pass this identifier to advertisers through ad bid request, enabling personalized advertising based on user interest on its property.

  ![workflow_3_pub](https://user-images.githubusercontent.com/4519242/88651836-65510080-d0ca-11ea-8d86-fcb6813ac12c.png)
</details>

#### Coexistence of workflows in the Network
Since each network participant is free to choose which workflow(s) to implement on its website, we foresee the coexistence of all those workflows in the Network. 

The following tab describes the capacity of two workflows to enable identity resolution between an advertiser and a publisher when the are implemented respectively on each one:
| Workflow ID | Advertiser | Publisher | ID controller | Personalized advertising |
|---|---|---|---|---|
| #1 | is authenticated and has consented | is authenticated and has consented | / | Enabled |
| #2 | is authenticated and has consented | is authenticated and has NOT consented  | /  | Disabled  |
| #3 | is authenticated and has NOT consented | is authenticated and has consented  | /  | Disabled  |
| #4 | is authenticated and has consented | has consented through redirection to ID controller  | is authenticated | Enabled  |
| #5 | is authenticated and has consented | has consented through redirection to ID controller | is NOT authenticated | Disabled |
| #6 | has consented through redirection to ID controller | is authenticated and has consented | is NOT authenticated | Disabled |
| #7 | has consented through redirection to ID controller | has consented through redirection to ID controller | is NOT authenticated | Enabled  |

### User consent, transparency and controls
Each network participant is responsible to collect the consent for user interest data collection and personalized advertising on their web domains. The network participant can choose at which rate the prompt to join the program should be displayed to the user, preventing user fatigue, or can even include an option "don't ask me again". Once a user has agreed to user interest data collection and personalized advertising on a network participant property, the consent is valid until revoked by that same user.

The network provides additional transparency to users on the portal my-advertising-services.com. In particular, users can review there at any time for which websites they have agreed to user interest data collection and personalized advertising. We can also imagine additional features on my-advertising-services.com, for instance the visualization of user interest data that has been collected by DSP participants under their IFA on the Network Controller website.

The network provides controls to the user via the portal my-advertising-services.com:
* users can choose independently for each network participant whether or not to agree to user interest data collection and personalized advertising. If the user does not consent, the IFA is not shared with the participant,
* users can withdraw their consent to specific websites or all of them on my-advertising-services.com,
* users can sever the link between their IFA and their email address on my-advertising-services.com, severing the link between their identity and any user interest data that has been collected.


## Benefits
Users, first and foremost, are in control of their advertising experience:
* user choice is enforced: consent is explicit, granular covering all users concerns (network websites, type of ads and type of content),
* users haveevisibility on their privacy profile, in a centralized manner for all network websites,
* users can revoke their IFA at any time, severing the link between their identity and interest data previously collected by all network participants,
* a consistent and transparent user experience where authentication & collection happens at the point of user interaction,
* users are in control of their IFA: Network participants will be prohibited to use an IFA for linking with other online user identities.

Publishers can optimize their inventory by monetizing access to their audience through personalized advertising:
* publishers increase their advertising revenue, by combining their own audience data with collected user interest data,
* publishers decide with whom they share the identifier among the SSPs of the network, enabling them to monetize their own user data (tied to a user login for instance), if they choose to, without risking data leakage,
* the management and collection of consent for each publisher is taken care of by the Network Controller, publishers can rely on their CMP to ensure user choices are effectively acted upon in the advertising value chain
* publishers can control whether or not to share an IFA for an ad placement, and choose which part of their inventory will benefit from the IFA or not.

Advertisers are able to engage with users in a personalized fashion:
* advertisers can target users based on their individual interest data and propose products people like,
* advertisers can manage ad frequency through all publishers within the network, preventing user fatigue,
* advertisers can get unified measurement at scale, enabling them to prevent fraud and deliver their advertising message with confidence within the network.

## About the Network Governance
The network should have a governance body, which could be an existing industry consortium or a newly created body.

This body should be in charge of defining the network policy:
* network participantship rules: access to participantship should not be open for advertisers or publishers operating website linked to sensitive information, or unsafe product categories,
* obligations of network participants: minimum level of user controls and transparency provided,

This body should be in charge of overseeing the Network Controller operation:
* the Network Controller is the keeper of the user IFA and ads preferences. It should be trusted by users and network participants,
* the Network Controller itself could be operated by companies like cloud providers,
* the Network Controller should be freely auditable.
