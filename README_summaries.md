# Exercise Summary Generator

This script adds contextual summaries beneath each exercise title in PythonMastery Jupyter notebooks.

## Usage

### Basic Usage
```bash
python add_exercise_summaries.py <input_notebook.ipynb> [output_notebook.ipynb]
```

### Examples

**Create a new notebook with summaries:**
```bash
python add_exercise_summaries.py PythonMastery_Part4.ipynb PythonMastery_Part4_with_summaries.ipynb
```

**Modify notebook in place:**
```bash
python add_exercise_summaries.py PythonMastery_Part4.ipynb
```

## What It Does

1. **Parses the .ipynb JSON structure** - Reads the notebook file and analyzes its cell structure
2. **Identifies exercise titles** - Finds markdown cells starting with `####` (excluding `#### Answer`)
3. **Generates intelligent summaries** - Creates 1-2 sentence contextual explanations based on:
   - Pattern matching against 25+ common exercise patterns
   - Lesson and skill context
   - Exercise title keywords
4. **Inserts summaries** - Adds new markdown cells beneath each exercise title
5. **Saves the updated notebook** - Outputs a new notebook or overwrites the original

## Summary Pattern Examples

The script includes intelligent patterns for various topics:

- **CLI/argparse**: "Learn to create a command-line argument parser using Python's argparse module."
- **Web APIs**: "Send JSON data in request bodies using the convenient json parameter."
- **SQL/Databases**: "Use parameterized queries with ? placeholders to prevent SQL injection attacks."
- **Jupyter**: "Execute code cells interactively and re-run them to experiment with changes."
- **Pandas**: "Filter DataFrame rows using conditional expressions that evaluate to True/False."
- **Visualization**: "Create basic line and bar charts using matplotlib's pyplot interface."
- **Machine Learning**: "Split data into separate training and testing sets to evaluate model performance."
- **Deep Learning**: "Create PyTorch tensors, the fundamental data structure for deep learning."
- **Packaging**: "Create Python packages by adding __init__.py files to directories."
- **Security**: "Never embed passwords, API keys, or tokens directly in source code."
- **Design Patterns**: "Learn the five fundamental principles for object-oriented design and architecture."

## Features

- ✓ Preserves original notebook structure
- ✓ Context-aware summaries based on lesson/skill
- ✓ Skips cells that already have summaries
- ✓ Pattern matching with 25+ exercise templates
- ✓ Fallback to generic summaries when no pattern matches
- ✓ Progress tracking and verbose output
- ✓ Creates properly formatted JSON output

## Output Example

**Before:**
```markdown
#### Use `sys.argv` to inspect arguments

[code cell]
```

**After:**
```markdown
#### Use `sys.argv` to inspect arguments

Learn how to access command-line arguments passed to your Python script using the built-in sys module.

[code cell]
```

## Results for PythonMastery_Part4.ipynb

- ✓ Successfully processed 300 exercises
- ✓ Added contextual summaries to all exercise titles
- ✓ Output saved to: PythonMastery_Part4_with_summaries.ipynb

## Extending the Script

To add new patterns, edit the `SUMMARY_TEMPLATES` dictionary in `add_exercise_summaries.py`:

```python
SUMMARY_TEMPLATES = {
    r"your_pattern": "Your summary text here.",
    # ... more patterns
}
```

Patterns use Python regex syntax and are matched case-insensitively against exercise titles.
