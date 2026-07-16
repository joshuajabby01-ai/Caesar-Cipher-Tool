# Caesar-Cipher-Tool
This project implements the Caesar cipher, a substitution cipher where each letter in the text is shifted by a fixed number of positions in the alphabet. It supports both encrypting and decrypting text through an interactive CLI, and preserves letter casing and non-alphabetic characters (spaces, punctuation, numbers) unchanged.

✨ Features
- Encrypt or decrypt any text via simple CLI prompts
- Preserves uppercase/lowercase formatting
- Non-letter characters (spaces, punctuation) pass through unchanged
- Shift values wrap around the alphabet correctly using modular arithmetic
- Input validation for mode selection

 Tech Stack
- **Language:** Python (standard library only — no dependencies)

 Usage
```bash
git clone https://github.com/yourusername/caesar-cipher.git
cd caesar-cipher
python caesar_cipher.py

## Example run:
=== Caesar Cipher ===
Mode (encrypt/decrypt): encrypt
Enter text: Hello, World!
Enter shift (1-25): 3
Result: Khoor, Zruog!

## 💻 Code

```python
def caesar_cipher(text, shift, mode='encrypt'):
    if mode == 'decrypt':
        shift = -shift

    result = []
    for char in text:
        if char.isalpha():
            base = ord('A') if char.isupper() else ord('a')
            shifted = (ord(char) - base + shift) % 26 + base
            result.append(chr(shifted))
        else:
            result.append(char)

    return ''.join(result)


def main():
    print("=== Caesar Cipher ===\n")

    mode = input("Mode (encrypt/decrypt): ").strip().lower()
    if mode not in ('encrypt', 'decrypt'):
        print("Invalid mode. Choose 'encrypt' or 'decrypt'.")
        return

    text = input("Enter text: ")
    shift = int(input("Enter shift (1-25): "))

    output = caesar_cipher(text, shift, mode)
    print(f"\nResult: {output}")


if __name__ == "__main__":
    main()
```

## 🧠 How It Works
Each letter is converted to its alphabet position (0–25), shifted by the given amount, and wrapped using the modulo operator so the shift loops back around from Z to A. Decryption simply reverses the shift. The `ord()`/`chr()` functions handle the letter-to-number conversion while keeping the original case intact.

## 🧠 What I Learned
Working with character encoding (`ord`/`chr`), modular arithmetic for wraparound logic, and handling edge cases like mixed-case text and non-alphabetic characters cleanly.
