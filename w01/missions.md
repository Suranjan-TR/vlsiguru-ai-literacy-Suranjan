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
