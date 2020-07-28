# Workflow 2: User is not authenticated on network participant and is authenticated on the Network Controller
### Advertiser side
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

### Publisher side
The user goes to my-news.com where he does not have an account either. Similarly to the user experience on my-localstore.com, my-news.com displays to the user a widget asking her whether she would be interested in getting personalized ads as part of my-advertising-services program. The widget is freely positioned by the publisher on its website.

If the user clicks on it, then the user is redirected through a pop-up towards my-advertising-services.com where he is asked in a prompt to consent to personalized advertising on my-news.com.

If the user accepts, then the IFA associated with her Network Controller profile is retrieved. This IFA is also passed to my-news.com, which can pass this identifier to the advertising value chain through ad bid request, enabling personalized advertising based on user interest on its property (for example, from my_localstore.com).

![workflow_2_pub](https://user-images.githubusercontent.com/4519242/88651787-5702e480-d0ca-11ea-8da0-1e61a7d4748c.png)
