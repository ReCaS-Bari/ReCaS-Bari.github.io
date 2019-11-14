# Welcome to ReCaS-Bari

## EGI Federated Cloud

ReCaS-Bari cloud site is fully integrated in the EGI Federated Cloud. 
The user access is regulated by SLAs/OLAs.

If your virtual organization has a valid SLA with our site, you will be able to access our Openstack cloud services as follows.

## Dashboard access

Point your browser to [http://cloud.recas.ba.infn.it](http://cloud.recas.ba.infn.it)

1. choose the OpenID Connect authentication method
   ![OpenID Connect Authentication](/images/choose_auth_method.png)

2. select the EGI-Checkin IdP
   ![EGI AAI IdP](/images/select_idp.png)

You will be redirected to your organization project.

### CLI access

The OpenStack Client has built-in support for using OpenID Connect Access Tokens to authenticate. 

First get a valid token from [EGI Check-in](https://aai.egi.eu/fedcloud/):

Copy the `curl` command provided in the form to generate the access token as shown in the screenshot below:

![](/images/get_egi_token.png)

Paste the command in a terminal and launch it. You will get an output similar to the following:

```markdown
{
    "access_token": "eyJraWQiOiJvaWRjIiwiYWxnIjoiUlMyN........",
    "expires_in": 3599,
    "id_token": "eyJraWQiOiJvaWRjIiwiYWxnIj........",
    "refresh_token": "************",
    "scope": "openid profile email",
    "token_type": "Bearer"
}
```

Then copy-paste the "access_token" field value and use it in a command like:
```markdown
$ openstack --os-auth-url https://cloud.recas.ba.infn.it:5000/v3 --os-auth-type v3oidcaccesstoken --os-protocol oidc --os-identity-provider egi.eu --os-access-token "eyJraWQiOiJvaWRjIiwiYWxnIjoiUlMyN........" token issue
+---------+----------------------------------+
| Field   | Value                            |
+---------+----------------------------------+
| expires | 2019-11-14T11:51:38+0000         |
| id      | c83f70e772294dca9778a4f6224c034a |
| user_id | b80cbdb04ade43b29da0a65855a8ed2a |
+---------+----------------------------------+
```

## Support or Contact

Check out our [site](https://www.recas-bari.it/index.php/en/) or [contact support](mailto:support@recas-bari.it) 
