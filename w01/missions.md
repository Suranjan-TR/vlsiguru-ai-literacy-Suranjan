## Mission 1 - Find AI Around You

### 3 AI Systems I Use

| System / Feature | What I think it does | Primary task |
|---|---|---|
| Google Maps | Predicts traffic and estimated travel time and suggests routes. | Prediction |
| YouTube | Recommends videos based on my viewing and search activity. | Recommendation |
| Gmail Spam Filter | Identifies unwanted or suspicious emails and places them in the spam folder. | Classification |

### Evidence

**Google Maps:**  
Google states that Google Maps uses machine learning with historical traffic patterns and live traffic conditions to predict traffic.

Source: https://blog.google/products-and-platforms/products/maps/google-maps-101-how-ai-helps-predict-traffic-and-determine-routes/

**YouTube:**  
YouTube explains that its recommendation system uses information such as watch history, search history, likes, and subscriptions to recommend videos.

Source: https://support.google.com/youtube/answer/16089387

**Gmail Spam Filter:**  
Google states that Gmail uses machine learning to identify spam and learn patterns from user feedback.

Source: https://workspace.google.com/blog/identity-and-security/an-overview-of-gmails-spam-filters

### Could a simple rule-based program do something similar?

A simple rule-based program could produce similar behaviour in some cases. For example, a traffic system could use a fixed rule such as:

> If traffic is high, increase the estimated travel time.

Similarly, a simple recommendation system could recommend a video based on a fixed rule such as:

> If I watched videos about electronics, recommend another electronics video.

However, fixed rules would be limited because real-world behaviour depends on many different factors. Machine-learning systems can learn patterns from data and use them for prediction, recommendation, or classification.

### Conclusion

I learned that I already interact with AI-related features in everyday applications. Google Maps uses AI/ML for prediction, YouTube uses it for recommendations, and Gmail uses it for spam classification. I also learned that a simple rule-based program can produce similar behaviour in some cases, but it would be more limited than a system that learns patterns from data.


## Mission 2 - AI, ML, GenAI: Put the Pieces Together

### Simple Relationship Diagram

```text
Artificial Intelligence (AI)
│
├── Machine Learning (ML)
│   │
│   └── Deep Learning (DL)
│
└── Other AI approaches

Generative AI (GenAI)
│
└── Uses AI models, commonly Deep Learning,
    to generate new content
```

### 1. Artificial Intelligence (AI)

AI is the broad field of creating computer systems that can perform tasks that normally require human intelligence, such as recognition, decision-making, reasoning, and problem-solving.

**Example:** A smartphone recognizing a person's face to unlock the phone.

### 2. Machine Learning (ML)

Machine Learning is a part of AI in which computers learn patterns from data and use those patterns to make predictions or decisions instead of being programmed with every rule.

**Example:** An email system learning patterns from previous emails to identify spam.

### 3. Deep Learning (DL)

Deep Learning is a type of Machine Learning that uses neural networks with multiple layers to learn complex patterns from data.

**Example:** A camera using a deep-learning model to recognize objects or faces in an image.

### 4. Generative AI (GenAI)

Generative AI is AI that can generate new content such as text, images, audio, video, or code based on patterns learned from existing data.

**Example:** ChatGPT generating an explanation or computer code from a user's prompt.

### AI Explanation Check

I asked an AI assistant to explain my diagram. It confirmed that AI is the broad field, Machine Learning is a part of AI, and Deep Learning is a type of Machine Learning. It also explained that Generative AI focuses on generating new content and commonly uses deep-learning models.

I checked the explanation and corrected the diagram so that Generative AI is not shown as a strict fourth level below Deep Learning.


## Mission 3 - Is It Really AI?

### Classification

| Example | Classification | Reason |
|---|---|---|
| Calculator | Rule-based / Traditional Software | It follows mathematical procedures programmed into the calculator. |
| Temperature warning rule | Rule-based / Traditional Software | The programmer explicitly defines the rule, such as `If temperature > 80°C, display WARNING`. |
| Spam filter | ML-based AI | It can learn patterns from previous emails and use them to classify new emails as spam or not spam. |
| Document summariser | Generative AI | It generates a new summary based on the information in the document. |
| Traffic ETA prediction | ML-based AI | It can learn patterns from traffic and historical data to predict estimated travel time. |

### Easy Classification

The calculator was easy to classify because it follows predefined mathematical procedures. The programmer determines how the calculation is performed, so it does not need to learn patterns from data.

### Difficult Classification

The spam filter was more difficult because it may look like a simple set of rules. However, modern spam filters can use machine learning to learn patterns from previous emails and classify new messages.

### My Own Example

**Automatic brightness control in a smartphone:** This can be an ML-based AI system when it learns from the user's brightness adjustments and environmental conditions to predict the brightness level the user is likely to prefer.

### Conclusion

I learned that a system looking intelligent does not automatically mean it uses AI. Traditional software follows explicitly programmed rules, while machine-learning systems learn patterns from data. Generative AI goes further by generating new content.


## Mission 4 - Make AI Explain Itself, Then Test It

### How an LLM Produces an Answer

When I send a prompt to an LLM, the text is first divided into smaller units called **tokens**. The model processes these tokens along with the available context and predicts what token is likely to come next. It generates the response one token at a time until the answer is complete.

For example:

```text
Prompt: The sky is

Model predicts: blue

Then: The sky is blue

Model predicts the next token again...
```

The model continues this process to produce the complete response.

### Beginner Explanation

A simple way to understand an LLM is to think of it as a very advanced text prediction system.

If I type:

> "The sky is"

the model may predict that **"blue"** is a likely next token because it has learned patterns from large amounts of text.

It then uses the text generated so far to predict the next token. By repeating this process, it produces a complete answer.

### Important Claims I Checked

**Claim 1: Text is processed as tokens.**

OpenAI explains that its models process text in units called tokens. A token can represent a character, part of a word, a whole word, or punctuation.

Source: https://help.openai.com/en/articles/4936856-what-are-tokens-and-how-to-count-them

**Claim 2: Language models generate text one token at a time.**

OpenAI documentation and examples show that language models generate output tokens and can predict the next token based on the preceding context.

Source: https://developers.openai.com/cookbook/examples/using_logprobs

### What the AI Explained Well

The AI explained the basic process clearly: prompt → tokens → model processing → next-token prediction → generated response. This helped me understand the basic idea without needing to study the mathematics of transformers.

### Correction / Clarification

One clarification I made is that an LLM should not be thought of as simply searching a database and copying an answer. It processes the input and generates output based on patterns learned during training and the context provided to it.

### Conclusion

I learned that an LLM produces an answer by processing the prompt as tokens and generating output step by step. The basic mental model is to think of the model as predicting likely next tokens based on the previous context.


## Mission 5 - Can AI Be Confidently Wrong?

### Prompt

I asked an AI assistant:

> In SystemVerilog, what is the default value of a `bit` variable, a `logic` variable, and an `int` variable when they are declared without initialization?

### AI Answer

I asked the same question to three AI assistants.

| AI Tool | `bit` | `logic` | `int` |
|---|---:|---:|---:|
| DeepSeek | 0 | X | 0 |
| Gemini | 0 | X | 0 |
| ChatGPT | 0 | X | X |

### Verification Source

I checked the answers against a SystemVerilog reference. SystemVerilog has two-state and four-state data types. `bit` is a two-state type, while `logic` is a four-state type. The default value of a two-state variable is `0`, while a four-state variable defaults to `X`.

Source: https://mail.chipverify.com/systemverilog/systemverilog-quick-refresher

### Result

The correct values are:

| Variable | Correct default value |
|---|---:|
| `bit` | `0` |
| `logic` | `X` |
| `int` | `0` |

DeepSeek and Gemini gave the correct answer. ChatGPT gave an incorrect answer for `int`.

### Lesson

This experiment showed me that an AI can give an answer confidently even when part of the answer is wrong. I learned that I should verify important technical information using a reliable source instead of trusting an answer only because it sounds confident.

## Mission 6 - Chatbot or Agent?

### Comparison

| Concept | Simple Explanation |
|---|---|
| **LLM** | A language model trained on a large amount of text that can understand and generate language. |
| **AI Application** | A software application that uses an AI model to perform a specific task, such as answering questions or summarizing documents. |
| **RAG** | Retrieval-Augmented Generation (RAG) retrieves relevant information from an external source and provides it to the LLM as context before generating an answer. |
| **Tool-Using Assistant** | An AI system that can use external tools such as search, calculators, databases, or APIs to complete a task. |
| **AI Agent** | An AI system that can use a model, tools, and actions to work toward a particular goal by deciding what steps are needed. |

### Simple Flow

```text
User Request
     ↓
AI Model / LLM
     ↓
Decide what information or tool is needed
     ↓
Retrieval / Tool
     ↓
Tool or Retrieval Result
     ↓
AI Model / LLM
     ↓
Final Response / Action
```

### Everyday Example of an Agentic Workflow

**Travel planning assistant**

A user asks:

> "Plan a 3-day trip to Bengaluru."

An agentic system could:

1. Understand the user's request.
2. Search for suitable places to visit.

## Mission 7 - What Actually Runs AI?

### 1. What is a CPU and what is it good at?

A CPU (Central Processing Unit) is a general-purpose processor that can perform many different types of tasks. It is good at handling sequential operations, decision-making, and a wide variety of software tasks.

### 2. What is a GPU and why is it useful for AI workloads?

A GPU (Graphics Processing Unit) is a processor designed to perform many calculations in parallel. AI workloads often involve large numbers of similar mathematical operations, so GPUs can process many of them at the same time.

### 3. What is an NPU / AI Accelerator and why do modern systems use specialised hardware?

An NPU (Neural Processing Unit) or AI accelerator is specialised hardware designed to efficiently perform common AI operations such as matrix and tensor calculations.

Modern systems use specialised hardware because it can perform AI workloads more efficiently than relying only on a general-purpose CPU. This can improve performance and reduce power consumption.

### 4. What does parallel computation mean?

Parallel computation means performing multiple calculations at the same time instead of performing every calculation one after another.

For example, if a large dataset requires many independent calculations, a processor can divide the work into smaller parts and process several parts simultaneously.

### 5. Why does AI depend so heavily on compute and memory?

AI models can contain a very large number of parameters and require many mathematical operations. The hardware must perform these calculations and move large amounts of data between processing units and memory.

Therefore, both computational power and memory capacity/bandwidth can strongly affect AI performance.

### 6. Training vs Inference

| Aspect | Training | Inference |
|---|---|---|
| Purpose | The model learns patterns from data. | The trained model produces an output from new input. |
| Computation | Usually requires a very large amount of computation. | Usually requires less computation than training for each individual request. |
| Hardware | GPUs and specialised accelerators are commonly useful. | CPUs, GPUs, NPUs, or other accelerators can be used depending on the workload. |
| Example | Training a model using a large dataset of images. | Using the trained model to classify a new image. |

### 7. Simple AI Computing Flow

```text
AI Application
      ↓
AI Model
      ↓
Software / Framework
      ↓
CPU / GPU / AI Accelerator
      ↓
Memory
```

The AI application uses an AI model. Software or frameworks provide the interface for running the model, while the CPU, GPU, or accelerator performs the required computations and uses memory to store and access data.

### 8. Real AI Workload Example

**Image Classification**

Suppose an AI system needs to identify whether an image contains a cat or a dog.

A GPU would be useful because image-processing models perform many similar mathematical operations on large amounts of data. These operations can be performed in parallel, allowing the GPU to process the workload efficiently.

### Conclusion

I learned that an AI model is software, but it needs hardware to perform its computations. CPUs provide general-purpose computing, while GPUs and specialised AI accelerators can efficiently handle highly parallel AI workloads. Memory is also important because AI models and their data need to be stored and accessed during computation.

The basic mental model is:

**AI Model → Computation → Hardware → Memory → Performance**
4. Check travel times and other information using tools.
5. Compare the results.
6. Prepare a three-day itinerary.

The important difference is that a simple chatbot mainly generates an answer, while an agentic system can use tools, examine the results, and take multiple steps toward a goal.

## Mission 8 - Where Could This Help My VLSI Track?

### VLSI Track: Design Verification (DV)

| Area | Task | How AI Might Help | Why Human Knowledge Still Matters |
|---|---|---|---|
| Design Verification (DV) | Debugging and analysing simulation failures | AI could analyse simulation logs and error messages, identify possible causes, and help suggest where the problem may be in the testbench or RTL. | Human knowledge is still needed to understand the design specification, decide whether the suggested cause is correct, and verify the fix. |

### Conclusion

AI can help automate repetitive debugging and data-analysis tasks in Design Verification, but domain knowledge is still important because an engineer must understand the design, verification requirements, and whether the AI-generated suggestions are actually correct.

## Mission 9 - Build My Own AI-Use Rule

### My 5-Rule AI Working Agreement

1. **Use AI as a learning assistant, not as the final authority.**  
   I will use AI to understand concepts, generate ideas, and explore possible solutions, but I will not blindly accept its answers.

2. **Verify important technical information.**  
   I will check important engineering facts, calculations, code, and technical claims using reliable sources or independent testing before using them.  
   
   **Why:** In Mission 5, I found that ChatGPT gave an incorrect answer for the default value of an `int` variable in SystemVerilog. This showed me that an AI answer can sound confident and still be wrong.

3. **Do not share confidential or proprietary information.**  
   I will not provide confidential project data, company information, passwords, private documents, source code, or other proprietary information to AI tools.

4. **Understand and test AI-generated code or solutions before using them.**  
   I will read, understand, and test AI-generated code instead of copying and using it without checking.

5. **Take responsibility for my final work.**  
   I will make sure that I understand the final answer, code, calculation, or explanation that I submit. I will verify and correct AI-generated content when necessary, and I will take responsibility for the final work.

### My Rule

My goal is not to completely trust or completely avoid AI. I will use AI as a tool for learning and problem-solving, while knowing when verification is necessary and taking responsibility for the final result.
