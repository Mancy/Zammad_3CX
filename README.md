# Zammad_3CX
Contact Lookup and Automatic creation in Zammad

To use this template goto your 3CX management console then from settings choose CRM Integration
from Server Side tab click on '+Add' button then attach the zammad.xml template then set your data.

The Zammad Ticket API Token can be issued from the user profile then "token access" then create an access token with sufficient permissions for search and user profile creation.

Don't forget to set this option in 3CX "Match Caller ID's to a contact entry" to "Match exactly"
from Advanced -> Contacts -> Options

For ReportCall event to work I had to make a callID using the incoming phone number and datetime obtained from HTTP Request from the following URL
```http://worldclockapi.com/api/json/utc/now``` using this key ```currentDateTime```
Then this callID can be reproduced by concatonating the incoming phone number with the ```CallStartTimeUTC``` from 3CX in the hangup/ReportCall request
