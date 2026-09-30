# Week 01 Questions

## Q1 - AI → Machine Learning → Deep Learning → Generative AI → AI Agents

### A - Answer

**AI** is the broad field of creating computer system that can perform task by itself which normally require human intelligence like decision making, reasoning, planning, recognition etc.
example: A smartphone using AI to recognize a person's face for unlocking the phone

**ML** is a part of AI in which computers learn patterns from data and use those patterns to make predictions or decisions instead of being programmed with every rule.
example: An email system learning from previous messages to identify whether a new email is likely to be spam.

**DL** is a subset of ML where it uses artificial neural network (layers of interconnected nodes) with multiple layers (data move from input layer, through multiple hidden layers that find features, to an output layer) to process data and learn complex pattern automatically.
example: A phone's camera using a deep-learning model to recognize objects or faces in an image.

**Generative AI** is AI that can generate new content such as text, images, audio, video, or code based on pattern it learned from existing data.
example: ChatGPT generating an explanation, email, or piece of computer code from a user's prompt.

An AI Agent is a system that can use an AI model together with tools and actions to work toward a particular goal. An AI agent relies on four core components working together: a brain, hands, memory, and autonomy. The Brain (LLM) uses advanced models like Claude or GPT to handle all the reasoning, strategic planning, and critical decision-making for a project. The Hands (Tools & APIs) give the agent physical capability in the digital world, allowing it to search the web, execute code, read files, and trigger external applications. Memory combines short-term context tracking with long-term database storage so the system can recall user preferences, remember past actions, and actively learn from its mistakes. Finally, Autonomy provides the independence needed to break a massive goal into smaller sequential steps and execute them flawlessly without requiring constant human supervision or check-ins.
example: An AI travel agent that receives a request to plan a trip, searches for suitable flights and hotels using available tools, compares the information, and prepares an itinerary.


A simple way to understand the relationship is:
AI → ML → Deep Learning
Generative AI → uses AI/ML/DL models to generate content
AI Agent → uses AI/Generative AI + tools + actions to achieve a goal

### E - Evidence

https://www.ibm.com/think/topics/ai-vs-machine-learning-vs-deep-learning-vs-neural-networks

https://www.ibm.com/think/topics/deep-learning

https://en.wikipedia.org/wiki/Machine_learning

https://csrc.nist.gov/glossary/term/artificial_intelligence

### V - Verification

I checked the definitions using IBM and NIST. They confirmed that ML is a part of AI and DL is a type of ML. I also checked the definitions of Generative AI and AI Agents using reliable sources, and they matched my understanding.

### R - Reflection

I learned that AI is the broadest concept. Machine learning is one way of building AI systems, and deep learning is a type of machine learning. Generative AI and AI Agents are not the same thing. Generative AI focuses on generating content, while an agent can use a model together with tools and actions to accomplish a goal.

---

## Q2 - Is Everything That Looks Intelligent Actually AI?

### A - Answer

No. A system can appear intelligent without actually using AI.

| Example | Classification | Reason |
|---|---|---|
| A. Calculator produces 25 × 16 = 400 | Traditional software | It follows a mathematical procedure programmed into the calculator. |
| B. If temperature > 80°C, display WARNING | Traditional software | The programmer explicitly defines the rule. |
| C. Email system identifies spam using patterns learned from previous email data | Machine-learning-based AI | The system uses patterns learned from data to classify new messages. |
| D. AI assistant writes a summary of a document | Generative AI | The system generates new text based on the document and instruction. |
| E. Navigation application predicts estimated arrival time using traffic and historical data | Machine-learning-based AI | A model can learn patterns from traffic and historical data to make a prediction. |

The important difference is that traditional software can follow explicit instructions written by a programmer, while machine-learning systems can learn patterns from data.

However, we should not call something AI only because it appears intelligent. We should check evidence about how the system actually works.

### E - Evidence

https://developers.google.com/learn/pathways/applied-ml-with-keras

https://cloud.google.com/use-cases/ai-summarization

https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0238200

### V - Verification

I checked the examples using the sources I listed. They show that AI and machine learning are actually used in applications like spam detection, document summarization, and traffic prediction. This supports my classification of these examples.

### R - Reflection

I learned that "smart-looking" does not automatically mean AI.

---

## Q3 - What Happens When You Ask an LLM a Question?

### A - Answer

LLM - Are advanced artificial intelligence systems trained on massive amounts of text to understand, summarize, and generate human-like language (Ex: OpenAI ChatGPT)

When I send a question to an LLM, the text I provide is called the prompt.

The prompt is broken into smaller pieces called tokens. Tokens can represent words, parts of words, punctuation, or other pieces of text.

The model processes the tokens together with the available context. It calculates probabilities for possible next tokens.

The model then selects a next token according to its generation process. The new token becomes part of the context, and the model predicts another token.

This process continues until the response is completed.

Simple flow:

Prompt
→ Tokens
→ Model processing
→ Probability distribution
→ Next-token selection
→ Generated response

Important terms:

- Prompt: The input given to the language model.
- Token: A small unit of text processed by the model.
- Context: The information available to the model while generating the response.
- Probability: A numerical representation of how likely different possible next tokens are.
- Next-token prediction: Predicting what token should come next based on the previous context.
- Generated response: The sequence of tokens produced by the model.

Training and inference are different.

Training is the process in which a model learns patterns from training data.

Inference is when the trained model is used to produce an output from a new input.

An LLM can produce fluent language even when a statement is false because producing fluent text and producing a verified fact are different things. The model is generating text based on learned patterns and probabilities; it does not automatically guarantee that every generated statement is factually correct.

### E - Evidence

https://developers.openai.com/api/docs/concepts

https://learn.microsoft.com/en-us/dotnet/ai/conceptual/understanding-tokens

### V - Verification

I checked the sources and verified that an LLM processes text as tokens and generates a response by predicting tokens based on the available context. 

### R - Reflection

I learned that an LLM does not simply search a database and copy an answer, it processes the available context and predicts tokens that can form a response. Also learned that every generated statement is not correct should verify it.

---

## Q4 - Hallucination Experiment: Can AI Sound Confident and Still Be Wrong?

### A - Answer

For this question, I performed an actual experiment using the same factual question with three AI assistants: DeepSeek, Gemini, and ChatGPT.

The question I asked was:

> "In SystemVerilog, what is the default value of a bit variable, a logic variable, and an int variable when they are declared without initialization?"

I asked the exact same question to all three AI assistants.

The responses were:

| AI Tool | bit | logic | int |
|---|---|---|---|
| DeepSeek | 0 | X | 0 |
| Gemini | 0 | X | 0 |
| ChatGPT | 0 | X | X |

DeepSeek and Gemini gave the same answers. ChatGPT gave a different answer for `int`.

I then checked the answer against a reliable SystemVerilog reference to determine which answer was correct.

### E - Evidence

The evidence for this experiment is:

1. The exact question asked to all three AI assistants.
2. The actual response from DeepSeek.
3. The actual response from Gemini.
4. The actual response from ChatGPT.
5. The reliable SystemVerilog reference used for verification.
6. The difference found between the AI responses.

### V - Verification

I compared the three AI responses with a reliable SystemVerilog reference.[https://chipverify.com/systemverilog/systemverilog-data-types-integer-byte]

### R - Reflection

This experiment showed me that an AI answer can sound confident and still be wrong.

Two AI tools gave the correct answer, while another AI gave an incorrect answer.

I learned that I should verify important technical information using a reliable source instead of trusting an AI answer only because it sounds confident.

---

## Q5 - AI Assistant vs Search vs Authoritative Reference

### A - Answer

AI assistants, search engines, and authoritative references are useful for different purposes.

| Method | Main use | Strength | Limitation |
|---|---|---|---|
| AI assistant | Explanation and brainstorming | Can explain a topic in simple language | Can produce incorrect or unsupported information |
| Search engine | Finding information | Helps locate many sources quickly | Search results are not automatically authoritative |
| Authoritative reference | Verification | Provides stronger evidence for important claims | May be harder to understand or less convenient |

For this activity, I would use the same technical question with all three methods.

Example question:

> "What is the difference between TCP and UDP?"

I would first ask the AI assistant.

Then I would search the same question using a search engine.

Finally, I would identify an authoritative networking reference and use it to verify the important claims.

### E - Evidence

The evidence should include:

- The AI answer.
- Search results and useful sources found.
- The authoritative reference.
- The differences found between the sources.

### V - Verification

I would not treat the AI answer or search-result snippet as final proof.

I would open the relevant source and check whether it actually supports the claim.

For important engineering decisions, I would prefer primary or authoritative documentation where appropriate.

### R - Reflection

I learned that AI is useful for understanding and brainstorming, while search is useful for discovering information.

An authoritative source is more important when I need to make an important technical decision or verify a factual claim.

The three methods should not automatically be treated as equally reliable.

---

## Q6 - What Is an AI Agent?

### A - Answer

The five concepts can be understood as follows:

| Concept | Simple explanation |
|---|---|
| LLM | A language model that processes language and generates text. |
| LLM application | A software application that uses an LLM to provide a particular function. |
| RAG system | A system that retrieves relevant information and provides it to the model as context before generating an answer. |
| Tool-using assistant | An AI system that can use external tools such as search, calculators, databases, or software. |
| AI Agent | A system that can use an AI model, tools, and actions as part of a workflow to accomplish a goal. |

Simple architecture:

User request
↓
AI model
↓
Decision
↓
Tool call
↓
Tool result
↓
AI model
↓
Final response / action

A simple chatbot may only generate a response to the user's message.

An agentic system can go further by deciding that it needs a tool, using the tool, examining the result, and continuing toward the requested goal.

Example:

A travel-planning agent could:

1. Receive a request for a trip.
2. Search for available transportation.
3. Search for accommodation.
4. Compare the information.
5. Present an itinerary.

### E - Evidence

The assessment requires the explanation to distinguish an LLM, LLM application, RAG system, tool-using assistant, and AI agent.

The evidence should come from reliable technical references describing these system behaviors.

### V - Verification

I will verify the explanation by checking whether the reference describes:

- A language model.
- Retrieval-augmented generation.
- Tool use.
- Multi-step or goal-oriented workflows.

I will focus on system behavior rather than vendor-specific terminology.

### R - Reflection

I learned that an LLM and an AI agent are not the same thing.

An LLM primarily provides model capabilities, while an agentic system can combine a model with tools and actions to work toward a goal.

---

## Q7 - Where Should Humans Still Make the Decision?

### A - Answer

There are situations where AI output should be inspected or approved by a human before action is taken.

| Situation | Possible failure | Required verification | Who approves? |
|---|---|---|---|
| Medical information | AI may provide incorrect or incomplete information | Reliable medical source and qualified professional | Qualified professional |
| Financial decision | AI may misunderstand risks or current information | Financial records and reliable financial sources | Responsible person/professional |
| Engineering calculation | Incorrect assumptions or calculations may cause failure | Independent calculation, test, or technical documentation | Engineer |
| Legal information | AI may miss jurisdiction-specific requirements | Current legislation and qualified legal advice | Qualified professional |
| Safety-critical decision | An incorrect recommendation could cause harm | Standards, procedures, testing, and expert review | Responsible human |

The general rule is:

> The more consequential the decision, the stronger the human review and verification should be.

### E - Evidence

The Week 1 assessment specifically asks for situations where AI output should be inspected or approved and what evidence is required before trusting the result.

Evidence can include:

- Official documentation.
- Standards.
- Experimental results.
- Independent calculations.
- Qualified professional review.

### V - Verification

For an important decision, I would verify the AI output using evidence appropriate to the specific domain.

I would not use the AI response itself as proof of its own correctness.

### R - Reflection

I learned that AI can assist with a decision without being responsible for the final decision.

Human verification is especially important when an incorrect answer could cause significant consequences.

---

## Q8 - Find AI Around You

### A - Answer

Examples of systems I may encounter in everyday life are:

| System / Feature | AI/ML involvement | Task type | Evidence / Verification | Conclusion |
|---|---|---|---|---|
| Face unlock on a smartphone | Likely AI/ML | Recognition | Manufacturer documentation should be checked | AI/ML if supported by evidence |
| Email spam filtering | AI/ML can be involved | Classification | Check the email provider's technical documentation | AI/ML if supported |
| Video recommendations | AI/ML can be involved | Recommendation | Check platform documentation | AI/ML if supported |
| Voice assistant | AI/ML | Recognition + generation | Check official technical documentation | AI/ML if supported |
| Calculator | Usually traditional software for basic arithmetic | Calculation | The mathematical operation is deterministic | Traditional software |

For commercial products, I should not claim that AI is used internally without evidence.

If reliable public evidence cannot be found, I should write:

> "Not enough public evidence to conclude."

### E - Evidence

The evidence should come from public technical documentation, official product documentation, research papers, or other reliable sources.

Simply saying that a product "looks intelligent" is not sufficient evidence.

### V - Verification

For each example, I would search for public evidence describing the technology used.

For at least one example, I would also ask whether a simpler rule-based system could produce similar behavior.

### R - Reflection

I learned that identifying AI requires more than observing intelligent behavior.

A system may produce useful results using ordinary rules, while another system may use machine learning.

When the internal implementation is not publicly documented, I should clearly state the uncertainty rather than guessing.

---

## Q9 - Prediction, Classification, and Generation

### A - Answer

| Example | Primary task | Reason |
|---|---|---|
| A. Predicting house prices | Prediction | The system estimates a numerical value. |
| B. Detecting whether an image contains a cat | Classification | The system assigns the image to a category such as cat/not cat. |
| C. Writing an email from a short instruction | Generation | The system generates new text. |
| D. Predicting whether a customer will cancel a subscription | Prediction | The system estimates a future outcome. |
| E. Summarizing a research paper | Generation | The system generates a new summary from the source information. |
| F. Identifying whether a transaction is fraudulent | Classification | The system assigns a category such as fraudulent/not fraudulent. |
| G. Generating an image from a text description | Generation | The system creates new image content. |
| H. Predicting the next word/token in a sentence | Prediction | The model predicts a likely next token. |

Next-token prediction is fundamental to modern language models because the model generates a response one token at a time.

A complete application can look like writing, summarization, coding, or question answering, but these outputs can be generated through repeated next-token prediction based on the available context.

### E - Evidence

The assessment defines three broad task types:

- Prediction
- Classification
- Generation

It also specifically asks why next-token prediction is fundamental to modern language models.

### V - Verification

I would check whether each example is primarily estimating a value, assigning a category, or generating content.

Some real systems combine multiple task types, so the table identifies the primary behavior.

### R - Reflection

I learned that prediction does not always mean predicting a number.

Classification predicts a category, while generation produces new content.

I also learned that language-model applications can appear very different even though next-token prediction is an important underlying mechanism.

---

## Q10 - Design Your Personal AI Verification Protocol

### A - Answer

My seven-step AI verification protocol is:

### Step 1 - Define the problem

Clearly state what I am trying to solve.

**Why:** Prevents me from asking the AI to solve the wrong problem.

**Failure caught:** Wrong interpretation of the task.

### Step 2 - Ask the AI

Give the AI a clear prompt and provide the necessary context.

**Why:** Better input can produce a more useful response.

**Failure caught:** Missing information or misunderstanding caused by an unclear prompt.

### Step 3 - Inspect the assumptions

Read the AI response carefully and identify assumptions it has made.

**Why:** AI may make assumptions that were not stated in the original problem.

**Failure caught:** Hidden or incorrect assumptions.

### Step 4 - Check the evidence and sources

Identify important factual claims and check them against reliable sources.

**Why:** AI output is not automatically evidence.

**Failure caught:** False, outdated, unsupported, or fabricated information.

### Step 5 - Test the result

Perform an experiment, calculation, comparison, simulation, or other appropriate test.

**Why:** A result should be tested when practical.

**Failure caught:** Errors that may not be obvious from reading the answer.

### Step 6 - Accept, reject, or revise

Based on the evidence, decide whether to accept the result, reject it, or revise it.

**Why:** The AI should support my engineering judgment rather than replace it.

**Failure caught:** Blind acceptance of an incorrect answer.

### Step 7 - Document and reflect

Record what I asked, what the AI produced, what I verified, and what I learned.

**Why:** Makes the work traceable and helps improve future decisions.

**Failure caught:** Losing track of how a result was obtained or verified.

Simple protocol:

```text
Define
  ↓
Ask
  ↓
Inspect
  ↓
Verify
  ↓
Test
  ↓
Accept / Reject / Revise
  ↓
Document + Reflect
