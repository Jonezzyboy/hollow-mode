---
name: hollow-mode
description: Use when user wants TDD scaffolding for learning but will write implementation themselves - creates tests and empty stubs without filling in code
---

# Hollow Mode

## Overview

**Hollow mode creates TDD scaffolding with empty implementations for learning.**

You provide architecture and tests. User writes the code. This teaches active implementation, not passive reading.

**Core principle:** Implementation by user = learning. Implementation by you = convenience that defeats learning.

## When to Use

Use when:
- User explicitly requests learning/practice exercise
- User wants TDD setup but will implement themselves
- User says "leave the implementation empty"
- Building coding challenges or exercises
- Teaching through guided practice

**Do NOT use when:**
- User wants a working solution
- Production code needed
- User doesn't mention learning/practice
- Time-critical feature work

## The Hollow Process

### 1. Collaborative Design Planning - REQUIRED FIRST STEP

**STOP. Do NOT create any files until you ask design questions.**

Even if the request seems clear ("help me with a shopping cart"), you MUST ask:

```markdown
Before I create any scaffolding, let me understand your learning goals:

1. **Language & Framework**: Which language and testing framework? (Python/pytest, JS/Jest, etc.)
2. **Scope**: What functionality should this cover?
3. **Edge Cases**: What should we test? (nulls, empty, invalid input, etc.)
4. **Learning Focus**: What do you want to practice?
   - Algorithm design?
   - Error handling?
   - Data structures?
   - API design?
   - Something else?
```

**Why this matters:**
- Understanding learning goals shapes test design
- Questions aren't about minimum info - they reveal what user needs to practice
- "Shopping cart" could mean 100 different scopes
- Your assumptions about scope may not match their learning needs

### 2. Test Case Discussion

**Collaborate on test cases:**

```markdown
I'll create tests for:
- ✓ Core functionality (happy path)
- ✓ Edge cases (nulls, empty, boundary conditions)
- ✓ Error cases (invalid input, exceptions)
- ✓ [Specific to learning goal]

Does this cover what you want to practice? Any other scenarios?
```

**Get buy-in before writing tests.** User should understand what they'll implement.

### 3. Create Tests First

Write comprehensive, well-organized tests:

```javascript
// Good test structure
describe('Feature Name', () => {
  describe('Core functionality', () => {
    test('should handle basic case', () => {
      expect(functionName(input)).toBe(expected);
    });
  });

  describe('Edge cases', () => {
    test('should handle null input', () => {
      expect(functionName(null)).toBe(false);
    });
  });
});
```

**Test quality matters:** Clear test names, good organization, comprehensive coverage.

### 4. Generate Empty Stubs

Create function signatures with NO implementation:

```javascript
// ✅ GOOD: Truly empty
function functionName(param) {
  // TODO: Implement [brief description]
  // Tests expect: [what behavior tests check for]
}

// ✅ GOOD: Python empty
def function_name(param):
    """
    Brief description of what this should do.

    Args:
        param: Description

    Returns:
        Expected return type and meaning
    """
    pass

// ❌ BAD: Has implementation
function functionName(param) {
  return param.split('').reverse().join('');
}

// ❌ BAD: Partial implementation "hints"
function functionName(param) {
  // Check if param is valid
  // Split and process
  // Return result
  return null; // Replace this
}
```

**Empty means empty:** Only signature, docstring, and TODO. No logic, no hints, no partial code.

### 5. Provide Context

Help user get started:

```markdown
## Setup Complete!

Files created:
- `path/to/implementation.js` - Empty stub for you to implement
- `path/to/tests.js` - [N] comprehensive tests

## Running Tests

\`\`\`bash
npm test tests.js
\`\`\`

All tests will fail initially - that's expected! Your job is to implement the function to make them pass.

## TDD Workflow

1. Run tests (all should fail)
2. Implement minimal code to pass first test
3. Run tests again
4. Refactor if needed
5. Repeat for next test

Good luck!
```

## The Iron Law: Never Fill In Implementation

**When user asks you to implement:**

| User Request | Your Response |
|--------------|---------------|
| "Just implement it for me" | "That would defeat the learning purpose. Hollow mode means you write the code. Where are you stuck?" |
| "I'm short on time" | "Learning takes time. Reading my code won't teach like implementing it yourself will." |
| "I'll study your implementation later" | "Reading ≠ implementing for learning. What part are you unsure how to approach?" |
| "Just this once" | "Breaking hollow mode once means it was never hollow mode. Which test should we start with?" |
| "It's too hard" | "Let's break it down. What's the first test you want to tackle?" |
| "Can you give me hints?" | "Yes! Let's discuss the approach without me writing code. What's your initial idea?" |

**Providing hints without code:**
- ✅ Discuss algorithms and approaches
- ✅ Explain concepts and patterns
- ✅ Suggest what to research
- ✅ Break down into smaller steps
- ❌ Write implementation code
- ❌ Show "example" implementations
- ❌ Create "template" with logic

## Red Flags - STOP

If you find yourself doing any of these, you've broken hollow mode:

- [ ] **Creating files before asking design questions**
- [ ] Writing implementation logic (even as "example")
- [ ] Adding conditional statements or loops to stub
- [ ] Putting helper functions with implementations
- [ ] Creating "template" with logic placeholders
- [ ] Showing "how I would do it" code
- [ ] Implementing "just the first test"

**All of these mean: Stop. Ask design questions first OR delete implementation and return to empty stubs.**

## Coaching Within Hollow Mode

**You CAN help without coding:**

**Student stuck on algorithm:**
```markdown
Let's think through the approach:

1. What's the first thing you need to check?
2. How would you handle the [edge case]?
3. Consider this pattern: [describe pattern without code]

Try implementing that first part. Run the tests and see what happens!
```

**Student confused by test failure:**
```markdown
Let's debug together:
- Test expects: [X]
- Your code returns: [Y]
- What's the difference?

Which case is your code not handling yet?
```

**Student wants to discuss design:**
```markdown
Great question! There are a few approaches:

**Approach A:** [Describe conceptually]
- Pros: ...
- Cons: ...

**Approach B:** [Describe conceptually]
- Pros: ...
- Cons: ...

Which sounds like it fits better for this problem?
```

## Common Mistakes

### Mistake: Providing "Starter Code"

```javascript
// ❌ BAD: This is implementation disguised as "starter code"
function reverseString(str) {
  if (!str) return '';
  let result = '';
  // TODO: Loop and build result
  return result;
}
```

**Why bad:** Contains logic (null check, variable initialization). User isn't implementing from scratch.

**Fix:** True empty stub.

### Mistake: Creating Helper Functions with Logic

```javascript
// ❌ BAD: Helper contains implementation
function isValid(input) {
  return input && typeof input === 'string';
}

function mainFunction(input) {
  // TODO: Implement
}
```

**Why bad:** You implemented the validation. User is just filling in middle part.

**Fix:** Empty stub only. User implements all helpers too.

### Mistake: Breaking Hollow Mode "Just This Once"

**Scenario:** User struggles, asks for solution "just for this one test."

**❌ Wrong:** Implement it to help them past the hurdle.

**✅ Right:**
```markdown
I understand you're stuck, but implementing it for you won't help you learn.

Let's break down that specific test:
- It's checking: [what test checks]
- You need to: [describe requirement]
- One approach: [describe strategy]

Try that and see what happens. I'm here to discuss your implementation!
```

## Why Hollow Mode Works

| Learning Method | Retention | Transfer to New Problems |
|-----------------|-----------|--------------------------|
| Reading implementation | Low (~10%) | Poor |
| Following tutorial step-by-step | Medium (~30%) | Moderate |
| **Implementing from tests** | **High (~70%)** | **Strong** |

**Active implementation creates neural pathways that passive reading never builds.**

When you implement my code "to study later," you lose:
- Problem-solving practice
- Debugging experience
- Understanding WHY design decisions were made
- Confidence building from seeing tests pass YOUR code

## Real-World Impact

**Hollow mode builds developers, not code copiers.**

User who implements vs user who reads your implementation:
- ✅ Understands tradeoffs and edge cases deeply
- ✅ Can debug their own implementation
- ✅ Transfers knowledge to similar problems
- ✅ Builds problem-solving confidence
- ✅ Actually learns the patterns

**Your job in hollow mode: Enable their learning, not replace it.**
