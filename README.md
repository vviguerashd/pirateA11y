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

### Perceivable

| #  | Description                                           | HTML Element                        | WCAG Violation                                                                                       | Expected Behavior / Recommended Fix                       |
|----|-------------------------------------------------------|-------------------------------------|------------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| 1  | Images missing alt text or need to be more specific   | `<img>`                              | [WCAG 1.1.1 Non-text Content (A)](https://www.w3.org/WAI/WCAG21/Understanding/non-text-content.html) | Add meaningful `alt` attribute to all images              |
| 2  | Low contrast text                                     | `<p>`, `<a>`, `<h2>`, `<h3>`                         | [WCAG 1.4.3 Contrast (AA)](https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum.html)        | Ensure minimum 4.5:1 contrast ratio                      |
| 3  | Non-scalable layouts                                  | `<div>`, layout containers           | [WCAG 1.4.10 Reflow (AA)](https://www.w3.org/WAI/WCAG21/Understanding/reflow.html)                   | Use relative units (`em`, `%`) to allow zoom/reflow      |
| 4  | Small clickable icons (social links, phone)           | `<a>` (wrapped around icons/images) | [WCAG 2.5.5 Target Size (AAA)](https://www.w3.org/WAI/WCAG21/Understanding/target-size.html)         | Expand hit area to ≥ 44x44px                             |
| 5  | No visible focus indicator on focus                   | Interactive elements                | [WCAG 1.4.13 Content on Hover or Focus (AA)](https://www.w3.org/WAI/WCAG21/Understanding/content-on-hover-or-focus.html) | Add visible focus states (e.g. outline or border) |
---

##  Operable

| # | Description | HTML Element | WCAG Violation | Expected Behavior / Recommended Fix |
|---|-------------|---------------|----------------|-------------------------------------|
| 1 | Missing "Skip to content" link | `<a>` (missing) | [WCAG 2.4.1 – Bypass Blocks (A)](https://www.w3.org/WAI/WCAG21/Understanding/bypass-blocks.html) | Add a visible skip link at top. |
| 2 | Carousel not keyboard accessible | `<div class="carousel slide">` | [WCAG 2.1.1 – Keyboard (A)](https://www.w3.org/WAI/WCAG21/Understanding/keyboard.html) | Ensure keyboard navigation and controls. |
| 3 | No focus on dropdown toggle | `<button class="dropdown-toggle">` | [WCAG 2.4.7 – Focus Visible (AA)](https://www.w3.org/WAI/WCAG21/Understanding/focus-visible.html) | Add visible `:focus` styles. |
| 4 | Missing focus form | `<form id="login-form">`  | [WCAG 2.4.7 – Focus Visible (AA)](https://www.w3.org/WAI/WCAG21/Understanding/focus-visible.html) | Add focus to inputs. |

---

##  Understandable

| # | Description | HTML Element | WCAG Violation | Expected Behavior / Recommended Fix |
|---|-------------|---------------|----------------|-------------------------------------|
| 1 | Links use vague text like "click here" | `<a>` | [WCAG 2.4.4 Link Purpose (A)](https://www.w3.org/WAI/WCAG21/Understanding/link-purpose-in-context.html) | Use descriptive text that conveys the link's destination or purpose |
| 2 | No guidance for required form fields | `<form>` / `<input required>` | [WCAG 3.3.2 Labels or Instructions (A)](https://www.w3.org/WAI/WCAG21/Understanding/labels-or-instructions.html) | Add clear instructions indicating required fields |
| 3 | Inputs lack visible labels and placeholders | `<input>` / `<label>` | [WCAG 1.3.1 Info and Relationships (A)](https://www.w3.org/WAI/WCAG21/Understanding/info-and-relationships.html) | Add `label for` and appropriate placeholder text |
---

##  Robust

| # | Description                               | HTML Element         | WCAG Violation                                | Expected Behavior / Recommended Fix                            |
|---|-------------------------------------------|----------------------|------------------------------------------------|----------------------------------------------------------------|
| 1 | Link element used as button               | `<a role="button">`  | [WCAG 4.1.2 Name, Role, Value (A)](https://www.w3.org/TR/WCAG21/#name-role-value)               | Use `<button>` or remove unnecessary role.                     |
| 2 | Paragraphs used as headings               | `<p>`                | [WCAG 1.3.1 Info and Relationships (A)](https://www.w3.org/TR/WCAG21/#info-and-relationships)          | Replace with semantic heading tags (`<h1>`–`<h6>`).            |
| 3 | Uses `onclick` without keyboard fallback  | `onclick` attribute  | [WCAG 2.1.1 Keyboard (A)](https://www.w3.org/TR/WCAG21/#keyboard)                        | Add keyboard event or use `href` and `target`, `rel`.         |
| 4 | Missing `rel` on external links           | `<a target="_blank">`| Not WCAG (Best Practice)                       | Add `rel="noopener noreferrer"` for security.                 |
| 5 | Heading level skipped (h2 → h4)           | `<h4>`               | [WCAG 1.3.1 Info and Relationships (A)](https://www.w3.org/TR/WCAG21/#info-and-relationships)          | Maintain correct heading order.                               |
| 6 | Div used instead of section               | `<div>`              | HTML5 Semantic Best Practice                   | Replace with `<section>` for structural meaning.               |
| 7 | Thumbnail lacks semantic container        | `.thumbnail`         | HTML5 Semantic Best Practice                   | Wrap in `<article>` if it's standalone content.               |
| 8 | Excessive use of `<div>`s                 | `<div>`              | HTML5 Semantic Best Practice                   | Replace with semantic tags like `<main>`, `<aside>`, etc.     |

Below is a screenshot showing the results from an automated accessibility evaluation conducted using the WAVE tool by WebAIM. This scan highlights various accessibility issues detected on the page, including errors, contrast problems, alerts, and ARIA usage.

The report indicates 14 errors, 37 contrast errors, and 83 alerts, along with 63 accessibility features and 38 structural elements. These findings serve as a preliminary overview and complement the manual audit detailed in the following sections.

**WAVE automated test**

![wave test](/docs/wave-test.png "This is a screenshot of the results.")

---

# 4. Prioritization Strategy

In order to efficiently address the accessibility issues discovered during this audit, we will follow a prioritization strategy based on  **WCAG conformance level (A, AA, AAA).** 

### 🎯 80/20 Pareto Principle Application

To optimize effort and impact, we apply the **Pareto Principle**, also known as the **80/20 rule**:

> **80% of accessibility barriers come from 20% of the issues.**

Based on this, we will **prioritize the fixes** that affect the most critical paths of the website and **repeat across multiple elements or pages**, such as:

- Missing or improper `alt` text on images (WCAG 1.1.1)
- Keyboard navigation issues (WCAG 2.1.1, 2.4.7)
- Contrast on text elements (WCAG 1.4.3 Contrast) (AA)
- Nondescriptive links (WCAG 2.4.4)
- Font sizing with relative units for accessibility and scalability (WCAG 1.4.4 – Resize text)

These five areas are responsible for **the majority of the accessibility friction** and will be the initial focus of remediation.

---

### ✅ How We Will Proceed

1. **Quick Wins (High Priority + Easy to Fix)**

2. **Structural Adjustments (Medium Priority)**

3. **Progressive Enhancements (Low Priority)**

---
# 5. Code Fixes Summary

## 1. Missing or improper `alt` text on images (WCAG 1.1.1)

During the process of adding alt attributes to all images on the page, I also made a few additional adjustments to improve the overall accessibility and user experience.

-	Alt texts were written to be clear and descriptive, avoiding redundancy.
-	In some sections, I removed repetitive elements, especially in areas with multiple links to the same resource or section. This was done to streamline screen reader navigation and avoid overwhelming users with repeated announcements.
- I made the corrections on DevTools, sadly I couldn't do it on the boostrap file.
- The changes also were applied to the footer elements

**Before fix**
![This is an alt text.](/docs/element-before-3.png "This is the element before.")

**Temporary fix in DevTools**
![This is an alt text.](/docs/element-correction-3.png "This is the fix on DevTools.")

**After fix**
![This is an alt text.](/docs/element-after-3.png "This is the element after the fix")
![This is an alt text.](/docs/element-after-2.1.png "This is the fix on DevTools.")


The goal was not only to meet WCAG guidelines but also to create a smoother, more usable experience for everyone.

## 2. Keyboard navigation issues (WCAG 2.1.1, 2.4.7)

Focus indicator hidden by Bootstrap

One accessibility issue found was that the keyboard focus indicator for the “Famous Pirates” dropdown menu was not visible when navigating using the Tab key. This was due to the following CSS rule from Bootstrap:

```
.dropdown-toggle:focus {
  outline: 0;
}
```
This rule suppresses the default focus outline, making it difficult for keyboard users to know where they are on the page. This violates:
	•	WCAG 2.1.1 Keyboard (A) – All functionality must be accessible via keyboard.
	•	WCAG 2.4.7 Focus Visible (AA) – A visible focus indicator must be present for interactive elements.

I temporarily resolved this by disabling the outline: 0 rule in DevTools, which restored the default focus style. However, I wasn’t able to permanently fix this in the source code because the style is embedded in the minified Bootstrap file.


**Before fix** 

![This is an alt text.](/docs/element-before-1.png "This is the element before.")

**Temporary fix in DevTools** 

![This is an alt text.](/docs/element-correction-1.png "This is the fix on DevTools.")

**After fix** 

![This is an alt text.](/docs/element-after-1.png "This is the element after the fix")

## 3. Contrast on text elements (WCAG 1.4.3 Contrast) (AA)

The paragraph shown in the image meets the required contrast ratio.

- **Foreground**: #000000
- **Background**: #ffffff
- **Contrast ratio**: 19.77 ✅

This value is well above the minimum threshold of 4.5:1 for normal text, meaning it's accessible and complies with WCAG AA.

**Before fix** 

![This is an alt text.](/docs/element-before-2.png "This is the element before.")

**Fix in style.css** 

![This is an alt text.](/docs/element-correction-2.png "This is the fix on DevTools.")

**After fix** 

![This is an alt text.](/docs/element-after-2.png "This is the element after the fix")

## 4. Nondescriptive links (WCAG 2.4.4)

Some links in the code, like “Email”, don’t give enough context for screen reader users. To improve accessibility, I replaced these with more descriptive phrases like “Email Kevin”, and added aria-label attributes where needed. This makes the purpose of each link clearer and helps users navigate the page more easily.

The original code used onclick="window.open(this.href); return false;", which prevents keyboard users and assistive technologies from reliably triggering the link. To make the link fully accessible and keyboard-navigable (WCAG 2.1.1 – Keyboard), we replaced it with the semantic HTML approach: using target="_blank" to open the link in a new tab and rel="noopener" for security. The updated version keeps the intended behavior while ensuring better accessibility and performance.

## 5. Font sizing with relative units for accessibility and scalability (WCAG 1.4.4 – Resize text)

To enhance accessibility and scalability across devices and user preferences, all font-size values have been converted from fixed px units to relative rem units. This change ensures that text scales appropriately based on the user’s default browser settings, which is particularly beneficial for users with low vision who rely on custom zoom levels. Using rem also aligns with responsive design best practices and helps meet WCAG 1.4.4 (Resize Text) and 1.4.12 (Text Spacing) guidelines.

## 6. The results after the fixes in WAVE:

**WAVE final automated test**

![wave test](/docs/wave-test-2.png "This is a screenshot of the results.")

# 6. Final Notes and Areas for Improvement

While significant accessibility issues have been identified and addressed—such as improving link descriptions, ensuring adequate text contrast, and using rem units for better scalability—there is still important work ahead. Some issues remain unresolved, and others could not be fixed directly due to limitations in editing the Bootstrap framework from within my project files.

It would have been ideal to configure Bootstrap overrides or custom themes from my own CSS files instead of applying temporary changes via DevTools. This approach would ensure that improvements persist and scale with future updates.

Accessibility is an ongoing process, not a one-time task. This audit represents a solid starting point, but continued iteration and user testing will be necessary to achieve full compliance and deliver an inclusive user experience for all.