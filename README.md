# OSTicketSearch


Place these files directly into the scp folder and access directly.
You will need to be logged in to access search.

## UserSearch.php

System Design
This system was designed to deal with several key issues in using OSTicket within an MSP environment.

    Telephony integration for automatic contact lookup.
    Partial info lookup to speed up finding contacts.
    Quick ticket lists to reduce duplicate ticket creation by agents.

Search:
The system will search the Users Names and Organisation Names fields containing each word/part word entered into the search box
This allows Agents to search based on part of a name and part of a company name. (e.g. 'John Acme' would return 'John Smith' from 'Acme Corporation').
All words searched for must in the results.

Results:
Results will be displayed for all matches, use the 'Select' option to see ticket info for an individual result.

Ticket Info:
When a result is narrowed to a single entry, the system will display open user tickets, the last 5 closed user tickets, all open company tickets, 100 closed company tickets.
This provides an overview of the users current situation.

Telephone Number Lookup:
The system allows for a URL Variable based search on users telephone numbers.
http(s)://ticket.system.domain/scp/UserSearch.php?tel=01234567890
For GoIntegrator call events the tel variable should be set to: %Call\CallerContact\Tel%
Results are pulled from three fields, User Phone Number, User Notes, Organisation Phone Number.
The inclusion of 'User Notes' allows for users to be searched via multiple numbers. (e.g. Work Number, Work Mobile, Personal Mobile)

Data Updates:
When a result is narrowed to a single entry, Agents are able to update the following fields by clicking on them, User Phone, User Notes, Org Phone, Org Notes.

## TicketSearch.php

System Design
This system was designed to deal with several key issues in using OSTicket within an MSP environment.
This module is designed to provide full system ticket search capabilities based on an and/or search limited by dates and 1,000 result max to reduce SQL load.
This system searches the 'ThreadEntry' table on the 'body' field only. 
