# Zammad_3CX
Contact Lookup and Automatic creation in Zammad
To use this template goto your 3CX management console then from settings choose CRM Integration
from Server Side tab click on '+Add' button then attach the zammad.xml template then set your data.

Don't forget to set this option in 3CX "Match Caller ID's to a contact entry" to "Match exactly"
from Advanced -> Contacts -> Options

Currently the ReportCall event is not working because 3CX must send unique callid in both Contact lookup and Report Call events, to be accepted by Zammad CTI
