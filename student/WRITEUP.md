---
# WHO THIS IS. Fill both in before you submit.
#
# This repository is PRIVATE — you and I are the only people who can read it.
# I need these two lines to put your grade in Canvas against the right person:
# GitHub knows you as a username, Canvas knows you as a student, and this is
# the only place those two meet. A blank or wrong ID means a grade that lands
# on nobody, and I have to come find you to fix it.
name: "Andrew Trujillo"
student_id: "032953828"

# The autograder reads only the honor flag below. Each ward is graded by
# running your exploit and checking its proof with the oracle, so there is no
# ward flag to paste. The lines below are for your own record: ward II and
# ward IV recover a CECS378 flag; ward I and ward III proofs are a duplicated
# block and a forged token, not flags.
honor: CECS378{honor_8b40653e01e9aa58935a31d7}
ward2: CECS378{ward2_f72dca9896c9358c632ff698}
ward4: CECS378{ward4_...}   # OMEGA WARD (Ω stretch)
---

# Grimoire of the Spellbreaker

> Every Spellbreaker keeps a grimoire, a record of how each ward fell, so the
> next break comes faster. This one is yours. Write an entry for every ward you
> defeated: comment your exploit code, cite at least one source, and tell me
> *how* the ward broke, not merely that it did. "I ran the attack" earns
> nothing; "the ward leaked X, which let me do Y" earns everything.

## The Oath

Speak the SOLDIER's Oath, run `python pledge.py`, and paste the honor flag it
yields into the frontmatter above. No honor flag, no marks: a Spellbreaker who
won't sign their work doesn't get paid.

## Ward I — The Wisp (ECB detection)

- **How I made the pattern flicker:**
I first checked that the ciphertext was made into proper blocks, once i did that I used list comprehension to check if any block repeated more than once and get the block that repeated
- **The real-world sin this is (name the CVE class):**
The CVE class that this vulnerability is is CWE-329, it is about predictable IVs found in the repeated blocks of this vulnerability.

## Ward II — The Rune Golem (ECB byte-at-a-time)

- **The block size I measured, and how I measured it:**
I messured the block size by adding different amounts of characters to the prefix and then seperating the bytes from the ward into 16 byte blocks, when a new block was added then I knew where the block size was
- **How prying one rune at a time recovers the whole word:**
By prying one rune at a time, i could slowly get all of the parts of the rune, i just need the prefix to stay the same and the recovered bytes/letters to be checked with that prefix value, checking it between them showed me one at a time and slowly recovered all of the word, building off of the last letter, though it would be easier if i wrote them in letters instead of bytes
- **Where this same flaw bites real systems:**
This same flaw can bite real systems by revealing the secret key used to encrypt their system, allowing others to hack into the system using that same key to get past their encryption, even if getting that key can take some time.

## Ward III — The Mirror Knight (CBC bit-flipping)

- **Which ciphertext byte(s) I flipped, and what each plaintext byte became:**
I flipped the ciphertext from block 2, and then making the plaintext byte be ";admin=true;AAA" with the A's being added at the end so the block size remainds the same.
- **Why CBC let me forge a sigil the ward couldn't question:**
CBC let me forge a sigil that the ward couldn't question because it considers that ciphertext secure, the sigil was already authenticated and sent, by doing the CBC bit flip, it changes that already authenticated data and changes it slightly, using that change and the fact that it is already authenticated, the ward couldn't question it
- **Where this same flaw bites real systems:**
This flaw bites real systems when someone is able to intercept a message and be able to change the contents of that message, allowing them to do things like change admin access, where files are going, etc. that they shouldn't be able to normally.

## Ward IV — OMEGA WARD (CBC padding oracle)  *(optional Ω stretch)*

- **What the one leaked bit told me, and how it cascades into full plaintext:**
- **The real-world reckoning (POODLE / Lucky 13):**

## Behind the curtain  *(optional, for the curious)*

- **Read the published oracle source: which primitives derive per-session
  secrets, and why does their one-wayness keep those proofs unforgeable?**

## Sources
https://crypto.stackexchange.com/questions/66085/bit-flipping-attack-on-cbc-mode
-
