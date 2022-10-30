---
layout: page
title: User Guide
---
## 1. Introduction
ModQuik is a desktop app that allows Teaching Assistants to keep track of their responsibilities, students’ progress and schedules for the ongoing semester.

* Table of Contents
{:toc}

--------------------------------------------------------------------------------------------------------------------
<div style="page-break-after: always;"></div>

## 5. Command summary

| Action                     | Format, Examples                                                                                                                                                                                                     |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Add Student**            | `add student n/NAME i/STUDENT_ID ph/PHONE e/EMAIL tele/TELEGRAM_HANDLE m/MODULE tut/TUTORIAL [t/TAG]…`<br> e.g., `add student n/John Doe i/A0000000J ph/98765432 e/johnd@example.com tele/johnDoe m/CS2103T tut/W17` |
| **List All Students**      | `list`                                                                                                                                                                                                               |
| **Edit Student**           | `edit student INDEX [n/NAME] [m/MODULE] [ph/PHONE] [e/EMAIL] [t/TAG]…`<br> e.g., `edit student 1 ph/91234567 e/jameslee@example.com`
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

<div style="page-break-after: always;"></div>

## 6. Prefix summary

| Prefix    | Symbolise        | Used in                                                                                                                                                                          |
|-----------|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **att/**  | attendance       | `add student`</br> `edit student`                                                                                                                                                |
| **by/**   | sorting criteria | `sort reminder`                                                                                                                                                                  |
| **d/**    | description      | `add consultation`</br> `edit consultation`</br> `add reminder`</br> `edit reminder`                                                                                             |
| **D/**    | date or day      | `add consultation`</br> `edit consultation`</br> `add reminder`</br> `edit reminder`                                                                                             |
| **e/**    | email            | `add student`</br> `edit student`                                                                                                                                                |
| **f/**    | field            | `switch` <br/> `clear`                                                                                                                                                           |
| **g/**    | grade            | `add student`</br> `edit student`                                                                                                                                                |
| **i/**    | student id       | `add student`</br> `edit student`</br> `find`                                                                                                                                    |
| **m/**    | module           | `add student`</br> `edit student`</br> `find`</br> `add tutorial`</br> `edit tutorial`</br> `add consultation`</br> `edit consultation`                                          |
| **n/**    | name             | `add student`</br> `edit student`</br> `find`</br> `add tutorial`</br> `edit tutorial`</br> `add consultation`</br> `edit consultation`</br> `add reminder`</br> `edit reminder` |
| **p/**    | priority         | `add reminder`</br> `edit reminder`                                                                                                                                              |
| **ph/**   | phone            | `add student`</br> `edit student`                                                                                                                                                |
| **part/** | participation    | `add student`</br> `edit student`                                                                                                                                                |
| **t/**    | tag              | `add student`</br> `edit student`                                                                                                                                                |
| **T/**    | time             | `add student`</br> `edit student`                                                                                                                                                |
| **tut/**  | tutorial         | `add student`</br> `edit student`</br> `find`</br> `add tutorial`</br> `edit tutorial`                                                                                           |
| **tele/** | Telegram handle  | `add student`</br> `edit student`                                                                                                                                                |
| **v/**    | venue            | `add tutorial`</br> `edit tutorial`</br> `add consultation`</br> `edit consultation`                                                                                             |
