# 1. Justification

## What are we doing?

This document presents the results of a comprehensive **accessibility audit** for the Pirate A11y website. The goal is to identify barriers that could prevent people with disabilities from accessing and interacting effectively with the website.

## Why is this important?

Ensuring digital accessibility:
- Promotes **inclusive experiences** for all users, regardless of ability.
- Helps meet **legal obligations** under international laws and standards (such as Section 508 in the U.S.).
- Improves **SEO and usability** for all users, not just those with disabilities.
- Reduces the risk of legal complaints and reputational harm.

## Which standards and how did we apply them?

We followed the **Web Content Accessibility Guidelines (WCAG) 2.1**, specifically focusing on levels **A and AA**, as well as key criteria from **Section 508**.

This audit was conducted using:
- **Manual testing** with keyboard navigation and screen readers (VoiceOver).
- **Automated tools** (WAVE, browser devtools) for contrast, structure, and ARIA validation.
- **Code inspection** to analyze semantic HTML and focus management.

## Which principles guide our audit?

Our approach is based on the four core principles of WCAG, known as **POUR**:

- **Perceivable** – Information must be presented in ways that users can perceive (e.g., text alternatives for images).
- **Operable** – Interface elements must be usable via keyboard and assistive technologies.
- **Understandable** – Content must be readable and interfaces predictable.
- **Robust** – Content must work with current and future technologies, including screen readers and browsers.

Together, these principles ensure that the web experience is accessible to as many people as possible.

# 2. Testing Approach

To ensure a thorough and meaningful accessibility audit, we applied a **hybrid testing approach** that combines both **manual inspection** and **automated analysis**.

## Manual Testing

Manual testing allows us to capture accessibility issues that automated tools typically miss, especially those related to context, meaning, and user experience.

We manually tested using:

- **Keyboard navigation only**: Checked if all interactive elements are reachable, logically ordered, and operable using the `Tab`, `Enter`, and `Space` keys.
- **Screen reader testing**: Used **VoiceOver** (macOS) to verify how well content is announced, whether labels are present, and if the experience is consistent.
- **Code inspection**: Reviewed HTML, ARIA roles, labels, and heading structures to identify semantic and structural issues.

## Automated Testing

Automated tools help us quickly detect common technical errors that affect accessibility, such as color contrast or missing attributes.

We used:

- ✅ **WAVE** (Web Accessibility Evaluation Tool): For quick identification of issues such as missing alt text, color contrast failures, and structural errors.
- ✅ **Browser DevTools**: To analyze computed roles, names, and keyboard focus.
- ✅ **Color Contrast Checkers**: To validate compliance with **WCAG 1.4.3 (AA)** and **1.4.6 (AAA)**.

By combining these methods, we created a more complete picture of the accessibility state of the website.

# 3. Findings 

Below is a detailed list of manually detected accessibility issues, grouped by WCAG principle, with links to the official documentation for each criterion.

##  Perceivable

| #  | Issue Description                                         | WCAG Criterion & Link                                                                                          | Priority | Recommendation                          |
|----|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|----------|------------------------------------------|
| 1  | Images missing alt text or need to be more especific                                   | [WCAG 1.1.1 Non-text Content (A)](https://www.w3.org/TR/WCAG21/#non-text-content)   | High    | Add meaningful `alt` attribute           |
| 2  | Low contrast text                                        | [WCAG 1.4.3 Contrast (AA)](https://www.w3.org/TR/WCAG21/#contrast-minimum)                 | High    | Ensure 4.5:1 contrast ratio              |
| 3  | Non-scalable layouts                                     | [WCAG 1.4.10 Reflow (AA)](https://www.w3.org/TR/WCAG21/#reflow)                                    | Medium  | Use relative units (`em`, `%`)           |
| 4  | Small clickable icons (social links, phone)              | [WCAG 2.5.5 Target Size (AAA)](https://www.w3.org/TR/WCAG21/#target-size)                        | Medium  | Expand hit area to ≥44×44px              |
| 5  | No visible focus indicator on focus               | [WCAG 1.4.13 Content on Hover or Focus (AA)](https://www.w3.org/TR/WCAG21/#content-on-hover-or-focus)  | Medium  | Add visible focus states                  |

---

##  Operable

| #  | Issue Description                                      | WCAG Criterion & Link                                                                                   | Priority | Recommendation                         |
|----|--------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|----------|-----------------------------------------|
| 1  | Missing "Skip to content" link                        | [WCAG 2.4.1 Bypass Blocks (A)](https://www.w3.org/TR/WCAG21/#bypass-blocks)   | High    | Add a visible skip-link at top         |
| 2  | Navigation not keyboard-accessible on carousel                    | [WCAG 2.1.1 Keyboard (A)](https://www.w3.org/TR/WCAG21/#keyboard)                       | High    | Ensure keyboard operability             |
| 3  | No visible focus outline on Famous Pirates Dropdown Toogle                             | [WCAG 2.4.7 Focus Visible (AA)](https://www.w3.org/TR/WCAG21/#focus-visible)             | High    | Implement visible `:focus` styles       |
| 4  | Missing focus on form expansion                       | [WCAG 2.4.7 Focus Visible (Level AA)](https://www.w3.org/WAI/WCAG21/Understanding/focus-visible.html)         | Medium  | Ensure each item receiving focus has a visible indicator |
| 5  | Auto-rotating carousel with no controls               | [WCAG 2.2.2 Pause, Stop, Hide (AA)](https://www.w3.org/TR/WCAG21/#pause-stop-hide)       | Medium  | Try to freeze the animation                 |

---

##  Understandable

| #  | Issue Description                             | WCAG Criterion & Link                                                                                   | Priority | Recommendation                          |
|----|-----------------------------------------------|-----------------------------------------------------------------------------------------------------------|----------|------------------------------------------|
| 1  | Nondescriptive link text ("click here", "more") | [WCAG 2.4.4 Link Purpose (A)](https://www.w3.org/TR/WCAG21/#link-purpose-in-context)        | High    | Use descriptive link text                |
| 2  | No instructions for required fields           | [WCAG 3.3.2 Labels or Instructions (A)](https://www.w3.org/TR/WCAG21/#labels-or-instructions)   | Medium  | Clearly indicate required fields          |
| 3  | Inputs lack labels and placeholders           | [WCAG 1.3.1 Info and Relationships (A)](https://www.w3.org/TR/WCAG21/#info-and-relationships)   | High    | Use `label for` and relevant placeholder  |

---

##  Robust

| #  | Issue Description                                  | WCAG Criterion & Link                                                                                   | Priority | Recommendation                            |
|----|----------------------------------------------------|-----------------------------------------------------------------------------------------------------------|----------|--------------------------------------------|
| 1  | `<a>` tags misused with `role="button"`            | [WCAG 4.1.2 Name, Role, Value (A)](https://www.w3.org/TR/WCAG21/#name-role-value)             | Medium  | Use correct elements; avoid redundant roles |
| 2  | Text in `<p>` used as headings                     | [WCAG 1.3.1 Info and Relationships (A)](https://www.w3.org/TR/WCAG21/#info-and-relationships)   | Medium  | Use semantically correct heading tags       |
| 3  | `onclick` used instead of `target="_blank"`        | [WCAG 2.1.1 Keyboard (A)](https://www.w3.org/TR/WCAG21/#keyboard)                       | High    | Use proper HTML attributes (`target`, `rel`) |
| 4  | Missing `rel="noopener noreferrer"` on external links | Best security practices (not WCAG-specific)                                                                | Medium  | Add `rel` attribute to external links       |
| 5  | Skips from `h2` to `h4` incorrectly                 | [WCAG 1.3.1 Info and Relationships (A)](https://www.w3.org/TR/WCAG21/#info-and-relationships)   | Medium  | Maintain heading hierarchy                  |
| 6  | `<div>` used instead of `<section>`                | HTML5 semantic best practices                                                                              | Low     | Use structural HTML elements                |
| 7  | `.thumbnail` lacking semantic wrapper (`<article>`) | HTML5 semantic best practices                                                                              | Low     | Use `<article>` for independent content     |
| 8  | Excessive non-semantic `<div>` usage               | HTML5 semantic best practices                                                                              | Low     | Replace `div` with semantic tags            |

Below is a screenshot showing the results from an automated accessibility evaluation conducted using the WAVE tool by WebAIM. This scan highlights various accessibility issues detected on the page, including errors, contrast problems, alerts, and ARIA usage.

The report indicates 14 errors, 37 contrast errors, and 83 alerts, along with 63 accessibility features and 38 structural elements. These findings serve as a preliminary overview and complement the manual audit detailed in the following sections.

![wave test](/docs/wave-test.png "This is a screenshot of the results.")
---

# 4. Prioritization Strategy

In order to efficiently address the accessibility issues discovered during this audit, we will follow a prioritization strategy based on  **WCAG conformance level (A, AA, AAA).** 

### 🚦 Priority Levels

| Priority | Meaning |
|----------|---------|
| 🔴 High   | Critical for accessibility and/or violates Level A or Level AA WCAG. Blocks users from completing core tasks. Should be fixed immediately. |
| 🟡 Medium | Important issues that affect usability but might have workarounds. These usually correspond to Level AA or AAA. |
| 🟢 Low    | Best practices or minor improvements. Low impact on accessibility. Can be resolved in later iterations. |

---

### 🎯 80/20 Pareto Principle Application

To optimize effort and impact, we apply the **Pareto Principle**, also known as the **80/20 rule**:

> **80% of accessibility barriers come from 20% of the issues.**

Based on this, we will **prioritize the fixes** that affect the most critical paths of the website and **repeat across multiple elements or pages**, such as:

- Missing or improper `alt` text on images (WCAG 1.1.1)
- Keyboard navigation issues (WCAG 2.1.1, 2.4.7)
- Missing visible focus indicators (WCAG 2.4.7)
- Nondescriptive links (WCAG 2.4.4)
- Forms without labels or instructions (WCAG 3.3.2, 1.3.1)

These five areas are responsible for **the majority of the accessibility friction** and will be the initial focus of remediation.

---

### ✅ How We Will Proceed

1. **Quick Wins (High Priority + Easy to Fix)**

2. **Structural Adjustments (Medium Priority)**

3. **Progressive Enhancements (Low Priority)**

---
