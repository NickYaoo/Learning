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

---

### Best Practices
1. Simplicity
2. Provide Examples
3. Input and Output Specificity
4. Positive Instructions over Constraints (Using Negatives like Don't, Not etc.)
5. Control Max Token Lengths
6. Consider Experimentation + Variations
