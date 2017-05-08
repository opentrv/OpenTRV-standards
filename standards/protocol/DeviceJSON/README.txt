Describes lightweight/compact JSON format used in OpenTRV devices.

One such use is in the JSON portion of an 'O' frame.

Informally, see below example.

[ "2016-02-18T10:45:40Z", "", {"@":"414a","+":2,"L":130,"vC|%":1158,"T|C16":255} ]
[ "2016-02-18T10:46:10Z", "", {"@":"2d1a","+":4,"L":78,"T|C16":326,"O":2,"vac|h":0} ]
[ "2016-02-18T10:46:13Z", "", {"@":"0d49","+":4,"L":238,"T|C16":265,"O":1,"vac|h":2} ]
[ "2016-02-18T10:46:59Z", "", {"@":"b6d9","+":7,"L":177,"T|C16":298,"H|%":67,"O":1} ]
[ "2016-02-18T10:48:25Z", "", {"@":"819c","T|C16":80,"L":223,"B|cV":251} ]
[ "2016-02-18T10:49:13Z", "", {"@":"0d49","+":5,"B|cV":259,"L":238,"v|%":0,"tT|C":6} ]
[ "2016-02-18T10:49:37Z", "", {"@":"414a","+":3,"O":1,"vac|h":2,"B|cV":257,"L":135} ]
[ "2016-02-18T10:50:52Z", "", {"@":"3015","+":4,"T|C16":295,"v|%":0,"tT|C":17} ]
[ "2016-02-18T10:50:53Z", "", {"@":"0a45","+":5,"tT|C":16,"vC|%":2322,"T|C16":283} ]
[ "2016-02-18T10:52:25Z", "", {"@":"819c","T|C16":80,"L":234,"B|cV":251} ]

This log file is a series of lines, each a JSON array,
of which the first field is a UTC timestamp
and the third is the JSON object as sent by the remote device (eg valve or sensor).
Almost all values are integer, a few are string.

The general format is x|u where x is the name and u are the UCUM units.
Non-UCUM units are used in some very common cases for brevity/clarity.
Units are omitted entirely where not applicable eg device is uncalibrated.

Meaning of the various JSON fields in there, ie common ones:

L     light level 0--255 (uncalibrated)
vC|%  valve movement Cumulative | %
T|C16 (room) temperature | Celsius * 16 (ie 16ths of a degree C)
O     Occupancy (0 unknown, 1 vacant, 2 possibly occupied, 3 defintiely occupied)
vac|h vacancy time | hours
H|%   relative Humidity | %
B|cV  battery voltage | centiVolts
v|%   valve-open | %
tT|C  target room temperature | Celsius

"@"   Node ID prefix in hex
"+"   frame sequence number