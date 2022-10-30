---
layout: page
title: User Guide
---
## 1. Introduction
ModQuik is a desktop app that allows Teaching Assistants to keep track of their responsibilities, students’ progress and schedules for the ongoing semester.

* Table of Contents
{:toc}

--------------------------------------------------------------------------------------------------------------------

## 2. Quick start

1. Ensure you have Java `11` or above installed in your Computer.

1. Download the latest `modquik.jar` from [here](https://github.com/AY2223S1-CS2103T-W17-3/tp/releases).

1. Copy the file to the folder you want to use as the _home folder_ for your ModQuik.

1. Double-click the file to start the app. The GUI similar to the below should appear in a few seconds. Note how the app contains some sample data.<br>
   ![Ui](images/Ui.png)

1. Type the command in the command box and press Enter to execute it. e.g. typing **`help`** and pressing Enter will open the help window.<br>
   Some example commands you can try:

   * **`list`**: Lists all students.

   * **`add student`**`n/John Doe i/A0232123X ph/98765432 e/johnd@example.com tele/john_fu m/CS2103 tut/T23`: Adds a student named `John Doe` to CS2103T module.

   * **`delete student`**`3`: Deletes the 3rd student shown in the current list.

   * **`clear f/reminder`**: Deletes all reminders.

   * **`exit`**: Exits the app.

1. Refer to the [Features](#features) below for details of each command.

--------------------------------------------------------------------------------------------------------------------

## 3. Features

<div markdown="block" class="alert alert-info">

**:information_source: Notes about the command format:**<br>

* Words in `UPPER_CASE` are the parameters to be supplied by the user.<br>
  e.g. in `add n/NAME`, `NAME` is a parameter which can be used as `add n/John Doe`.

* Items in square brackets are optional.<br>
  e.g. `n/NAME [t/TAG]` can be used as `n/John Doe t/friend` or as `n/John Doe`.

* Items with `…` after them can be used multiple times including zero times.<br>
  e.g. `[t/TAG]…` can be used as ` ` (i.e. 0 times), `t/friend`, `t/friend t/family` etc.

* Parameters can be in any order.<br>
  e.g. if the command specifies `n/NAME ph/PHONE`, `ph/PHONE n/NAME` is also acceptable.

* If a parameter is expected only once in the command but you specified it multiple times, only the last occurrence of the parameter will be taken.<br>
  e.g. if you specify `ph/12341234 ph/56785678`, only `ph/56785678` will be taken.

* Extraneous parameters for commands that do not take in parameters (such as `help` and `exit`) will be ignored.<br>
  e.g. if the command specifies `help 123`, it will be interpreted as `help`.

</div>

### 3.1 Student Features

#### 3.1.1 Adding a student: `add student`

Adds a student to the specified module.

Format: `add student n/NAME i/STUDENT_ID ph/PHONE e/EMAIL tele/TELEGRAM_HANDLE m/MODULE tut/TUTORIAL [g/GRADE] [att/ATTENDANCE] [part/PARTICIPATION] [t/TAG]…`
<div markdown="span" class="alert alert-primary">:bulb: **Tip:**
A student can have any number of tags (including 0)
</div>

Examples:
* `add student n/John Doe i/A0000000J ph/98765432 e/johnd@example.com tele/johnDoe m/CS2103T tut/W17`
* `add student n/Betsy Crowe i/A0000000B t/struggling e/betsycrowe@example.com ph/91234567 tele/betsy_crowe m/CS2105 tut/G03 att/3 part/1 g/C t/quiet`

#### 3.1.2 Listing all students: `list`

Shows a list of all students in ModQuik.

Format: `list`

#### 3.1.3 Editing a student: `edit student`

Edits an existing student in a specified module.

Format: `edit student INDEX [n/NAME] [m/MODULE] [ph/PHONE] [e/EMAIL] [t/TAG]…`

* Edits the student at the specified `INDEX`. The index refers to the index number shown in the displayed student list. The index **must be a positive integer** 1, 2, 3, …
* At least one of the optional fields must be provided.
* Existing values will be updated to the input values.
* When editing tags, the existing tags of the student will be removed i.e. adding of tags is not cumulative.
* You can remove all the student’s tags by typing `t/` without
  specifying any tags after it.

Examples:
* `edit student 1 ph/91234567 e/jameslee@example.com` Edits the phone number and email address of the 1st student to be `91234567` and `jameslee@example.com` respectively.
* `edit student 2 n/Betsy Crower t/` Edits the name of the 2nd student to be `Betsy Crower` and clears all existing tags.
* `find m/CS2103T` followed by `edit student 2 n/Betsy Crower` Edits the name of the 2nd student to be `Betsy Crower` in the results of the `find` command.

#### 3.1.4 Locating students by their attributes: `find`

Finds students by names, student ID, module or tutorial, by checking if respective attribute contains any of the given keywords.

Format: `find [n/NAME] [i/STUDENT_ID] [m/MODULE] [tut/TUTORIAL]`

* At least one of the optional fields must be provided.
* The search is case-insensitive. e.g. `hans` will match `Hans`
* The order of the keywords does not matter. e.g. `Hans Bo` will match `Bo Hans`
* Only full words will be matched e.g. `Han` will not match `Hans`
* Persons matching at least one keyword will be returned (i.e. `OR` search).
  e.g. `Hans Bo` will return `Hans Gruber`, `Bo Yang`

Examples:
* `find n/John` returns `john` and `John Doe`
* `find m/CS2103T` returns list of students in CS2103T<br>\

#### 3.1.5 Deleting a student: `delete student`

Deletes the specified student from the list of students.

Format: `delete student INDEX`

* Deletes the student at the specified `INDEX`.
* The index refers to the index number shown in the displayed student list.
* The index **must be a positive integer** 1, 2, 3, …

Examples:
* `list` followed by `delete student 2` deletes the 2nd student in the list of people.
* `find n/Betsy` followed by `delete student 1` deletes the 1st student in the results of the `find` command.
* `find m/CS2103T` followed by `delete student 2` deletes the 2nd student in the results of the `find` command.

#### 3.1.6 Extracting student's emails : `extract emails`

Copies all emails in the displayed student list onto the clipboard.

Format: `extract emails`

<div markdown="span" class="alert alert-primary">:bulb: **Tip:**
Paste the link in the address bar of a browser and a pop-up will appear, prompting you to open up your email apps e.g. Outlook !
</div>

Examples:
* `find m/CS2103T` followed by `extract emails` copies all the emails of the students in the results of the `find` command.


### 3.2 Tutorial Features

#### 3.2.1 Adding a tutorial : `add tutorial`

Adds a tutorial to the list of tutorials.

Format: `add tutorial n/NAME m/MODULE v/VENUE T/TIMESLOT D/DAY`
<div markdown="span" class="alert alert-primary">:bulb: **Tip:**
Day should take in a number from 1 (Monday) to 7 (Sunday).
</div>

Examples:
* `add tutorial n/T23 m/CS2103T v/COM1-0205 T/18:00-20:00 D/1`

#### 3.2.2 Editing a tutorial: `edit tutorial`

Edits an existing student in a specified module.

Format: `edit tutorial INDEX [n/NAME] [m/MODULE] [v/VENUE] [T/TIMESLOT] [D/DAY]`

* Edits the tutorial at the specified `INDEX`. The index refers to the index number shown in the displayed tutorial list. The index **must be a positive integer** 1, 2, 3, …
* At least one of the optional fields must be provided.
* Existing values will be updated to the input values.
* When editing the timeslot or the day, both fields must be given.

Examples:
* `edit tutorial 1 n/G08 m/CS1101S` Edits the tutorial name and module of the 1st tutorial to be `G08` and `CS1101S` respectively.
* `edit tutorial 2 T/14:00-16:00 D/2` Edits the timeslot of the 2nd tutorial to be `14:00 to 16:00` and sets tutorial day to `Tue`.

#### 3.2.3 Deleting a tutorial: `delete tutorial`

Deletes a specified tutorial from the list of tutorials

Format: `delete tutorial INDEX`

* Deletes the tutorial at the specified `INDEX`.
* The index refers to the index number shown in the displayed tutorial list.
* The index **must be a positive integer** 1, 2, 3, …

Examples:
* `delete tutorial 3`

### 3.3 Consultation Features

#### 3.3.1 Adding a consultation: `add consultation`

Adds a consultation to the list of consultations.

Format: `add consultation n/NAME m/MODULE v/VENUE D/DATE T/TIMESLOT d/DESCRIPTION`

Examples:
* `add consultation n/JakeKim m/CS2103T D/2022-10-24 T/18:00-20:00 v/COM1-0205 d/past year papers`

#### 3.3.2 Editing a consultation: `edit consultation`

Edits an existing consultation in the list of consultation.

Format: `edit consultation INDEX [n/NAME] [m/MODULE] [v/VENUE] [T/TIMESLOT] [D/DATE] [d/DESCRIPTION]`

* Edits the consultation at the specified `INDEX`. The index refers to the index number shown in the displayed consultation list. The index **must be a positive integer** 1, 2, 3, …
* At least one of the optional fields must be provided.
* Existing values will be updated to the input values.
* When editing the timeslot or the date, both fields must be given.

Examples:
* `edit consultation 1 n/G08 m/CS1101S` Edits the tutorial name and module of the 1st tutorial to be `G08` and `CS1101S` respectively.
* `edit consultation 2 T/14:00-16:00 D/2022-10-10` Edits the timeslot of the 2nd consultation to be `14:00 to 16:00` and sets consultation date to `2022 Oct 10`.

#### 3.3.3 Deleting a consultation: `delete consultation`

Deletes a specified consultation from the list of consultation.

Format: `delete consultation INDEX`

* Deletes the consultation at the specified `INDEX`.
* The index refers to the index number shown in the displayed consultation list.
* The index **must be a positive integer** 1, 2, 3, …

Examples:
* `delete consultation 3`

### 3.4 Reminder Features

#### 3.4.1 Adding a reminder : `add reminder`

Adds a reminder to the list of reminders.

Format: `add reminder n/NAME T/DEADLINE_TIME D/DEADLINE_DATE p/PRIORITY d/DESCRIPTION `

Adds a reminder to the list of reminders.
* `PRIORITY` is case-insensitive and can only be either `HIGH`, `MEDIUM` or `LOW`.


Examples:
* `add reminder n/Mark Midterms D/2022-01-01 T/15:00 d/300 papers to mark p/HIGH`

#### 3.4.2 Editing a reminder: `edit reminder`

Edits an existing reminder in the list of reminders.

Format: `edit reminder INDEX [n/NAME] [T/DEADLINE_TIME] [D/DEADLINE_DATE] [p/PRIORITY] [d/DESCRIPTION] `

* Edits the reminder at the specified `INDEX`. The index refers to the index number shown in the displayed reminder list. The index **must be a positive integer** 1, 2, 3, …
* At least one of the optional fields must be provided.
* Existing values will be updated to the input values.
* When editing the time or the date, both fields must be given.
* `PRIORITY` is case-insensitive and can only be either `HIGH`, `MEDIUM` or `LOW`.


Examples:
* `edit reminder 1 p/LOW` Edits the priority of the 1st reminder to be `LOW`.
* `edit reminder 2 T/14:00 D/2022-10-10` Edits the deadline time of the 2nd reminder to be `14:00` and sets deadline date to `2022 Oct 10`.

#### 3.4.3 Mark a reminder : `mark reminder`

Marks a reminder as complete.

Format: `mark reminder INDEX`

Examples:
* `mark reminder 2`

<table>
  <tr>
    <td>Before executing mark command</td>
    <td>After executing mark command</td>
  </tr>
  <tr>
    <td><img src="images/UnmarkedReminder.png" width=350 height=400></td>
    <td><img src="images/MarkedReminder.png" width=350 height=400></td>
  </tr>
 </table>

#### 3.4.4 Unmark a reminder : `unmark reminder`

Unmarks a reminder as incomplete.

Format: `unmark reminder INDEX`

Examples:
* `unmark reminder 3`

#### 3.4.5 Deleting a reminder : `delete reminder`

Deletes the specified reminder from the list of reminders.

Format: `delete reminder INDEX`

* Deletes the reminder at the specified `INDEX`.
* The index refers to the index number shown in the displayed reminder list.
* The index **must be a positive integer** 1, 2, 3, …

Examples:
* `delete reminder 3`

#### 3.4.6 Sort reminders: `sort reminder`

Sort reminders by a chosen criteria.

Format: `sort reminder by/SORT_CRITERIA`

* `SORT_CRITERIA` must either be `priority` or `deadline`.
* Specifying `priority` will sort reminders by their priority, with `HIGH` on top of the list, followed by `MEDIUM` and `LOW`. 
Reminders with the same priority will then be sorted by date, from earliest to latest chronologically.
* Specifying `deadline` will sort reminders by their deadline, with the earliest date on top of the list.
Reminders with the same deadline will then be sorted by descending priority level, with the same order as stated above.
* Reminders with the same priority and deadline will then be sorted lexicographically. 

Examples:
* `sort reminder by/priority`

### 3.5 Switch tabs: `switch`

Switch the tabs displayed.

Format: `switch f/FIELD`

* `FIELD` includes: `student`, `tutorial`, `consultation`, `grade`

Examples:
* `switch f/tutorial` will switch tabs and display the tutorial list.
* `switch f/grade` with switch tabs and display a pie chart showing an overview of the number of students in each grade category.

![Grade Chart Tab](images/GradeChart.png)
_Figure 2. Grade Chart Tab_

### 3.6 Clearing all data: `clear`

Clears all data in a specific fields or the entire app.

Format: `clear f/FIELD`
* `FIELD` including `all`, `student`, `tutorial`, `consultation`, `reminder`

Examples:
* `clear f/all`

### 3.7 Viewing help: `help`
Shows a message explaining how to access the help page.

Format: `help`

### 3.8 Exiting the program: `exit`

Exits the program.

Format: `exit`

### 3.9 Saving the data

All data in ModQuik is saved in the hard disk automatically after executing any command that changes the data. There is no need to save manually.

### 3.10 Editing the data file

All data in ModQuik is saved as a JSON file `[JAR file location]/data/modquik.json`. Advanced users are welcome to update data directly by editing that data file.

<div markdown="span" class="alert alert-warning">:exclamation: **Caution:**
If your changes to the data file makes its format invalid, ModQuik will discard all data and start with an empty data file at the next run.
</div>

### 3.11 Archiving data files `[coming in v2.0]`

_Details coming soon..._

--------------------------------------------------------------------------------------------------------------------

## 4. FAQ

**Q**: How do I transfer my data to another Computer?<br>
**A**: Install the app in the other computer and overwrite the empty data file it creates with the file that contains the data of your previous ModQuik home folder.

**Q**: How do I toggle between tabs at the side panel  ?<br>
**A**: Click on the `Tab` button, and it will toggle between all 4 tabs (**Student**, **Grade Chart**, **Consultation**, **Tutorial**) and the command line input too.

--------------------------------------------------------------------------------------------------------------------

## 5. Command summary

| Action                     | Format, Examples                                                                                                                                                                                                     |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Add Student**            | `add student n/NAME i/STUDENT_ID ph/PHONE e/EMAIL tele/TELEGRAM_HANDLE m/MODULE tut/TUTORIAL [t/TAG]…`<br> e.g., `add student n/John Doe i/A0000000J ph/98765432 e/johnd@example.com tele/johnDoe m/CS2103T tut/W17` |
| **List All Students**      | `list`                                                                                                                                                                                                               |
| **Edit Student**           | `edit student INDEX [n/NAME] [m/MODULE] [ph/PHONE] [e/EMAIL] [t/TAG]…`<br> e.g., `edit student 1 ph/91234567 e/jameslee@example.com`                                                                                 |
| **Find Student**           | `find [n/NAME] [i/STUDENT_ID] [m/MODULE] [tut/TUTORIAL]`<br> e.g., `find n/john m/CS2103T`                                                                                                                           |
| **Delete Student**         | `delete student INDEX [m/MODULE]`<br> e.g., `delete student 2 m/CS2103T`                                                                                                                                             |
| **Extract Student Emails** | `extract emails`                                                                                                                                                                                                     |
| **Add Tutorial**           | `add tutorial n/NAME m/MODULE v/VENUE T/TIMESLOT D/DAY`<br> e.g., `add tutorial n/T23 m/CS2103T v/COM1-0205 T/1800-2000 D/1`                                                                                         |
| **Edit Tutorial**          | `edit tutorial INDEX`<br> e.g., `edit tutorial 1 n/W17 m/CS2103T`                                                                                                                                                    |
| **Delete Tutorial**        | `delete tutorial INDEX`<br> e.g., `delete tutorial 3`                                                                                                                                                                |
| **Add Consultation**       | `add consultation n/NAME m/MODULE v/VENUE D/DATE T/TIMESLOT d/DESCRIPTION`<br> e.g., `add consultation D/2022-10-24 T/18:00-20:00 v/COM1-0205 m/CS2103T n/JakeKim d/past year papers`                                |
| **Edit Consultation**      | `edit consultation INDEX`<br> e.g., `edit consultation 3 d/Review past year paper`                                                                                                                                   |
| **Delete Consultation**    | `delete consultation INDEX`<br> e.g., `delete consultation 3`                                                                                                                                                        |
| **Add Reminder**           | `add reminder n/NAME D/DEADLINE_DATE D/DEADLINE_TIME p/PRIORITY d/DESCRIPTION`<br> e.g., `add reminder n/mark papers D/2022-03-21 T/13:00 p/HIGH d/300 papers to mark`                                               |
| **Edit Reminder**          | `edit reminder INDEX`<br> e.g., `delete reminder 1 D/2022-01-01 T/14:00`                                                                                                                                             |
| **Mark Reminder**          | `mark reminder INDEX`<br> e.g., `mark reminder 3`                                                                                                                                                                    |
| **Unmark Reminder**        | `unmark reminder INDEX`<br> e.g., `unmark reminder 3`                                                                                                                                                                |
| **Delete Reminder**        | `delete reminder INDEX`<br> e.g., `delete reminder 3`                                                                                                                                                                |
| **Sort Reminder**          | `sort reminder by/SORT_CRITERIA`<br> e.g., `sort reminder by/priority`                                                                                                                                               |
| **Switch Tabs**            | `switch f/FIELD`<br> e.g., `switch f/tutorial`                                                                                                                                                                       |
| **Clear**                  | `clear f/FIELD`<br> e.g., `clear f/student`                                                                                                                                                                          |
| **Help**                   | `help`                                                                                                                                                                                                               |
| **Exit**                   | `exit`                                                                                                                                                                                                               |

## 6. Prefix summary

| Prefix    | Symbolise        | Used in                                                                                                                                                                   |
|-----------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **att/**  | attendance       | `add student`<br> `edit student`                                                                                                                                          |
| **by/**   | sorting criteria | `sort reminder`                                                                                                                                                           |
| **d/**    | description      | `add consultation`<br> `edit consultation`<br> `add reminder`<br> `edit reminder`                                                                                         |
| **D/**    | date or day      | `add consultation`<br> `edit consultation`<br> `add reminder`<br> `edit reminder`                                                                                         |
| **e/**    | email            | `add student`<br> `edit student`                                                                                                                                          |
| **f/**    | field            | `switch` <br> `clear`                                                                                                                                                     |
| **g/**    | grade            | `add student`<br> `edit student`                                                                                                                                          |
| **i/**    | student id       | `add student`<br> `edit student`<br> `find`                                                                                                                               |
| **m/**    | module           | `add student`<br> `edit student`<br> `find`<br> `add tutorial`<br> `edit tutorial`<br> `add consultation`<br> `edit consultation`                                         |
| **n/**    | name             | `add student`<br> `edit student`<br> `find`<br> `add tutorial`<br> `edit tutorial`<br> `add consultation`<br> `edit consultation`<br> `add reminder`<br> `edit reminder`  |
| **p/**    | priority         | `add reminder`<br> `edit reminder`                                                                                                                                        |
| **ph/**   | phone            | `add student`<br> `edit student`                                                                                                                                          |
| **part/** | participation    | `add student`<br> `edit student`                                                                                                                                          |
| **t/**    | tag              | `add student`<br> `edit student`                                                                                                                                          |
| **T/**    | time             | `add student`<br> `edit student`                                                                                                                                          |
| **tut/**  | tutorial         | `add student`<br> `edit student`<br> `find`<br> `add tutorial`<br> `edit tutorial`                                                                                        |
| **tele/** | Telegram handle  | `add student`<br> `edit student`                                                                                                                                          |
| **v/**    | venue            | `add tutorial`<br> `edit tutorial`<br> `add consultation`<br> `edit consultation`                                                                                         |
