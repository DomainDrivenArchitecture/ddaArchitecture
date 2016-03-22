# Log Handling

## Location of logging messages
Log-Messages are generated for Exceptions or important point of controll flow. Exceptions are logged in the client system or on system borders.

## Definition of Log Levels
* FATAL: An exception is FATAL if the system is unable to continue working. The application terminates. Audience of Fatal messages are support staff and developers.
* ERROR: An exception is ERROR, if the system needs to cancel a domain transaction. Affected Transactions are rolled back. Audience of Error messages are support staff and developers.
* INFO: INFO referred information on the beginning, end, and important elements of domain transactions. Audience of info messages are support staff and developers.
* DEBUG: DEBUG means information that is relevant to the entry or end of important methods. Audience of debug messages are developers.
* TRACE: TRACE means information that is relevant to the entry or end of any methods. Audience of trace messages are developers.    