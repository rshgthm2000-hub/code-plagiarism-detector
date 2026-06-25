# Token-Based Plagiarism Detection System

## 📌 Overview

This project implements a highly efficient plagiarism detection engine for tokenized source code submissions. Instead of comparing raw text strings, the system processes sequences of integers (tokens), making it resilient against variable renaming or formatting changes.

The engine identifies both exact and approximate similarities between two token streams using Rabin-Karp rolling hashes and dynamic gap-tolerant expansion algorithms.

---

## 🚀 Algorithmic Parameters & Logic

The system is hardcoded with specific threshold parameters to ensure high-confidence match reporting:

### 1. Exact Match Detection
* **Hashing Strategy:** Utilizes Rabin–Karp rolling hashes (Base `257`, Modulo `1e9 + 7`) for initial fixed-length windows of **5 tokens**.
* **Match Verification:** Hashes are compared, and identical sequences are verified token-by-token.
* **Minimum Threshold:** A sequence is only recorded as a valid exact match if it spans **at least 10 consecutive tokens**.
* **Non-Overlapping Guarantee:** Implements boolean tracking maps (`visited1`, `visited2`) to prevent counting overlapping sequence matches.

### 2. Approximate Match Expansion
* **Anchor Expansion:** Takes the exact match indices and dynamically expands them both forward and backward.
* **Configurable Gap Tolerance:** Allows up to **20% structural drift/gaps** (`gap_fraction = 0.20`) between the two token sequences to catch injected or deleted statements.
* **Minimum Threshold:** An approximate match is only logged as the maximum if its total expanded length is **at least 30 tokens**.

---

## 📊 Return Output Format

The core `match_submissions` function evaluates the token arrays and returns a 5-element `std::array<int, 5>` mapping the following metrics:

| Index | Metric | Description |
| :--- | :--- | :--- |
| `[0]` | **Plagiarism Flag** | Binary `1` if total exact match length is **$\ge$ 40%** of the shorter submission, else `0`. |
| `[1]` | **Total Exact Match** | The sum of all non-overlapping exact match sequences ($\ge$ 10 tokens). |
| `[2]` | **Longest Approx Match** | The length of the single largest gap-tolerant matching segment ($\ge$ 30 tokens). |
| `[3]` | **Submission 1 Index** | The starting index of the longest approximate match in the first array. |
| `[4]` | **Submission 2 Index** | The starting index of the longest approximate match in the second array. |
---

## 💻 Technologies Used

* **Language:** C++
* **Header Dependencies:** `<vector>`, `<unordered_map>`, `<array>`, `<span>`, `<tuple>`
* **Data Structures:** Hash Maps for $O(1)$ token sequence lookups.
* **Algorithms:** Rabin–Karp Rolling Hashing, Sliding Window Validation, Greedy Bidirectional Alignment.

---

## 📂 Applications

* Academic plagiarism detection for programming courses (identifying structural clones).
* Source code similarity and clone-detection analysis.
* Submission comparison and anomaly detection for competitive programming.
* Large-scale code repository inspection and intellectual property verification.

---

## 🧑‍💻 Author Profile

| Detail Field | Associated Information |
| :--- | :--- |
| **Name** | RISHI GOUTHAM |
| **Technical Focus** | C++ \| Advanced Algorithms \| Computer Science Student |
| **Project Context** | Developed as a data structures and algorithms project exploring efficient techniques for source code similarity detection. |
