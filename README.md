# Networkwalks-B084-week3-Password-Recovery-with-JTR-and-NW-new-Tools

# Week 3: Password Cracking Labs
 
Documentation of my Week 3 practical modules on password hashing and recovery. All work was done on training files provided by Networkwalks, in an authorized learning environment, for educational purposes only.

---

## Contents

- [Overview](#overview)
- [Environment](#environment)
- [W3-PM1: Password cracking with John the Ripper and Johnny](#w3-pm1-password-cracking-with-john-the-ripper-and-johnny)
- [W3-PM2: Password cracking with Networkwalks tools](#w3-pm2-password-cracking-with-networkwalks-tools)
- [Challenges and lessons learned](#challenges-and-lessons-learned)
- [Key takeaways](#key-takeaways)
- [Disclaimer](#disclaimer)
- [Acknowledgements](#acknowledgements)

---

## Overview

Password-protected files such as PDFs do not store the password itself. They store a **hash**, a scrambled one-way value that represents it. Security professionals test password strength by extracting that hash and trying many candidate passwords until one matches. If a password is short or common, it falls quickly.

This week I recovered the password of a protected PDF (`My Locked PDF1.pdf`) using three approaches.

| Module | Focus | Tools |
|--------|-------|-------|
| W3-PM1 | Local password cracking | John the Ripper (jumbo), Johnny GUI, online hash extractor |
| W3-PM2 | Browser-based password cracking | Networkwalks Hash Calculator and Password Cracker |

## Environment

- **Operating system:** Windows [10/11]
- **Browser:** [Chrome ]
- **Tools:** John the Ripper 1.9.0 jumbo, Johnny 2.2, Networkwalks web tools
- **Target file:** `My Locked PDF1.pdf`, `My Locked PDF2.pdf` ,`My Locked PDF3.pdf`  (training file provided by Networkwalks)

---

## W3-PM1: Password cracking with John the Ripper and Johnny

**Objective:** Recover the password of a protected PDF using John the Ripper and its Johnny GUI on Windows.

### Steps

1. **Downloaded John the Ripper** (jumbo build for Windows) and extracted it. The executable `john.exe` is in the `run` folder.
2. **Downloaded and installed Johnny**, the graphical front end for John.
3. **Configured Johnny:** opened *Settings*, clicked *Browse*, and selected `john.exe`. Johnny then detected the John version.
4. **Extracted the PDF hash** by uploading the locked PDF to an online PDF hash extractor (it uses `pdf2john`). The output starts with `$pdf$`.
5. **Saved the hash** to a text file (`hash1.txt`) using Notepad, removing any stray characters such as a leading `b'`.
6. **Loaded the file in Johnny** with *Open password file*.
7. **Started the attack** with *Start new attack* and waited for the password to appear.
8. **Opened the PDF** with the recovered password and confirmed it unlocked.

### Screenshots

| Step | Screenshot |
|------|------------|
| Johnny configured with John's executable |![john](Screenshot%202026-11-20%20152717.png) |
| Hash saved in text file | ![hash](Screenshot%202026-11-21%20160607.png)|
| Attack completed |![attack](Screenshot%202026-11-21%20155717.png)|
| PDF unlocked | ![pdf](Screenshot%202026-11-18%20113228.png) |

> The hash and recovered password are deliberately hidden or cropped in the screenshots.

---

## W3-PM2: Password cracking with Networkwalks tools

**Objective:** Recover the same PDF's password using two browser-based tools, with nothing to install.

### Steps

1. **Opened the Networkwalks Hash Calculator** and uploaded the locked PDF. The file is parsed locally in the browser and the tool returns a crackable `$pdf$...` hash.
2. **Copied the complete hash**, from `$pdf$` to the end, since a missing part makes the attack fail.
3. **Opened the Networkwalks Password Cracker** and pasted the hash.
4. **Ran the dictionary attack** using the built-in wordlist. The tool tries each word, hashes it, and compares it to the target.
5. **Used the recovered password** to open the PDF.

### How it works

A **dictionary attack** tries a list of likely passwords instead of every possible combination. It succeeds only if the real password is in the list, which is why common words and predictable patterns are risky. The Networkwalks cracker applies the same idea John the Ripper uses, in a simplified form that shows each attempt.

### Screenshots

| Step | Screenshot |
|------|------------|
| Hash extracted in Hash Calculator | `screenshots/pm2-hash-calculator.png` |
| Password Cracker running | `screenshots/pm2-cracker-running.png` |
| PDF unlocked | `screenshots/pm2-pdf-unlocked.png` |

---

## Challenges and lessons learned

**Johnny setup problem (W3-PM1):** I initially struggled to get John's executable files working. I didn't realize that Johnny is only a front end and has to be installed and pointed at `john.exe` in its Settings before it can run any attack. After configuring that path, the workflow worked as expected.

**Lesson:** Read the setup steps first and understand how the tools depend on each other before troubleshooting.

## Key takeaways

- **Encryption is two-way, hashing is one-way.** Even so, weak passwords can be recovered by guessing and comparing hashes.
- **Dictionary attacks defeat short, common passwords almost instantly.**
- **Details matter:** an incomplete or malformed hash makes the attack fail.
- **GUI tools often depend on command-line tools.** Know how the pieces connect.
- **Defense:** use long, unique, mixed passphrases, and never reuse passwords.

## Disclaimer

This repository is for **educational purposes only**. All activities were performed on training files supplied by Networkwalks in an authorized learning environment. Do not use these techniques on files, accounts, or systems you do not own or have explicit written permission to test.

## Acknowledgements

Thanks to **[Networkwalks](https://www.networkwalks.com)** and my instructor **Waqas Karim (CCIE)** for the guidance and lab materials.

**Author:** [Your Name] | [LinkedIn profile link]
 
