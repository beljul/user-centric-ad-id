# Workflow #1: user is not authenticated on network participant and is not authenticated on the Network Controller
### Advertiser side
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

### Publisher side
The user goes to my-news.com where he does not have an account either. Similarly to the user experience on my-localstore.com, my-news.com displays to the user a widget asking her whether she would be interested in getting personalized ads as part of my-advertising-services program. The widget is freely positioned by the publisher on its website.

If the user clicks on it, then the user is redirected through a pop-up towards my-advertising-services.com where he is asked in a prompt to consent to personalized advertising on my-news.com.

If the user accepts, then a first-party cookie with the IFA is created and stored by the Network Controller in the user's browser (or retrieved if the user already went through this workflow with another network participant). This IFA is also passed to my-news.com, which can pass this identifier to the advertising value chain through ad bid request, enabling personalized advertising based on user interest on its property (for example, from my_localstore.com). The storage in a first-party cookie is the most immediate way to move forward but we can imagine other storage solutions in the future (e.g. storage by the browser).

![workflow_1_pub](https://user-images.githubusercontent.com/4519242/88651749-4ce0e600-d0ca-11ea-8a20-71745a50b6ca.png)
