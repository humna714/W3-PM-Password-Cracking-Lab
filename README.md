# W3-PM-Password-Cracking-Lab
Educational lab for Password Cracking using Hash Calculator and Password Cracker and John the Ripper

Password Cracking Lab

A simple, beginner-friendly lab that shows how locked (password-protected) PDF files can be cracked using a dictionary attack.

This is based on the Networkwalks Cybersecurity Labs. It uses two Networkwalks web tools "the Hash Calculator and the Password Cracker" together with John the Ripper on Kali Linux.

What is a dictionary attack?

A dictionary attack means trying lots of common passwords, one by one, from a list (called a wordlist), until one of them works. Many people use weak, common passwords like password1. A dictionary attack can crack these in seconds.

What you need
A password-protected PDF file.
A wordlist file full of common passwords (for example JTR_default_password.txt).
Kali Linux (for the John the Ripper method), or just a web browser (for the Networkwalks web tools method).
How it works (step by step)
Step 1: Extract the hash from the PDF

Go to the Networkwalks Hash Calculator tool and open the PDF tab. Upload your locked PDF file. The tool reads the file in your browser (it is not uploaded anywhere) and shows a message like:

"This PDF is encrypted. A crackable hash has been extracted below."

Copy the hash shown. It looks something like this:

$pdf$4*4*128*-1028*1*16*ca7f72f11459cba469f1005a8765ed51*32*f32d8fa1bfbe...
Step 2: Crack the hash

You can crack this hash in two ways:

Option A: Networkwalks Password Cracker (web tool, no install needed)

Open the Networkwalks Password Cracker tool.
Paste the hash from Step 1 into it.
Click to start the attack. The tool tries every word in its wordlist against the hash and shows progress, like:
Tried: 3456 / 3556
[-] Trying: testi
[-] Trying: tika
[-] Trying: tnt
When it finds a match, it shows:
PASSWORD CRACKED SUCCESSFULLY
good-luck

Option B: John the Ripper (on Kali Linux)

Save the hash from Step 1 into a file, for example hash-pdf1.
Open a terminal and run:
bash
john --wordlist=JTR_default_password.txt --rules hash-pdf1
Once it finishes, see the cracked password with:
bash
john --show hash-pdf1

This prints something like:

?:good-luck
Step 3: Unlock the PDF

Open the PDF and type in the password you found. The file will now open.

Step 4: Repeat for more PDFs

Do the same steps again for any other locked PDF. Each one gets its own hash file (hash-pdf1, hash-pdf2, hash-pdf3, and so on).

Example results from this lab
PDF file	Hash file	Cracked password
My Locked PDF1.pdf	hash-pdf1	good-luck
My Locked PDF2.pdf	hash-pdf2	password1
My Locked PDF3.pdf	hash-pdf3	1qaz2wsx

Each completed step in the real lab unlocks a "flag" (a short code that proves you finished that part), for example:

nw{cybersecurity_flag_captured_2608}
nw{networkwalks_persistence_jtr_270521}
nw{networkwalks_flag_260821_1}
Why this matters

Common passwords like password1 or 1qaz2wsx can be cracked almost instantly with a basic wordlist. This lab is a reminder to always use long, random, and unique passwords, especially on important files.

⚠️ Please use this responsibly
Only crack passwords on files you own, or ones you have clear permission to test.
This project is for learning and authorized practice only.
Never use these steps on someone else's files or accounts without permission — that is illegal.
