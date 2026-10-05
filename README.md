# Rose Frame

A small browser lesson on **stack buffer overflow** for COMS 352.

Open `index.html` and type a name. The page draws a simplified function frame and shows `strcpy` walking from a local buffer toward higher addresses, into the saved frame pointer and the return address when the name is too long.

This is a picture of memory for learning. It is not an exploit, a payload, or a program you can attack.

## Run it

No install and no build step.

1. Download or clone this repository.
2. Open `index.html` in Chrome, Firefox, Safari, or Edge.

You can also serve the folder locally:

```bash
python3 -m http.server 8765
```

Then visit `http://127.0.0.1:8765`.

## What you can do

- Type any short ASCII message, or pick an example from the menu.
- Drag **buffer size** to change how many bytes `buf` holds.
- Scrub **copy progress**, or use **Next byte** and **Walk the copy**, to watch one byte land at a time.
- Turn on **length check** to skip the copy when the name plus its NUL would not fit in the buffer.
- Turn on **stack canary** to place guard bytes between the buffer and the saved control data.

## What the picture simplifies

The frame is a 32-bit teaching model: a 4-byte saved frame pointer and a 4-byte return address, stored little-endian. Real 64-bit frames use wider slots, and compilers add padding and their own canary layout. The addresses (`0xBFFF0E00` for `buf[0]`, `0x00401230` for “resume in main”) are made up so the lesson can talk about neighbors without pointing at a real binary.

## What this repository does not contain

No shellcode, no chosen jump target, and no steps for compromising a program. Overflowed bytes are shown as the characters you typed, re-read as data, and the explanation stops there.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The interactive lesson (HTML, CSS, and JavaScript in one file) |
| `reflection.md` | One-page note on building the lesson and what it clarified |
| `README.md` | This file |

## Privacy

This project has no API keys, passwords, or personal data. If the repository is made private, add the instructor (`@atamrawi`) and the TA (`@adajani`) as collaborators before the deadline.
