# 🎮 Practice Quizzes

Interactive HTML-based quizzes for AWS Security Specialty exam preparation.

## Features

| Feature | Description |
|---------|-------------|
| **📚 Learn Mode** | Reveal answers one at a time with immediate feedback |
| **📝 Exam Mode** | Timed assessment (2.5 min/question), submit all at once |
| **🔀 Shuffle** | Questions and options randomize on every restart |
| **✅ Pass/Fail** | 80% threshold with clear visual feedback |
| **📖 Explanations** | Detailed answers with AWS documentation links |

## Available Quizzes

| Quiz | Topic | Questions | Domain |
|------|-------|-----------|--------|
| [guardduty-extended-threat-detection.html](./guardduty-extended-threat-detection.html) | GuardDuty Extended Threat Detection | 15 | Domain 1 |

## How to Use

### Option 1: Direct File Access
Simply double-click any `.html` file to open in your default browser.

### Option 2: Local HTTP Server (Recommended)

```bash
# Navigate to quizzes folder
cd quizzes

# Start a simple HTTP server
python -m http.server 8080

# Open in browser
# http://localhost:8080/guardduty-extended-threat-detection.html
```

### Option 3: GitHub Pages
If this repo is published to GitHub Pages, quizzes will be available at:
```
https://radulupan.github.io/aws-security-specialty-study-guide/quizzes/
```

## Quiz Modes

### 📚 Learn Mode
- Answer one question at a time
- Click "Show Answer" to reveal if correct
- See explanation and documentation link immediately
- Good for: Initial learning, studying new topics

### 📝 Exam Mode
- Timer starts (2.5 minutes per question)
- Answer all questions before submitting
- All answers revealed at once after submission
- Shows pass/fail (80% threshold)
- Good for: Testing yourself, simulating exam conditions

## Requesting New Quizzes

Want a quiz on a specific topic? [Open an issue](../../../issues/new) with:
- Topic name
- AWS service(s) involved
- Any specific areas to focus on

## Contributing Quiz Questions

See [CONTRIBUTING.md](../CONTRIBUTING.md) for guidelines on submitting quiz questions.

---

**Good luck with your exam preparation! 🎓**
