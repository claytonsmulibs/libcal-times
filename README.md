# libcal-times
These scripts work with the library hours widgets provided in Springshare's LibCal system. Created with claude.ai, the scripts reformat the times displayed on web pages to match my university's editorial style, which is based on the AP Stylebook. 

We use these widgets on our website (www.smu.edu/libraries): Today's Hours, Daily Hours, Weekly Grid View, Monthly Calendar View. The added script for the Monthly Calendar View should be placed in the page code AFTER the LibCal script. The added script used with the other widgets should be placed BEFORE the LibCal script. Following are detailed descriptions of what the two scripts do.
 
Time Formatting Script for Daily Hours, Weekly Hours, and Upcoming Events

This script should be placed BEFORE loading hours_grid.js, hours_today.js, api_hours_today.php, or api_events.php.

What it formats:
Elements with class .s-lc-time (weekly hours grid)
Elements with class .event-daytime (event listings)
Elements with class .s-lc-whw-head-date (date headers in weekly grid)

Formatting rules applied:
1.	Removes leading zeros from dates - "Nov 05" → "Nov 5"
2.	Standardizes am/pm format - Adds spaces and periods (e.g., "9am" → "9 a.m.")
3.	Replaces 12 a.m./12:00 a.m. with "Midnight"
4.	Replaces 12 p.m./12:00 p.m. with "Noon"
5.	Removes :00 from times on the hour - "10:00 a.m." → "10 a.m." (but preserves actual minutes like "10:30")
6.	Removes spaces around en dashes - "2 p.m. – 5 p.m." → "2 p.m.–5 p.m."
7.	Removes redundant period designations in same-period ranges - "8 a.m.–11 a.m." → "8–11 a.m."
8.	Handles cross-period ranges - Keeps both designations: "10 a.m.–5 p.m."
9.	Properly formats ranges with Noon and Midnight - "10 a.m.–Noon", "Midnight–5 a.m."

How it works:
Processes content on page load with multiple retries (100ms, 500ms, 1000ms, 2000ms)
Intercepts dynamic content insertion via innerHTML
Monitors for navigation clicks and processes content after navigation
Uses MutationObserver to watch for DOM changes
Automatically reformats new content as it appears


