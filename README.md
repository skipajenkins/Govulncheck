---

# 🐹 Govulncheck — Go Language Tag Parser (CLI Tool)

This project demonstrates:

- Building a basic **Go CLI application**
- Parsing command-line arguments
- Validating structured input
- Using external Go modules
- Handling errors gracefully in Go

---

## 🎯 Learning Objectives

By working through this project, you will learn:

- How to build command-line tools in Go
- How to read command-line arguments using `os.Args`
- How to parse and validate language tags
- How to use external Go packages
- How to structure simple Go projects

---

## 📁 Project Structure

- Govulncheck/
  - go.mod
  - go.sum
  - main.go
  - README.md

---

## ⚙️ Prerequisites

Make sure you have the following installed:

| Tool | Purpose |
|------|----------|
| Go   | Go compiler & runtime |
| Git  | Version control       |
| Terminal / Shell | Running CLI commands |

---

## 🦫 Installing Go

### Step 1: Check if Go is installed

```bash
go version
Step 2: Install Go (if missing)
```
Linux / macOS:
```bash
curl -OL https://go.dev/dl/go1.25.6.linux-amd64.tar.gz
sudo tar -C /usr/local -xvf go1.25.6.linux-amd64.tar.gz
export PATH=$PATH:/usr/local/go/bin
```
Windows:
```bash
https://go.dev/dl/
```
---

## 🚀 Getting Started
Step 1: Clone the Repository
```bash
git clone https://github.com/skipajenkins/Govulncheck.git
cd Govulncheck
```
Step 2: Install Dependencies
```bash
go mod tidy
```
Step 3: Build the Program
```bash
go build -o govulncheck
```
Step 4: Run the Program
```bash
./govulncheck en-US fr-FR invalid-tag zh-Hans
```

---

## 🧪 Example Output
```bash
en-US: tag en-US
fr-FR: tag fr-FR
invalid-tag: error: language: tag is not well-formed
zh-Hans: tag zh-Hans
```

---

## 🧠 How It Works

- Reads command-line arguments
```bash
os.Args[1:]
```
- Parses language tags
```bash
language.Parse(arg)
```
- Validates parsed values
```bash
if tag == language.Und
```
- Prints formatted output
```bash
fmt.Printf("%s: tag %s\n", arg, tag)
```

---

## 🧩 Code Overview
```bash
main.go
package main

import (
	"fmt"
	"os"

	"golang.org/x/text/language"
)

func main() {
	for _, arg := range os.Args[1:] {
		tag, err := language.Parse(arg)
		if err != nil {
			fmt.Printf("%s: error: %v\n", arg, err)
		} else if tag == language.Und {
			fmt.Printf("%s: undefined\n", arg)
		} else {
			fmt.Printf("%s: tag %s\n", arg, tag)
		}
	}
}
```

---

## 🧠 Key Concepts
| Concept | Explanation |
|----------|-------------|
| CLI Tool | Program executed from terminal |
| os.Args | Reads command-line parameters |
| Go Modules | Dependency management |
| Error Handling | Graceful failure control |
| External Packages | Using third-party libraries |

---

## 📦 Dependencies
```bash
golang.org/x/text
```
Used for:

Language tag parsing

BCP 47 validation

🔬 Example Test Cases

Valid Inputs:
```bash
./govulncheck en-US fr-FR de-DE zh-Hans
```
Invalid Inputs:
```bash
./govulncheck invalid language-tag 1234
```

---

## 🏗️ Built With

- Go (Golang)

- Go Modules

- golang.org/x/text/language

---

## 📜 License

This project is licensed under the MIT License — free to use, modify, and distribute.

---
