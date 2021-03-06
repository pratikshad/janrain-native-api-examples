Native API Examples
===================

Janrain's OAuth registration and authentication API endpoints have picked up the
nickname "Native API" since they were designed for use within *native* desktop
and mobile appliactions.

Using the Native API for web applications can offer a greater degree of control
over the user registration and authentication flows at the cost of the
convenience and simplicity of the
[Registration Javascript "widget"](http://developers.janrain.com/overview/registration/registration-overview/javascript-based-solution-for-websites/) .

All examples are written in PHP.


Contents
--------

* [Prerequisites](#user-content-prerequisites)
* [Getting Started](#user-content-getting-started)
* [Examples](#user-content-examples)
    * [Social Registration](#user-content-social-registration)
    * [Social Sign In](#user-content-social-sign-in)
    * [Traditional Registration](#user-content-traditional-registration)
    * [Traditional Sign In](#user-content-traditional-sign-in)
    * [Social Merge Accounts](#user-content-social-merge-accounts)
    * [Traditional Merge Accounts](#user-content-traditional-merge-accounts)
    * [Account Linking](#user-content-account-linking)
    * [Edit Profile](#user-content-edit-profile)
    * [Forgot Password](#user-content-forgot-password)
    * [Verify Email](#user-content-verify-email)


Prerequisites
-------------

* Janrain Social Login (aka Engage) application
* Janrain Registration (aka Capture) application
* PHP web server or local environment (eg. LAMP,
  [MAMP](https://www.mamp.info/en/), [WAMP](http://www.wampserver.com/en/), etc.)


Getting Started
---------------

1. Create a new Janrain *Login* API client using the
   [`/clients/add`](http://developers.janrain.com/rest-api/methods/api-client-configuration/clients/add-3/)
   API call:

        curl -X POST \
        -d client_id=APPLICATION_OWNER_CLIENT_ID \
        -d client_secret=APPLICATION_OWNER_CLIENT_SECRET \
        -d description='Native API examples login client' \
        -d features='["login_client"]' \
        https://YOUR_APP.janraincapture.com/clients/add

2. Add the `default_flow_name` setting to the login client you created in step
   1 (The flow name is usually "standard" but check with your Janrain
   representative if in doubt):

        curl -X POST \
        -d client_id=APPLICATION_OWNER_CLIENT_ID \
        -d client_secret=APPLICATION_OWNER_CLIENT_SECRET \
        -d for_client_id=LOGIN_CLIENT_ID_FROM_STEP_1 \
        -d key=default_flow_name \
        -d value=standard \
        https://YOUR_APP.janraincapture.com/settings/set

3. Add the `default_flow_version` setting to the login client you created in
   in step 1 (The flow version must be provided by your Janrain representative):

        curl -X POST \
        -d client_id=APPLICATION_OWNER_CLIENT_ID \
        -d client_secret=APPLICATION_OWNER_CLIENT_SECRET \
        -d for_client_id=LOGIN_CLIENT_ID_FROM_STEP_1 \
        -d key=default_flow_version \
        -d value=497f2277-a8ca-418e-a6dd-e7d30fabe7df \
        https://YOUR_APP.janraincapture.com/settings/set

4. [Download the source code](https://github.com/JanrainMicah/janrain-native-api-examples/archive/master.zip)
   or fork and clone this repository.

5. Unzip the files into your web server root. For example:

        unzip janrain-native-api-examples-master.zip -d /var/www

6. Rename `config.example.php` to `config.php`.

7. Add the client ID and secret for login client you created in step 1 to the
   `config.php` file:

        define('JANRAIN_LOGIN_CLIENT_ID', 'Your client ID goes here');
        define('JANRAIN_LOGIN_CLIENT_SECRET', 'Your client secret goes here');

8. Navigate to the examples folder in your web browser. Eg.
   [`http://localhost/janrain-native-api-examples-master/`](http://localhost/janrain-native-api-examples-master/)


Examples
--------

### Social Registration

Social Registration consists of a new user authenticating with an identity
provider (Facebook, Google, etc.) as the first step in a 2-step process to
register a new account. Janrain handles the interaction between the end-user
and the identity provider using the appropriate protocol
(OAuth 2.0/OpenID/SAML 2.0) to authenticate the user and obtain user data.


The second step is a registration form which ensures required data fields are
collected from the user. The *User Data* can be used to pre-populate the
registration form.

![Social Registration Sequence Diagram](https://raw.githubusercontent.com/JanrainMicah/janrain-native-api-examples/master/img/social-registration-sequence.png)

**Reference Documentation**

* [/oauth/auth_native](http://developers.janrain.com/rest-api/methods/authentication/oauth/auth_native/)
* [/oauth/register_native/](http://developers.janrain.com/rest-api/methods/authentication/oauth/register_native/)


### Social Sign In


### Traditional Registration


### Traditional Sign In


### Social Merge Accounts


### Traditional Merge Accounts


### Account Linking


### Edit Profile


### Forgot Password


### Verify Email

