# Week 01 AI Assistant Comparison

## Common question

> In SystemVerilog, what is the default value of a bit variable, a logic variable, and an int variable when they are declared without initialization?

I asked the same question to three AI assistants.

## Tool 1

Name: ChatGPT

### Answer summary

ChatGPT answered:

- `bit` → `0`
- `logic` → `X`
- `int` → `X`

### Strengths

- Gave a direct answer.
- Presented the values clearly.
- Explained the difference between the data types.

### Weaknesses

- The answer for `int` was incorrect.
- The response sounded confident even though one of the values was wrong.

## Tool 2

Name: DeepSeek

### Answer summary

DeepSeek answered:

- `bit` → `0`
- `logic` → `X`
- `int` → `0`

### Strengths

- Gave a direct answer.
- The values matched the SystemVerilog reference I used for verification.

### Weaknesses

- The answer still needed to be checked against a reliable technical source.

## Tool 3

Name: Gemini

### Answer summary

Gemini answered:

- `bit` → `0`
- `logic` → `X`
- `int` → `0`

### Strengths

- Gave a direct answer.
- The values matched the SystemVerilog reference I used for verification.

### Weaknesses

- The answer still needed independent verification.

## Verification source

I compared the answers with a SystemVerilog technical reference.

Source:

https://chipverify.com/systemverilog/systemverilog-data-types-integer-byte

The reference was used to verify the default values of the SystemVerilog data types.

## Final comparison

- **Accuracy:** DeepSeek and Gemini matched the verified values, while ChatGPT gave an incorrect value for `int`.
- **Traceability:** The answers themselves were not sufficient evidence, so I checked them against a technical reference.
- **Explanation quality:** All three tools gave understandable answers, but a clear explanation does not guarantee that every value is correct.
- **Ease of verification:** The values were easy to verify using a SystemVerilog reference.
- **Claims that required correction or qualification:** The `int` value in the ChatGPT response required correction.

## Lesson

I learned that different AI assistants can give different answers to the same technical question. Even when an answer sounds confident and clear, it should be checked against a reliable technical source before I use it in my work.
