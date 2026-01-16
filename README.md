# 🎵 Lyrics Guesser (Console-Based Game)

![Language](https://img.shields.io/badge/Language-C-blue)
![Platform](https://img.shields.io/badge/Platform-Windows-0078D6)
![Subject](https://img.shields.io/badge/Course-CPE100%20Computer%20Programming-green)

> **"Can you guess the song from a single line?"**
> A C-based console application that challenges players to identify songs from lyrics, featuring file manipulation and dynamic song management.

---

## 📄 Full Project Report
This repository contains the source code and the detailed project report (including Flowcharts and User Manual).

## https://drive.google.com/file/d/1OFMk9OW2o6Lb7tqYyHVmcXWgMLrJw7n9/view?usp=drive_link
*(Note: Please click the link above to view the detailed documentation)*

---

## 🔍 Project Overview

### 🎯 Objective
To apply fundamental programming concepts (Functions, Pointers, File I/O) to create an interactive game. The program reads song lyrics from text files stored in categorized folders and randomizes questions for the user.

### 🛠️ Key Features
* **Game Mode:** Randomly selects a lyric snippet and asks the user to choose the correct song title.
* **Song Management:** Users can **Add new songs** directly through the console, which creates new `.txt` files in the database.
* **Search System:** Functionality to search for specific lyrics or song titles.
* **File Handling:** Uses `windows.h` API to traverse directories and read song data dynamically.

---

## ⚙️ Logic & Architecture

### Flowchart
The program follows a modular structure, separating the Game Loop, File Reading, and Display Logic.

![System Flowchart](flowchart.png)

### 💻 Code Highlight (File Traversal)
The system uses Windows API to scan for song files in directories automatically.

```c
// Sample Code: Scanning for .txt files in a directory
void AllSong(const char *path) {
    char searchPath[MAX_PATH];
    sprintf(searchPath, "%s\\*", path);
    WIN32_FIND_DATA findFileData;
    HANDLE hFind = FindFirstFile(searchPath, &findFileData);
    
    // Loop to find all text files
    do {
        if (strstr(findFileData.cFileName, ".txt") != NULL) {
            printf("%s\n", findFileData.cFileName);
        }
    } while (FindNextFile(hFind, &findFileData) != 0);
}
