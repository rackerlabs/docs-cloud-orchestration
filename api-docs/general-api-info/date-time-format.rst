================
Date/Time format
================

The Cloud Orchestration Service uses an ISO-8601 compliant date format
for the display and consumption of date/time values.

The system timezone is in UTC. MySQL converts TIMESTAMP values from the
current time zone to UTC for storage, and back from UTC to the current
time zone for retrieval. This does not occur for other types, such as
DATETIME.

**Example: Cloud Orchestration Service Date/Time Format**

.. code::

    yyyy-MM-dd'T'HH:mm:ssZ

See the table below for a description of the date/time format codes.

May 19th, 2011 at 8:07:08 AM, GMT-5 would have the following format:

.. code::

    2011-05-19T08:07:08-05:00

**Explanation of Date/Time Format Codes** 

+------+-----------------------------------------------------------+
| yyyy | Four digit year                                           |
+------+-----------------------------------------------------------+
| MM   | Two digit month                                           |
+------+-----------------------------------------------------------+
| DD   | Two digit day                                             |
+------+-----------------------------------------------------------+
| T    | Separator for date/time                                   |
+------+-----------------------------------------------------------+
| HH   | Two digit hour (00-23)                                    |
+------+-----------------------------------------------------------+
| mm   | Two digit minute                                          |
+------+-----------------------------------------------------------+
| ss   | Two digit second                                          |
+------+-----------------------------------------------------------+
| Z    | RFC 8601 timezone (offset from GMT). If Z is not replaced |
|      | with the offset from GMT, it indicates a 00:00 offset.    |
+------+-----------------------------------------------------------+





