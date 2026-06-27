# AI Tutor (Local LLM via Ollama)

Explains Python code clearly and concisely using **Gemma3** running locally via
**Ollama** — no paid API required.

## How it works

1. You pass a code snippet to the `Tutor()` or `stream()` function
2. It sends the code to a locally running Gemma3 model through Ollama's OpenAI-compatible API
3. Returns a clean explanation rendered as Markdown — with a typewriter streaming animation if you use `stream()`

## Setup

```bash
# 1. Install Ollama: https://ollama.com
# 2. Pull the model
ollama pull gemma3
 
# 3. Install Python deps
pip install openai ipython
 
# 4. Run
tutor.ipynb
```



## Usage

```python
# Without streaming
Tutor("""
def flatten(nested):
    for item in nested:
        if isinstance(item, list):
            yield from flatten(item)
        else:
            yield item
""")
 
# With streaming animation
stream("""
tokens = [word.lower() for word in text.split() if word.isalpha()]
vocab = {word: idx for idx, word in enumerate(sorted(set(tokens)))}
""")
```


## Example Output

### 1. Output for Tutor()
>Okay, let's break down this Python code snippet. It's a concise and clever way to "flatten" a nested list – meaning it takes a list that might contain other lists within it, and produces a single, flat list without any sub-lists.
>
>**What the Code Does:**
>
>This function `flatten(nested)` takes a potentially nested list (`nested`) as input and returns an iterator (a special kind of object that provides values one at a time) containing all the elements from the original list, but in a single level. 
>
>**Why it Works (Explanation with Analogy):**
>
>Think of it like unpacking a box.  You have a box inside another box… inside another box... and so on.  The function `flatten` works like opening each box one by one.
>
>1. **`for item in nested:`**: This loop goes through each *item* within the input list `nested`.
>
>2. **`if isinstance(item, list):`**: It checks if the current `item` is itself a list.
>   - If it *is* a list (like one of those inner boxes),  it calls `yield from flatten(item)` again on that inner list.  This is where the recursive part comes in: we’re letting the function call itself to handle unpacking *that* sublist. 
>
>3. **`else:`**: If the current `item` isn't a list (meaning it’s just a regular value like a number or string), 
>   -  **`yield item`**: This is the magic! The `yield` keyword in Python makes this function a *generator*. Instead of building a completely new flat list in memory and returning it, it *generates* each element one at a time as you ask for it. Think of it like dispensing items from the unpacked boxes as you need them. 
>
>**Example:**
>
>```python
>nested_list = [1, [2, [3, 4], 5], 6]
>flattened_list = list(flatten(nested_list))  # Convert iterator to a list
>print(flattened_list) # Output: [1, 2, 3, 4, 5, 6]
>```
>
>**Key Concepts Illustrated:**
>
>*   **Recursion:** The function calls *itself* when it encounters another list. This is essential for handling nested lists of arbitrary depth.  >Without recursion, you'd need a hardcoded limit on the nesting level.
>*   **Generators (`yield`)**: Generators are memory-efficient ways to create iterators. They produce values one at a time rather than storing the >entire flattened list in memory upfront.
>*   **`isinstance()`:**  This function checks if an object is of a certain type (in this case, `list`).
>
>Let me know if you'd like a more detailed explanation of any part, or want to explore how generators work further!

### 2. Output for Stream()

>Okay, let's break down this Python code snippet step by step. It’s a common process used in Natural Language Processing (NLP) to create a vocabulary for text data.  Think of it like building a dictionary of all the unique words you want to work with.
>
>**What the Code Does:**
>
>This code performs two main operations:
>
>1. **Creating a List of Tokens:**
>   - `text.split()`: This splits the input string `text` into individual words, using spaces as delimiters (like separating sentences). For example, if `text = "This is a simple sentence."`, it would become `['This', 'is', 'a', 'simple', 'sentence.']`.
>   - `word.lower()`:  For each word extracted, this converts it to lowercase. This ensures that “This” and “this” are treated as the same word. Lowercasing is crucial for normalization. 
>   - `if word.isalpha()`: This filters out any words that contain non-alphabetic characters (like punctuation or numbers). So, "sentence." would become "", because it contains a period.  We only want words containing letters.
>   - `[... for ... in ...]`: These are list comprehension elements. They efficiently create a new list (`tokens`) by applying these operations to each word from the split text.
>
>2. **Creating a Vocabulary Dictionary:**
>   - `set(tokens)`: This converts the `tokens` list into a set. A set only contains *unique* items – it automatically removes duplicates.  So, if "is" appeared multiple times in `tokens`, it’ll appear only once in the set.
>   - `sorted(...)`: This sorts the unique words alphabetically (A to Z).  This makes it easier to work with them and assign indices consistently.
>   - `{word: idx for idx, word in ...}` : This is another list comprehension used to construct a dictionary called `vocab`. It does the following:
>     - **`enumerate(sorted(...))`:** Enumerate takes this sorted set of words and pairs each word with its index (position) starting from 0.  So it produces a sequence like `(0, 'a'), (1, 'is'), (2, 'simple'), ...`.
>     - **`word: idx`**: For each pair, it creates a key-value pair in the dictionary where the *key* is the word and the *value* is its index.
>
>**Example:**
>
>Let's say `text = "This is a sentence! This is good."`
>
>1. **Tokenization & Lowercasing:** The code would first produce: `['this', 'is', 'a', 'sentence!', 'this', 'is', 'good']`.  Then it converts all to lowercase and filters out the punctuation: `['this', 'is', 'a', 'sentence', 'this', 'is', 'good']`
>
>2. **Vocabulary Creation:**
>   - `set(tokens)` becomes `{'this', 'is', 'a', 'sentence', 'good'}`
>   - `sorted(...)` becomes `['a', 'good', 'is', 'sentence', 'this']`
>   - The `vocab` dictionary would then be:
>     ```python
>     vocab = {
>         'a': 0,
>         'good': 1,
>         'is': 2,
>         'sentence': 3,
>         'this': 4
>      }
>     ```
>
>
>**Why is this done?**
>
>* **Numerical Representation:** Computers can’t directly understand text. This code transforms words into numbers (indices), which allows the computer to analyze and process them mathematically.
>* **Vocabulary Size Limits:**  Very large vocabularies can slow down processing. By creating a vocabulary, you limit yourself to a manageable set of words.
>* **Text Analysis:** A vocabulary is a fundamental building block for many NLP tasks like:
>   - Text Classification (e.g., sentiment analysis)
>   - Machine Translation
>   - Information Retrieval
>
>Do you want me to explain any part of the code in more detail, or perhaps show how this might be used in a simple example?