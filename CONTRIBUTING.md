# Contributing to AWS Security Specialty Study Guide

First off, thank you for considering contributing! This guide is made better by people like you.

## Ways to Contribute

### 📝 Add Study Notes

1. Fork the repository
2. Add your notes to the appropriate domain file in `docs/`
3. Ensure your notes reference official AWS documentation
4. Submit a pull request

### ❓ Suggest Quiz Questions

Quiz questions should:
- Have **one clear correct answer**
- Include **4 options** (A, B, C, D)
- Be **sourced from official AWS documentation**
- Include an **explanation** with a documentation link

**Format for suggesting questions:**

```markdown
## Question: [Your question here]

A. [Option A]
B. [Option B]
C. [Option C]
D. [Option D]

**Correct Answer:** [Letter]

**Explanation:** [Why this is correct, with AWS doc reference]

**Documentation:** [URL to official AWS docs]
```

Submit questions via:
- [Open an issue](../../issues/new) with the "quiz-question" label
- Or submit a PR adding to an existing quiz HTML file

### 🐛 Report Errors

Found something outdated or incorrect?

1. [Open an issue](../../issues/new)
2. Include:
   - What's wrong
   - Where you found it (file and line number if applicable)
   - What the correct information should be
   - Link to AWS documentation supporting the correction

### 📚 Add Video or Blog Resources

When adding resources:
- Ensure they're from official AWS sources (re:Invent, re:Inforce, AWS blogs)
- Include the full title and year
- Add to the appropriate section in the README or domain docs

## Pull Request Process

1. **Fork** the repository
2. **Create a branch** for your changes (`git checkout -b feature/add-kms-quiz`)
3. **Make your changes** following the existing style
4. **Test any quizzes** in a browser before submitting
5. **Commit** with a clear message
6. **Push** to your fork
7. **Open a Pull Request** with a description of your changes

## Code Style

### Markdown
- Use proper heading hierarchy
- Include table of contents for long documents
- Use code blocks for commands
- Link to official AWS documentation

### HTML Quizzes
- Follow the existing quiz template structure
- Keep all CSS and JavaScript inline (self-contained HTML)
- Test in multiple browsers
- Ensure mobile responsiveness

## Questions?

Feel free to [open an issue](../../issues/new) if you have questions about contributing.

---

Thank you for helping make this study guide better! 🙏
