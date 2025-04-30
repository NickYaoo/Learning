All Information is derived from 
[Lee Boonstra's Prompt Engineering](https://www.gptaiflow.tech/assets/files/2025-01-18-pdf-1-TechAI-Goolge-whitepaper_Prompt%20Engineering_v4-af36dcc7a49bb7269a58b1c9b89a8ae1.pdf)

## LLM Output Settings

### Output Length (Tokens)
  - More Tokens = More Computation, Energy Consumption, Higher Costs, Longer Response Time
  - Does not necessarily reflect in shorter (in words) responses but rather stopping prediction after token limit is reached

#### Sampling Controls
  
  Temperature (Degree of Randomness)
  - 0 (greedy decoding) = deterministic = only highest probability token is selected (tiebreakers determined with encoded implementation)
  - Greater than 1  = random/"creative" = if high enough, all tokens become equally likely to be predicted

  Nucleaus Sampling
  - Top K:
  - Top P:
    
---

### Prompting Techniques

---

### Types of Prompting
**ReAct (Reason & Act)**


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


