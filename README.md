# 🖼️ Image Steganography using LSB Encoding and Decoding

An **Image Steganography** project developed in **C** that hides secret information inside an image using the **Least Significant Bit (LSB) technique**.

The project demonstrates how data can be embedded into image data by modifying the least significant bits while maintaining the visual appearance of the original image.

The project consists of two main operations:

* 🔐 **Encoding** – Hiding secret information inside an image.
* 🔓 **Decoding** – Extracting the hidden information from the stego image.

---

## 📌 Table of Contents

* [Project Overview](#-project-overview)
* [Features](#-features)
* [Project Objectives](#-project-objectives)
* [Technologies Used](#-technologies-used)
* [Project Structure](#-project-structure)
* [System Requirements](#-system-requirements)
* [Compilation](#-compilation)
* [Running the Project](#-running-the-project)
* [Encoding](#-encoding)
* [Decoding](#-decoding)
* [LSB Technique](#-lsb-technique)
* [Workflow](#-workflow)
* [Sample Execution](#-sample-execution)
* [Key Challenges and Learnings](#-key-challenges-and-learnings)
* [Limitations](#-limitations)
* [Future Enhancements](#-future-enhancements)
* [Learning Outcomes](#-learning-outcomes)
* [Author](#-author)

---

## 📌 Project Overview

**Image Steganography** is a technique used to hide secret information inside a digital image.

This project uses **LSB encoding and decoding** to hide and retrieve secret data from an image.

The basic concept is:

```text
Cover Image + Secret Data
          |
          v
     LSB Encoding
          |
          v
      Stego Image
          |
          v
     LSB Decoding
          |
          v
     Secret Data
```

The project provides practical experience with **image data, file handling, bitwise operations, pointers, structures, and C programming**.

---

## ✨ Features

* 🔐 Encode secret data into an image.
* 🔓 Decode hidden data from an image.
* 🖼️ Uses image data for information hiding.
* 🔢 Uses bitwise operations for manipulating individual bits.
* 📂 Performs file handling operations.
* 🧩 Modular C programming.
* ✅ Command-line based execution.
* 🔍 Extracts hidden information from the encoded image.

---

## 🎯 Project Objectives

* To understand the fundamentals of **image steganography**.
* To implement **LSB encoding and decoding**.
* To understand image file data and pixel information.
* To practice **bitwise manipulation in C**.
* To understand file handling in C.
* To understand how information can be hidden inside an image.
* To retrieve embedded information from a stego image.

---

## 🛠️ Technologies Used

| Technology             | Usage                        |
| ---------------------- | ---------------------------- |
| **C**                  | Core programming language    |
| **LSB Technique**      | Data hiding                  |
| **Bitwise Operations** | Bit manipulation             |
| **File Handling**      | Reading and writing files    |
| **Pointers**           | Data and memory manipulation |
| **Structures**         | Managing project data        |
| **GCC**                | Compilation                  |

---

## 📁 Project Structure

```text
Image-Steganography/
│
├── main.c
├── encode.c
├── encode.h
├── decode.c
├── decode.h
├── types.h
├── common.h
└── README.md
```

> The file names above should be adjusted if your actual source files use different names.

---

## 💻 System Requirements

* GCC Compiler
* Linux / Ubuntu / WSL / macOS
* Command-line terminal
* Basic knowledge of C programming
* Understanding of bitwise operations
* Understanding of file handling

---

## ⚙️ Compilation

This project does **not require a Makefile**.

Compile the C source files directly using GCC.

For example:

```bash
gcc *.c -o steganography
```

If your source files are separated into encoding and decoding modules, you can compile them together:

```bash
gcc main.c encode.c decode.c -o steganography
```

Run:

```bash
./steganography
```

---

## ▶️ Running the Project

The project supports two operations:

```text
Encoding
Decoding
```

The exact command-line arguments should follow the format implemented in the source code.

A typical usage format is:

```bash
./steganography -e <source_image> <secret_file> <output_image>
```

For decoding:

```bash
./steganography -d <stego_image> <output_file>
```

---

## 🔐 Encoding

Encoding is the process of hiding secret information inside a cover image.

### Encoding Process

```text
             Cover Image
                  |
                  v
          Read Image Information
                  |
                  v
          Read Secret Information
                  |
                  v
          Check Image Capacity
                  |
                  v
        Convert Data into Bits
                  |
                  v
          Embed Bits using LSB
                  |
                  v
            Create Stego Image
```

During encoding, selected **least significant bits** of the image data are modified to store the bits of the secret information.

---

## 🔓 Decoding

Decoding is the process of retrieving the secret information from the stego image.

### Decoding Process

```text
             Stego Image
                  |
                  v
          Read Image Information
                  |
                  v
          Access Embedded Bits
                  |
                  v
          Extract LSB Values
                  |
                  v
        Reconstruct Secret Data
                  |
                  v
           Save Decoded Data
```

The decoder reads the embedded bits and reconstructs the original secret information.

---

## 🔢 LSB Technique

**LSB** stands for **Least Significant Bit**.

A byte contains eight bits:

```text
7 6 5 4 3 2 1 0
| | | | | | | |
              ^
             LSB
```

The rightmost bit is the least significant bit.

For example:

```text
Original byte:
10110110
```

If the required secret bit is `1`, it can be changed to:

```text
10110111
```

Only one bit has changed.

Similarly:

```text
Original:
10110111

Modified:
10110110
```

The modification is very small and is generally difficult to notice visually when applied appropriately to image data.

---

## 🧠 Bitwise Operations

Bitwise operations are an important part of the LSB technique.

Common bitwise operators in C include:

```c
&
|
^
<<
>>
```

These operations allow individual bits to be examined, modified, shifted, and extracted.

---

## 🖼️ Image Data Representation

A digital image contains image information that can be represented as bytes.

A simplified representation is:

```text
Image File
    |
    +---- Header
    |
    +---- Image Data
             |
             +---- Pixel Data
                    |
                    +---- Byte
                    +---- Byte
                    +---- Byte
                    +---- ...
```

The steganography process uses suitable image data to store the hidden information.

---

## 🔄 Workflow

```text
                       Start
                         |
                         v
                Read Command-Line Input
                         |
                         v
                   Select Operation
                    /           \
                   /             \
                  v               v
             Encoding          Decoding
                |                 |
                v                 v
          Open Cover Image    Open Stego Image
                |                 |
                v                 v
          Read Secret Data    Read Embedded Data
                |                 |
                v                 v
          Encode Using LSB    Extract Using LSB
                |                 |
                v                 v
           Create Stego       Generate Secret
              Image               File
                |                 |
                +--------+--------+
                         |
                         v
                        End
```

---

## 🖥️ Sample Execution

### Encoding

```text
$ ./steganography -e source.bmp secret.txt stego.bmp

Encoding started...

Encoding completed successfully.

Stego image generated successfully.
```

### Decoding

```text
$ ./steganography -d stego.bmp decoded.txt

Decoding started...

Decoding completed successfully.

Secret data extracted successfully.
```

> Replace these example commands with the exact commands supported by your source code if they are different.

---

## 🔍 Example of LSB Encoding

Suppose a secret character is represented by the following binary value:

```text
01000001
```

The encoder can store these bits in the least significant bits of image-data bytes.

For example:

```text
Image bytes:

10110110
11001010
10011100
11100010
...
```

After embedding:

```text
10110110 → stores 0
11001011 → stores 1
10011100 → stores 0
11100010 → stores 0
...
```

The decoder reads the LSBs:

```text
0 1 0 0 0 0 0 1
```

and reconstructs:

```text
01000001
```

which represents the original character.

---

## 🧩 Key Challenges and Learnings

The major challenges encountered during the development of this project include:

* Understanding **image pixels and image file headers**.
* Understanding how information can be embedded without significantly changing the image.
* Performing **bitwise manipulation** to embed and extract data.
* Managing binary data during encoding and decoding.
* Handling image and secret-data files.
* Debugging errors during data embedding and extraction.

These challenges helped improve practical understanding of **C programming, bitwise operations, file handling, pointers, and image-data processing**.

---

## ⚠️ Limitations

* The amount of information that can be hidden depends on the capacity of the cover image.
* Excessive modification of image data can affect image quality.
* LSB steganography itself does not provide encryption.
* Modifying or compressing the stego image may corrupt the hidden information.
* The technique is primarily suitable for educational and demonstration purposes.

---

## 🚀 Future Enhancements

Possible improvements include:

* 🔐 Add encryption before embedding secret information.
* 📦 Add data compression before encoding.
* 🔑 Implement password-based protection.
* 🖼️ Support additional image formats.
* 📊 Add image-quality analysis.
* 🛡️ Improve resistance against image processing.
* 🖥️ Develop a graphical user interface.
* 📁 Support multiple secret-file formats.

---

## 📚 Learning Outcomes

Through this project, I gained practical experience in:

* **C Programming**
* **Image Steganography**
* **LSB Encoding and Decoding**
* **Bitwise Operations**
* **File Handling**
* **Pointers**
* **Structures**
* **Binary Data Manipulation**
* **Image File Processing**
* **Command-Line Arguments**
* **Modular Programming**
* **Debugging and Error Handling**

---

## 👨‍💻 Author

**Darshuu**

### 📌 Project

**Image Steganography using LSB Encoding and Decoding**

### 💻 Language

**C Programming**

### 🧠 Concepts

**LSB Steganography | Bitwise Operations | File Handling | Pointers | Structures | Binary Data Processing**

---

⭐ If you find this project useful, feel free to star the repository!
