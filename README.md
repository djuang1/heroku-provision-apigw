#  Heroku add-on for Anypoint API Manager (Proof of Concept)

 Deploying a Mule Runtime into a Heroku Dyno is pretty easy with the [Deploy to Heroku](https://github.com/djuang1/mule-heroku-dyno) button. Heroku provides a flexible cloud platform as a service that allows developers to bundle their code, apps, add-ons, etc... into a single package that can be driven by a CI/CD pipeline. Unfortunately for Mule, there are licensing restrictions that make this a difficult model at the moment. But fear not, there are other ways where MuleSoft and Heroku are "Better Together".
 
 Instead of a running in a Dyno, what if Mule could act as an [Add-On](https://elements.heroku.com/addons/anypoint-api-gateway) and provide API Management capabilities through the click of a button? Leveraging the [Anypoint Platform APIs](https://anypoint.mulesoft.com/apiplatform/anypoint-platform/#/portals) and the [Heroku Partner API](https://devcenter.heroku.com/articles/platform-api-for-partners), this PoC is a working example of a Heroku Add-On that allows a developer to deploy an API Proxy for their Heroku app.
 
 In the diagram below, the developer will find the add-on in the catalog and either click a button or add the proxy using the CLI. Heroku will call a Provisioning API that calls the Anypoint Platform APIs. The API will create an asset in Exchange, add an API in API Manager from that asset, and then deploy the proxy to Runtime Manager. When the developer no longer needs the proxy, they can delete the add-on and the API will handle the teardown of all the added components.

 <img src="https://github.com/djuang1/djuang1.github.io/blob/master/img/heroku-provision-apigw/heroku-mule-apigw.png?raw=true"/>

 ## Code Examples

* Setup and teardown assets using the Anypoint Platform APIs
    * Exchange
    * API Manager
    * Runtime Manager
* Error Handling with APIKit and Try Scope
* Object Store to manage add-on state.
* Anypoint MQ for reliability and to handle asynchronous calls.
* HTTP Redirect URL and 302 Status.

