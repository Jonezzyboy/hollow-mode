# Hollow Mode - Claude Code Plugin

> TDD scaffolding with empty implementations for learning

## What is Hollow Mode?

Hollow Mode is a Claude Code skill that creates Test-Driven Development (TDD) scaffolding for learning exercises. Instead of providing complete implementations, it:

1. **Asks collaborative design questions** to understand your learning goals
2. **Creates comprehensive tests** that guide your implementation
3. **Generates empty function stubs** for you to fill in
4. **Maintains learning boundaries** - refuses to implement code even when asked
5. **Provides coaching** through pseudocode and approach discussions (without writing actual code)

**The philosophy:** Reading someone else's code teaches ~10% retention. Implementing it yourself teaches ~70% retention.

## Features

### ✅ Collaborative Planning
Before creating any files, Hollow Mode asks about:
- Language and testing framework
- Scope of functionality
- Edge cases to cover
- Your specific learning goals

### ✅ Comprehensive Tests
Creates well-organized test suites with:
- Core functionality tests
- Edge case coverage
- Error handling scenarios
- Clear test descriptions

### ✅ True Empty Stubs
Generates function signatures with:
- Proper docstrings/JSDoc
- TODO comments explaining requirements
- No implementation logic (truly empty)

### ✅ Strong Learning Boundaries
Even when you ask "just implement it for me," Hollow Mode:
- Explains why that would defeat the learning purpose
- Offers alternative help (pseudocode, approach discussion)
- Maintains the educational methodology

### ✅ Coaching Without Coding
Provides guidance through:
- Algorithm and approach discussions
- Pseudocode outlining logic flow
- Breaking down complex problems into steps
- Debugging help for your implementation

## Installation

### From GitHub
```bash
claude plugin install hollow-mode@github:Jonezzyboy/hollow-mode
```

### Local Installation
```bash
# Clone or download this repository
git clone https://github.com/jonezzyboy/hollow-mode.git

# Install the plugin
claude plugin install hollow-mode@file:./hollow-mode
```

## Usage

### Basic Usage
```bash
# In Claude Code, invoke the skill:
Use hollow-mode to help me create a TDD exercise for [your feature]
```

### Example Session

**You:**
> Use hollow-mode to help me practice TDD with a password validator

**Claude:**
> Before I create any scaffolding, let me understand your learning goals:
>
> 1. **Language & Framework**: Which language and testing framework?
> 2. **Scope**: What functionality should this cover?
> 3. **Edge Cases**: What should we test?
> 4. **Learning Focus**: What do you want to practice?

**You:**
> 1. JavaScript with Jest
> 2. Check length, uppercase, numbers, special chars
> 3. Test null, empty, edge cases
> 4. I want to practice regex and validation logic

**Claude:**
> *Creates comprehensive test suite and empty stubs*
> All tests will fail initially - that's expected! Your job is to implement the function to make them pass.

**Later, if you get stuck:**

**You:**
> Can you just implement it for me?

**Claude:**
> That would defeat the learning purpose. Hollow mode means you write the code. Where are you stuck?
> I can provide pseudocode or discuss approaches without writing implementation code.

## When to Use Hollow Mode

Use Hollow Mode when:
- Learning a new language or framework
- Practicing TDD methodology
- Building coding exercises for students
- Creating interview practice problems
- Teaching through guided practice

**Don't use when:**
- You need a working solution for production
- Time-critical feature work
- You just want code generated

## Why Hollow Mode Works

| Learning Method | Retention | Transfer to New Problems |
|-----------------|-----------|--------------------------|
| Reading implementation | Low (~10%) | Poor |
| Following tutorials | Medium (~30%) | Moderate |
| **Implementing from tests** | **High (~70%)** | **Strong** |

Active implementation creates neural pathways that passive reading never builds.

## Examples

Hollow Mode has been tested with:
- **Email validators** - String parsing and regex patterns
- **Password validators** - Complex validation rules
- **String reverse functions** - Algorithm basics
- **Prime number checkers** - Mathematical logic
- **URL parsers** - Multi-step parsing and error handling
- **Shopping carts** - Object-oriented design and state management

## Philosophy

Hollow Mode is based on the principle that **implementation by user = learning, implementation by AI = convenience that defeats learning.**

When an AI fills in the code "for you to study later":
- ❌ You lose problem-solving practice
- ❌ You miss debugging experience
- ❌ You don't understand WHY design decisions were made
- ❌ You don't build confidence from seeing tests pass YOUR code

When you implement it yourself with AI coaching:
- ✅ You understand tradeoffs and edge cases deeply
- ✅ You can debug your own implementation
- ✅ You transfer knowledge to similar problems
- ✅ You build problem-solving confidence
- ✅ You actually learn the patterns

## Skill Development

This skill was created following Test-Driven Development methodology:

1. **RED Phase**: Tested agent behavior WITHOUT the skill (baseline)
2. **GREEN Phase**: Wrote skill addressing baseline failures
3. **REFACTOR Phase**: Closed loopholes through iterative testing

The skill includes explicit counters for common rationalizations like:
- "I'm short on time, just implement it"
- "I'll study your code later"
- "Just this once"
- "It's too hard"

## Contributing

Found a loophole where the skill breaks hollow mode boundaries? Please open an issue!

Have suggestions for improving the learning experience? PRs welcome!

## License

MIT License - feel free to use, modify, and share!

## Credits

Created by Alan Jones following TDD best practices for skill development.

Inspired by the principle that the best way to learn coding is through active implementation, not passive consumption.

---

**Remember:** The struggle IS the learning. When you get stuck, think through the problem yourself first. That's where the real growth happens! 🚀
