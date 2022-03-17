# Create Tehran TZ in Linux 2022

### Time Zone Database (TZ Database)

You can download the latest time zone database from this link: https://www.iana.org/time-zones

### Zone File, UTC Offset, Rule

The files are text files and contains the below information about a time zone:

- Definition of a time zone
- Daylight saving time (DST) rules
- Names of time zones

##### Example
```
# Rule	NAME	FROM	TO	-	IN	ON	AT	SAVE	LETTER/S
...
Rule	Iran	2017	2019	-	Mar	21	24:00	1:00	-
Rule	Iran	2017	2019	-	Sep	21	24:00	0	-
Rule	Iran	2020	only	-	Mar	20	24:00	1:00	-
Rule	Iran	2020	only	-	Sep	20	24:00	0	-
Rule	Iran	2021	2023	-	Mar	21	24:00	1:00	-
Rule	Iran	2021	2023	-	Sep	21	24:00	0	-
Rule	Iran	2024	only	-	Mar	20	24:00	1:00	-
Rule	Iran	2024	only	-	Sep	20	24:00	0	-
Rule	Iran	2025	2027	-	Mar	21	24:00	1:00	-
Rule	Iran	2025	2027	-	Sep	21	24:00	0	-
Rule	Iran	2028	2029	-	Mar	20	24:00	1:00	-
Rule	Iran	2028	2029	-	Sep	20	24:00	0	-
...

#
# The following rules are approximations starting in the year 2088.
# These are the best post-2088 approximations available, given the
# restrictions of a single rule using ordinary Gregorian dates.
# At some point this table will need to be extended, though quite
# possibly Iran will change the rules first.
Rule	Iran	2088	max	-	Mar	20	24:00	1:00	-
Rule	Iran	2088	max	-	Sep	20	24:00	0	-

# Zone	NAME		STDOFF	RULES	FORMAT	[UNTIL]
Zone	Asia/Tehran	3:25:44	-	LMT	1916
			3:25:44	-	TMT	1946     # Tehran Mean Time
			3:30	-	+0330	1977 Nov
			4:00	Iran	+04/+05	1979
			3:30	Iran	+0330/+0430
```
For more information, visit [zic man](https://man7.org/linux/man-pages/man8/zic.8.html)

### Make The Time Zone
Prepare the zone file and make any change that you want, then compile it with the below command:
```
zic {The zone file path} -d .
```
If there is no problem, then you’ll have your own time zone. The file will be created according to the zone file name but time zone name will be same as `Zone Name`.

### Usage manual

```
git clone https://github.com/ahidnaeimi/Linux_TZTehran2022.git

cd Linux_TZTehran2022

zic TehranZone -d .

cp Asia/TehranNew /usr/share/zoneinfo/Asia/

timedatectl set-timezone Asia/TehranNew

timedatectl
```