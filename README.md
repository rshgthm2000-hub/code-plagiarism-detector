# Token-Based Plagiarism Detection System

## 📌 Overview

This project implements a plagiarism detection system for tokenized source code submissions. It identifies both exact and approximate similarities between two submissions using rolling hash techniques and gap-tolerant matching.

The system is designed to detect copied code even when minor modifications, insertions, or deletions have been made.

---

## 🚀 Features

* **Exact Match Detection:** Utilizes Rabin–Karp rolling hashes for fixed-length token windows.
* **Non-Overlapping Matches:** Identifies and isolates distinct, non-overlapping matching code segments.
* **Approximate Matching:** Offers configurable gap tolerance to catch structural modifications.
* **Longest Similar Segment Identification:** Automatically pinpoints the single largest region of duplication.
* **Similarity Scoring:** Generates exact metrics and binary plagiarism flags efficiently.
* **Efficient Indexing:** Uses optimized hash-based structures to scale across large token streams.

---

## 🛠️ Algorithm

### 1. Exact Matching
1. Generate rolling hashes for fixed-length token windows.
2. Store hashes and their corresponding starting positions.
3. Compare hash values across submissions.
4. Verify matches and record non-overlapping exact match sequences.

### 2. Approximate Matching
1. Start from anchors identified during the exact matching phase.
2. Expand matches dynamically both forward and backward.
3. Allow a limited number of gaps or structural shifts while preserving alignment.
4. Compute the longest approximate matching segment.

---

## 📊 Output

The system evaluates the inputs and returns:
* **Plagiarism Flag:** Binary flag (0/1) indicating if the similarity threshold is exceeded.
* **Total Exact Match Length:** Total count of exactly matched tokens.
* **Longest Approximate Match:** Length of the longest structurally similar token block.
* **Match Target Positions:** Starting index of the dominant match in both Submission 1 and Submission 2.

---

## 💻 Technologies Used

* **Language:** C++
* **Data Structures:** STL Containers (Hash Maps, Vectors)
* **Algorithms:** Rabin–Karp Rolling Hashing, Sequence Matching, Greedy Tracking

---

## 📂 Applications

* Academic plagiarism detection for programming courses.
* Source code similarity and code-clone analysis.
* Submission comparison and anomaly detection for competitive programming.
* Large-scale code repository inspection and intellectual property verification.

---

## 🧑‍💻 Author

**RISHI GOUTHAM** C++ | Advanced Algorithms | Computer Science Student  

*Developed as a data structures and algorithms project exploring efficient techniques for source code similarity detection.*
