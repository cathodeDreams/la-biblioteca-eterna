# Notes

## Links

### libtcod

https://libtcod.readthedocs.io/en/latest/

https://libtcod.github.io/docs/

### llama-cpp-python

https://github.com/abetlen/llama-cpp-python

https://github.com/abetlen/llama-cpp-python/tree/main/examples

### Mini agents

[Section for relevant papers on multi-agent LLM architectures]

## Iterative prompt instructions

### 1. Read the last conversation and append to context documentation

```
Carefully read the provided context. 

Update technical_report.md and README.md to account for the project's current status.
```

### 2. Read the context documentation and choose the next step.

```
Carefully read the provided context.

Choose what to work on from the Next Steps section of the technical report and implement with tests.
```

### 3. Read the test results and systematically fix.
    
```
Carefully read the test results.

Systematically fix the issues.
```