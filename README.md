# ukTides
Slack /app to retrieve UK tides

Code a simple and free Slack app for use in the BSAC 67 workspace.

A slash command that will accept tide parameters from a message line, retrieve the tide information from a UK Admiralty api (which I subscribe to)  and format it into a simple table shown in the message.

Command should be:

/tides [location] [day | date]

Returns:

Location, day, date
Time  Height
HH:MM 9.99m
HH:MM 9.99m
HH:MM 9.99m
HH:MM 9.99m


(3-6 lines of table)

Valid [Locations] are held in a table (607 of them), if [Location] not given then default to “Aberdeen”.  Not case sensitive ABERDEEN == Aberdeen == aberdeen

[day] is day of week or abbreviation {today, sat, sun, mon, tue, wed, thur, fri, saturday, sunday …] not case sensitive.  Code translates day to a date in the range today to next 6 days.  Defaults to today if day or date not given.

[date] in YYYY-MM-DD format. Valid range is today to today+364 days

So

/tides == /tides Aberdeen today
/tides sunday == /tides Aberdeen [date of next Sunday]
/tides peterhead == /tides peterhead today
/tides 2022-03-11 == /tides aberdeen 2022-03-11

Etc.  

I can code this part if you can show me where in the module to code.

Slash command takes command line input and if it can’t be resolved to valid parameters then reports an error “sorry I didn’t understand that or the location you used is invalid, use /tides [location] [sat, sun... | YYYY-MM-DD] 

If command line input can be resolved into a valid location and date then app calls UK Admiralty API to retrieve tide information for that location and day in JSON format.  Waiting message is displayed while call being made, error code and message  from api shown if call fails.

App formats the retrieved data as a table in the message line which can then be sent in thread or new message.

I can provide a table of locations (for validation and decode for api call).

I can provide JS code for admiralty api call (url format and header keys).

App must make use of free services if possible.  

I can code much of the logic but I am really stuck with the creation of the Slack app;

How to use slack manifests for the app
Use of URLs for slack call validation
How/where to run listener code external to slack
How to complete app (all attempts have resulted in apps which Slack thinks are still “work in progress”)



