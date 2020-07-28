# Workflow 3: User is authenticated on network participant or is signing-up on network participant
### Advertiser side: user is signing-up on network participant
Suppose a user is a regular browser of my-localstore.com, and is creating an account on this website. This workflow is integrated with the existing authentication on the website (either their own and/or an SSO).

During the sign-up process on my-localstore.com, the user gets a prompt to accept personalized advertising with my-advertising-services.com program (sketch name for the website operated by the Network Controller).

The prompt clearly states that:
* user interest data can be collected to perform personalized advertising,
* ad preferences can be updated at any time,
* user may leave the program at any time.

The user chooses to join the program. An IFA linked to the user email address is created and stored by the Network Controller. This IFA is passed to my-localstore.com's DSP, which can collect user interest data linked to this IFA.

![workflow_3_adv](https://user-images.githubusercontent.com/4519242/88651823-6124e300-d0ca-11ea-8032-ed1ce92d2dfc.png)

### Publisher side: user is already authenticated on network participant
The user goes to my-news.com, and has already an account on this website.

The user being already signed on my-news.com, my-news.com sends a request to the Network Controller, asking whether the user has already joined my-advertising-services.com. 

Answer is yes and the user gets a prompt asking whether she authorizes user interest data collection and personalized advertising from my-advertising-services.com on my-news.com.

The user chooses to agree, and the IFA linked to the user email address that is shared by the Network Controller to my-news.com.

my-news.com can pass this identifier to advertisers through ad bid request, enabling personalized advertising based on user interest on its property.

![workflow_3_pub](https://user-images.githubusercontent.com/4519242/88651836-65510080-d0ca-11ea-8d86-fcb6813ac12c.png)
