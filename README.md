# Zammad and 3CX Integration Template
Contact lookup and automatic ticket creation in Zammad from 3cx

## Requirements

This template works on 3cx 16.x. It won't work on 15.x.

## Setup

### On Zammad

First of all you need settings from Zammad. Log in with an administrator account (better *the* admin, so the token is bond to an user which
may leave your organization) and go to *Profile > Token Access* and create a new token with `admin.user` permission.

Then go to *Admin > Integrations > CTI (generic)*, enable the feature and copy the url of the CTI Endpoint.


### On 3cx

Go to *Advanced > Contacts > Options* and change the value of *Match Caller ID's to a contact entry* to *Match exactly*.

Then install the template by going to *Settings > CRM Integration*, and in the 
*Server Side* tab click on '+Add' button and attach the `zammad.xml` file. 
Then you will be taken to the integration configuration.

#### General configuration

* Zammad CTI Endpoint URL: paste the url obtained above from Zammad
* Zammad URL: base url of your Zammad installation
* Zammad API Token: the token generated above with the admin user

#### Enable call journaling

Enable this flag to generate tickets on Zammad from 3cx calls.

* Queue Name: ?

#### Enable Contact Creation

Enable this flag to automatically create contacts on Zammad for unknown customers.

* New Contact First Name: the name to use for the contact. It may be a variable (FIXME explain how to find them out) or a fixed string
* New Contact Last Name: as above


## Notes

For ReportCall event to work I had to make a callID using the incoming phone number and datetime obtained from HTTP Request from the following URL
`http://worldclockapi.com/api/json/utc/now` using this key `currentDateTime`. 
Then this callID can be reproduced by concatonating the incoming phone number with the `CallStartTimeUTC` from 3CX in the hangup/ReportCall request
