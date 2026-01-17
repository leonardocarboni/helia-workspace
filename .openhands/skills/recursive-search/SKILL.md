---
triggers:
  - deep search
  - huge file
  - massive context
  - find in files
  - recursive search
  - needle in a haystack
---

# Recursive Knowledge Search (RLM)

You possess a specialized method for analyzing files that are too large to fit in your context window (e.g., >1MB logs, books, massive codebases).

## The RLM Methodology
Instead of reading a file into memory, treat the **filesystem as your external memory** and use **recursion** to process it.

### Step 1: Peek (Exploration)
**NEVER** use `read()` on a large file immediately.
1.  Check file size: `ls -lh filename` 
2.  Peek at structure: `head -n 20 filename` 

### Step 2: Decompose (Filtering)
Narrow down the search space using shell tools or Python streaming.
* **Keywords:** Use `grep -nC 5 "keyword" filename > matches.txt` to extract relevant context into a smaller file.
* **Chunking:** If no keywords exist, split the file into chunks (e.g., 500 lines) using `split` or Python generators.

### Step 3: Recurse (Sub-Calls)
Analyze the extracted chunks by calling a sub-model.
* *Note:* If a specific `llm_query` tool is not available, simulate this by iterating through chunks in your main loop and summarizing them one by one.
* **Verification:** If a chunk looks promising, verify it specifically before adding it to the final answer.

### Step 4: Aggregate
Synthesize the findings from your sub-calls/grep results into a final answer.

## Example Workflow (Python)
```python
# Don't do this: open("huge.log").read()

# Do this:
with open("huge.log") as f:
    for line in f:
        if "ERROR" in line:
            # Process only relevant lines or send to sub-agent
            print(line)

```
