![Version](https://img.shields.io/badge/Version-1.0-blue)
![Hardware](https://img.shields.io/badge/Hardware-Cardputer_ADV-orange)
![Platform](https://img.shields.io/badge/Platform-M5Stack-red)
![License](https://img.shields.io/badge/License-Proprietary-gray)
[![Boosty](https://img.shields.io/badge/Support-Boosty-orange)](https://boosty.to/zeloksa)

# 📚 Wikipedia Offline ADV (V1.0)

**Wikipedia Offline ADV** is a hyper-optimized, standalone Wikipedia search engine and Pseudo-AI assistant built specifically for the **M5Stack Cardputer ADV**. It allows you to carry exactly **6,400,233 articles** in your pocket, fully offline, wrapping complex data retrieval in an immersive, retro-futuristic "ELIZA OS" terminal interface.

> [!IMPORTANT]
> **SD Card Required:** This application relies entirely on an external MicroSD card formatted in FAT32. You **must** download the proprietary database `.bin` files (containing the full 6.4 million article archive) and place them in the root of your SD card for the OS to boot.
> **Storage Requirement:** The unpacked database requires **18.3 GB** of free space. A **32GB (or larger)** SD card is required.
> **Distribution:** Binary available via **M5Burner**.

---

## ⚡ Technical Highlights

* **O(log N) Binary Pointer Search:** Bypasses standard FAT32 4GB file limits by distributing data across multiple chunks (`dataX.bin`) and packing file IDs and local offsets into 64-bit pointers. Searches through the entire database of **6,400,233 articles** take mere milliseconds.
* **Pseudo-AI Extractive QA (Question Answering):** More than just a search bar. Ask natural questions (e.g., *"Who is the president of the USA?"* or *"What are the symptoms of a cold?"*). The onboard NLP engine cleans the intent, loads the 32KB article into RAM, and scores sentences using a custom **TF-IDF Lite algorithm** to extract and print the exact answer before displaying the full text.
* **Fuzzy Levenshtein Radar:** Typos happen on a tiny keyboard. If an exact match isn't found, the engine scans a 250-article sliding window on the SD card, calculates Levenshtein distance relevancy, and offers a paginated list of the 96 closest matches.

---

## 🛠 Installation

1. Open **M5Burner**.
2. Search for `Wikipedia Offline ADV` or `Zeloksa`.
3. Select version **V1.0** and burn it to your M5Stack Cardputer.
4. **CRITICAL:** Download the archive containing the 6.4 million article database from Google Drive:
👉 **[Download Database (18.3 GB)](https://drive.google.com/file/d/1vk8ZYRW6EJnWbYxpt7XWHItsnzcVqdjU/view?usp=drive_link)**

   *(Note: Google Drive will say it cannot scan the file for viruses because it is too large. This is normal for heavy files. Click "Download anyway".)*
5. Unpack the downloaded `.zip` archive. Ensure you have at least **18.3 GB** of free space.
6. Move the files `index_ptr.bin`, `index_data.bin`, and all `dataX.bin` files **directly into the root directory** of your FAT32-formatted MicroSD card. 

> [!WARNING]
> **Do not put the database files into folders!** ELIZA OS scans only the root directory (`/`) of the storage. If the files are hidden inside a sub-folder, the system will trigger a databank fault on boot.

7. Insert the MicroSD card into your Cardputer and power it on to initialize the terminal.

---

## 🕹 Controls & Usage

* **[ A-Z, 0-9 ]**: Type your query naturally.
* **[ ENTER ]**: Execute search / Submit selection.
* **[ ENTER ] (While ELIZA is typing)**: **Skip Animation** and display the full text instantly.
* **[ DEL ]**: Delete the last character.
* **[ ESC / \` ]**: Hardware Reset. Clears the screen and starts a new session.
* **[ , ] / [ . ] (Left / Right Arrows)**: Flip through suggestion pages when multiple results are found.
* **[ ; ] / [ / ] (Up / Down Arrows)**: Scroll through long articles.
* **[ - / = ]**: Adjust system volume (typing sound effects).

---

## 📖 Comprehensive User Manual

To get the most out of Wikipedia Offline ADV, it's important to understand how the ELIZA OS parses your requests.

### 🧠 The NLP Intent System
You don't need to type exact Wikipedia titles. The system understands natural language intents.
* **People & Leaders:** Ask *"Who is..."* or *"President of..."*
* **Geography:** Ask *"Where is..."* or *"Capital of..."*
* **Medicine:** Ask *"Symptoms of..."* or *"Cure for..."*
* **History:** Ask *"When did..."* or *"What year..."*
* **Data:** Ask *"Population of..."* or *"How many..."*

*Example:* If you type `"What is the capital of France?"`, the engine automatically strips the filler words, searches for `France`, scans the text specifically for geographical triggers, and extracts the sentence mentioning Paris.

### 🎲 Random Discovery Mode
Bored? Just type **`random`**, **`surprise me`**, or **`random fact`**. The engine will generate a random 64-bit pointer, dive into the database, and pull up a completely random article from human history out of the 6.4 million available.

### 🗂️ Navigating Suggestions
If you make a typo (e.g., *"Einstien"* instead of *"Einstein"*), ELIZA will offer up to 96 close matches. 
1. Use the **Left (`,`)** and **Right (`/`)** arrow keys to instantly flip through the pages of suggestions.
2. Type the number corresponding to your desired article (e.g., `14`) and press `[ENTER]`.
3. If none of the suggestions match, simply type `no` or `cancel` to return to the main menu.

---

## 🛑 Error Codes & Troubleshooting

* **"CRITICAL ERROR: No SD card detected"**: Ensure your MicroSD card is clicked fully into the slot and is formatted to FAT32 (exFAT is not supported by default ESP32 libraries).
* **"ERROR: Databanks missing or corrupted"**: You are missing `index_ptr.bin`, `index_data.bin`, or `dataX.bin`. The OS cannot index the raw data without these files. Check your file transfers.
* **"[TRUNCATED: Memory limit reached]"**: The article exceeds the 32KB safe-RAM buffer limit. The OS protects itself from crashing by cutting off the very end of massive articles.

---

## 💬 Feedback & Suggestions
If you find a bug or have a suggestion for the next version:
1. Go to the **[Issues]** tab at the top of this repository.
2. Click **[New Issue]**.
3. Describe your problem or idea in detail.

---

## ☕ Support the Project
Building custom NLP parsers and indexing engines for microcontrollers takes hundreds of hours of trial and error. If this tool has blown your mind or helped you, consider supporting further development!
* **[Support Zeloksa on Boosty](https://boosty.to/zeloksa)**

---
*Created by Zeloksa. Optimized for Cardputer ADV.*
