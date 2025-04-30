All Information is derived from 
[Lee Boonstra's Prompt Engineering](https://www.gptaiflow.tech/assets/files/2025-01-18-pdf-1-TechAI-Goolge-whitepaper_Prompt%20Engineering_v4-af36dcc7a49bb7269a58b1c9b89a8ae1.pdf)

## LLM Output Settings

### Output Length (Tokens)
  - More Tokens = More Computation, Energy Consumption, Higher Costs, Longer Response Time
  - Does not necessarily reflect in shorter (in words) responses but rather stopping prediction after token limit is reached

#### Sampling Controls
  
  **Temperature (Degree of Randomness)**
  - 0 (greedy decoding) = deterministic = only highest probability token is selected (tiebreakers determined with encoded implementation)
  - Greater than 1  = random/"creative" = if high enough, all tokens become equally likely to be predicted

  **Nucleaus Sampling**
  - Top K: Selects the top K most likely tokens
      - Higher ==> More creative and varied
      - Lower ==> More Factual (not necessarily correct)
      - Top-K = 1 ==> Greedy Decoding
  - Top P: Selects top tokens whose cumulative probability does not exceed P
    - 0 == Greedy Decoding
    - 1 == All tokens in LLM

   **Understanding Combinations**
   - If temperature = 0 ==> top-K and top-P becomes irrelevant
   - If top-K = 1 ==> temperature and top-P is irrelevant
   - If top-P = 0 ==> temperature and top-K is irrelevant
   - If your task has 1 right/correct answer - set temperature to 0
   
---

### Prompting Techniques

**General/Zero Shot Prompting**
- Model temperature should be set to low value (close to 0)
- Zero Shot == No examples Provided

** One-shot & Few-Shot Prompting**
One-shot == Single Example
Few-Shot == Multiple examples (Typically 3-5)

Determining number of examples needed:
1. Complexity of the Task
2. Quality of Examples
3. Capability of LLM

Example Criteria:
1. Diverse
2. High Quality
3. Well Written (Avoid Typos/mistakes)
4. Include Edge Cases

**System, Contextual, and Role Prompting**
System Prompting: Overall Context + Purpose ==> Defining the "Big Picture"
  - Define fundamental capabilities + overall purpose
  - Useful for safety and toxicity

Contextual Prompting: Specific Details + Background Info ==> Understanding Nuances
  - Immediate, task-specific info
  - Dynamically Specific to Task
  - Looking to Guide LLM

Role Prompting: Assigns specific character or identity
  - Frames output style, voice, personality
  - Common Styles: Confrontational, Descriptive, Direct, Formal, Humorous, Influential, Informal, Inspirational, Persuasive

---

### Types of Prompting

**Step-back Prompting**
- Activates relevant background knowledge and reasoning before solving specific task
- Use Case: Ask to Generate a List of Items based on a metric, feed its output to the next prompt that asks for an action performed on the fed in output

1. First consider a general question related to the task
2. Feed its answer into the prompt for the specific task

**Chain of Thought (CoT)**
- Prompting Technique used to improve reasoning by generating intermediate reasoning steps
- Utilizes Simple Greedy Decoding
- Use Case: Any task that can be solved by "Talking it Through"
- Prompt Verbage Example: "Let's think step by step"

Pros:
- Low-Effort
- Effective with off-the-shelf LLM (no fine-tuning needed)
- Better robustness (less output performance drift between different models used)
- Allows users to identify errors in reasoning to adjust/re-prompt

Cons:
- Involves more output tokens ==> Predictions cost more money and time


**Self Consistency**
- Combines Sampling and Majoirty Voting to generate diverse reasoning paths andpicks the most consistent answer
1. Generate Diverse Reasoning Paths
   - Set Temperature to value close to 1
   - Feed LLM Same Prompt Multiple Times
2. Extract Output
3. Pick most common Output

**Tree of Thoughts (ToT)**
- Generalization of CoT to allow LLM to explore multiple different reasoning paths simultaneously\
- Well-suited for complex tasks that require exploration of thought

**ReAct (Reason & Act)**
Combines reasoning and a thought-action loop.
1. Reaons the Problem
2. Generates Plan of Action
3. Performs plan
4. Observe Results
5. Iterate until solution reached

**Automatic Prompt Engineering (APE)**
1. Generate Output Variants with a Prompt
2. Evaluate instructions based on a metric like BLEU or ROUGE
3. Select instruction with highest score

**Code Prompting**
1. Write/Compose
2. Explain Code
3. Translate into another Language
4. Debug + Review
---

### General Best Practices
1. Simplicity (concise + clear + easy)
2. Provide Examples (effective teaching tool)
3. Specify Input and Desired Output
4. Positive Instructions over Constraints (Avoid Negatives like Don't, Not etc.)
   - Encourage flexibility and creativity within defined boundaries
   - Tell what to do not what NOT to do
   - Use Constraints for safety, clarity, or specific requirements
5. Control Max Token Lengths
    - Directly Specify Token Length OR request specific length of response
6. Consider Experimentation + Variations
    - Input Format + Writing Styles (Question, Statement, Instruction)
    - Return Output as JSON, XML etc.

**CoT Best Practices**
1. Set Temperature to 0
2. Separate Reasoning and Answer

--- 

### Commonly Used Verbs that Describe Actions:

Act, Analyze, Categorize, Classify, Contrast, Compare, Create, Describe, Define, Evaluate, Extract, Find, Generate,

Identify, List, Measure, Organize, Parse, Pick, Predict, Provide, Rank, Recommend, Return, Retrieve, Rewrite,

Select, Show, Sort, Summarize, Translate, Write

### Template for Documenting Prompts

| Name | (Include Version) |
|:----| :----|
| Goal | Explanation of the Attempt |
| Model | Name and Version |
| Temperature | Token Limit |
| Top-k | Top-P |
| Prompt |  Indicate Changes |
| Output | Document Exact Output |


