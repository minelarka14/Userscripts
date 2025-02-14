# UoA SSO Timetable to iCalendar

This script fetches data from the timetable on SSO (Student Services Online) and converts it into `.ics` format. This script was written as UoA decommissioned UoACal with zero notice and has yet to communicate when a replacement service would be available.

> [!CAUTION]
> **Standard cybersecurity warning:**
> Do not blindly run code from untrusted sources. Please audit the code before running it.

## Usage

> [!WARNING]
> ### **Create a new calendar in your calendar application separate from your main calendar.**
> 
> **This script works differently to UoACal**. The link UoACal gives subscribes you to a seperate calendar, the whole calendar is easily removable.
>
> The `.ics` file that this script generates will import events into YOUR (likely main or personal, by default) calendar and, if you don't import the `.ics` file into a seperate calendar, the events CANNOT be easily removed in bulk.
>
> **If you don't import the generated `.ics` into a seperate calendar, you will need to manually delete the events** (30 events in my case) when you want to remove all events generated by this script. You may want to do that for several reasons:
> - The script is not working properly and generates classes with incorrect dates or times.
> - UoA releases their successor to UoACal and you want to stop using this to switch to that instead.
> - You have changed your enrolments and wish to update your timetable again. You need to delete the previous events and import them again.
>   - **⚠️ Previous events may not get deleted (causing a double-up).**
>   - **⚠️ Changed class times may not get deleted.**
> 
> Use at your own risk. Verify the calendar is correct before confirming the import into your calendar application.

0. Please read the `Important` block above. This will NOT work if your timezone is not `Pacific/Auckland` (e.g., you are overseas). Change your device timezone to `Pacific/Auckland`
1. Go to the ["My Class Timetable" page on SSO](https://www.student.auckland.ac.nz/psc/ps/EMPLOYEE/SA/c/UOA_MENU_FL.UOA_VW_CAL_FL.GBL)
2. Open the JavaScript Console:
   - On Firefox and forks (e.g. Librewolf, Waterfox, Pale Moon), Chromium and forks (e.g. Chrome, Edge, Brave, Opera):
     - `ctrl` + `shift` + `I`
     - Click on the "[Console]" tab at the top
   - On Safari on macOS (unverified; I do not have macOS):
     - You will need to enable the "Develop" menu in the menu bar:
       - `⌘` + `,` to open Safari Preferences, or use the "Safari" Menu
       - Navigate to the "Advanced" tab, find "Show Develop menu in menu bar" and enable this setting
     - `Option` + `⌘` + `C` to open the JavaScript Console, or use the "Show JavaScript Console" in the "Develop" menu
3. Copy the code from  [uoa-timetable-to-ical.js](https://github.com/Excigma/Userscripts/blob/trunk/student.auckland.ac.nz/uoa-timetable-to-ical.js)
4. Paste the code into the console. You may need to allow pasting before your browser allows you to paste code into the console
5. Press Enter to run the code. You should see the script switching to the "List View" tab, opening "Meeting Information" for each meeting, and finally downloading a file: `uoa-sso-calendar.ics`. The `.ics` file's contents will be logged to the console as well
6. Note: Importing events from `.ics` files might be a **difficult to reverse action** depending on your calendar application. Read the `Important` block above before importing the `.ics` file.

> [!IMPORTANT]
> **Events may show up even on public holidays when classes are not running. Check SSO on public holidays to verify. The calendar will not update if your timetable changes.**

 ## Steps to create a new calendar in your calendar application
 ### Google Calendar
 - You can make a new calendar by visiting https://calendar.google.com
 - Go to "Settings" > "Add calendar" > "Create new calendar"
 - Create a new calendar for UoA SSO Timetable to iCalendar's `.ics` import
 - Import the `.ics` file by going to "Settings" > "Import & export". Make sure you select the correct calendar to import into

...feel free to contribute steps for your favorite calendar application

## Credits
- [@Silverarmor](https://github.com/Silverarmor) for sharing places with timetable data and ideas how to parse it - the method that this script works is based on his ideas
- [@BirdMakingStuff](https://github.com/BirdMakingStuff) for testing early revisions of the script reporting bugs, and providing fixes
- [@tash192dev](https://github.com/tash192dev) for providing examples of the `.ics` format, allowing me to fix timezone/date-related issues
