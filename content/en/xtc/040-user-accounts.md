---
title: "User Accounts"

weight: 40
type: docs

description: >
    How to set up user accounts and SSO in XTC.
---

## Creating a User Account

To use Xceptance Test Center, you need a user account. You can easily sign up on https://xtc.xceptance.com/. You will be prompted to enter your name, mail address and password.

After the successful registration, XTC will send you an email to the given address, asking you to confirm the registration. You will be able to log in to XTC as soon as you confirmed.

Currently, your role and projects will be assigned by Xceptance. This will change in the future.

### Sign Up Using an External Provider

XTC supports authenticating users using their Google or Microsoft accounts. This allows users to use their existing Single-Sign-On accounts without having to remember additional login credentials.

To sign up with your Google or Microsoft account click on the appropriate button in the registration form. This will forward you to your preferred provider to log in.

{{< image src="xtc/registration-form.png" >}}
Registration form with buttons for external login providers
{{< /image >}}

{{% note %}}
Depending on whether you are already logged into your Google or Microsoft account, you may not see any indication of being redirected at all. The provider may redirect you back into XTC immediately without showing any login interface at all.
{{% /note %}}

Upon return XTC will continue the signup process by requesting additional information like your full name and email address. After confirming, you will receive a validation email to the given address to complete the signup, before your account can be activated.

{{< image src="xtc/registration-form-return.png" >}}
Registration details form pre-filled with data from the login provider
{{< /image >}}

{{% note %}}
The details form may already contain the details returned by your login provider. You are free to change those details. XTC will not use any of the supplied information to connect your XTC user to your external account. It will, however, use the supplied email address as your point-of-contact for any kind of notifications from the system (e.g. test results). Please refer to your organization's guidelines regarding the correct email address to use for this kind of data.
{{% /note %}}

{{% warning %}}
The supplied email address MUST be unique. DO NOT use shared addresses (e.g. mailing lists), because other users will be unable to register with the same address.
{{% /warning %}}

## Account Management

XTC enables you to manage your account information. After logging in, click your avatar on the right side of the header and go to _My Account_. 

The _My Account_ view contains two tabs: _Profile_ and _Login Data_. 

In **Profile** you may update your profile information such as your first and last name, your phone number (which may be useful for receiving [monitoring notifications]({{< relref "monitoring/440-scenario-setup#notifications" >}})), and you can also upload an avatar/profile picture.

In **Login Data** you can update your login data: to set a new e-mail address or password for your account, you need to enter the new data twice and confirm this with your current password. (If you are using an external provider for authentication, entering the password will not be necessary, and you will only be able to update your account's e-mail address.)

External login providers for this account will be listed here and if you want to switch from internal authentication to using an external provider, you can [connect your XTC account to an external login provider]({{< relref "#connecting-existing-xtc-accounts-to-an-external-login-provider" >}}) here.

### Connecting Existing XTC Accounts to an External Login Provider

If you already have an existing XTC account, you can connect it to an external login provider in order to use your existing Single-Sign-On account instead of previously defined XTC login credentials.

1. Click on your avatar in the top right corner and go to "My Account" > "Login Data".
2. Edit the "External Login Providers" section by clicking on the pen icon.
3. Select your preferred login provider via the appropriate button.

   {{< image src="xtc/switch-to-external-login.png" >}}
  UI to connect existing accounts to external providers. The user in the example is already connected to a Google account. Therefore the Google button is disabled.
   {{< /image >}}

   XTC will redirect you to your provider to complete the login process. Upon return your XTC account will be connected to your external provider.

{{% note %}}
Depending on whether you are already logged into your Google or Microsoft account, you may not see any indication of being redirected at all. The provider may redirect you back into XTC immediately without showing any login interface at all.
{{% /note %}}

{{% warning %}}
After connecting your account to an external login provider normal login via username and password is no longer possible. This action cannot be undone.
{{% /warning %}}

### Two-Factor Authentication (2FA)

It is possible to secure your XTC account not only with a regular password, but also with a second factor. Currently, XTC supports _time-based one-time passwords (TOTP)_ as the second factor. Use apps like Twilio Authy or Google Authenticator on your phone to generate such passwords. 2FA is optional at the moment, but we recommend that you set up 2FA for your account right now.

To enable 2FA for your XTC account, go to _My Account > Login Data_. In the section _Two-Factor Authentication_, click the button _Enable Two-Factor Authentication_ and follow the instructions to set up your preferred TOTP app on your phone. When this is done and you want to sign in to XTC again, you will first have to enter your regular password as usual, but afterwards you will now be prompted to enter the second factor, a one-time password. Use your TOTP app to generate that one for you.

If you later need to disable 2FA, simply click the button _Disable Two-Factor Authentication_ and confirm.

{{% note notitle %}}
Note that if you have bound your account to an [external login provider]({{< relref "#connecting-existing-xtc-accounts-to-an-external-login-provider" >}}) (currently Google or Microsoft), the section **Two-Factor Authentication** is not available in XTC as in this case 2FA is managed in the settings of your external account.
{{% /note %}}

## Login Using an External Provider

XTC supports authenticating users by login credentials as well as by using their Google or Microsoft accounts. Depending on whether your user account is set up to use SSO (see above for how this is done) you can log in using external login providers:

{{< image src="xtc/login-form.png" >}}
Login form with buttons for external login providers
{{< /image >}}

To log in using either your Google or Microsoft account click on the respective buttons in the login form. This will forward you to your login provider and perform authentication there.

{{% note %}}
Depending on whether you are already logged into your Google or Microsoft account, you may not see any indication of being redirected at all. The provider may redirect you back into XTC immediately without showing any login interface at all.
{{% /note %}}
