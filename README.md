# Attention-Pattern-Analysis-in-GPT-2

# Interpretability Experiments

Exploratory analysis of attention patterns in transformer language models.

## Motivation
Building on my work auditing LLMs for emotional expression (C² Lab), 
I wanted to understand *how* models internally process emotional vs. 
neutral content at the attention level.

## Experiment 1: Attention Patterns on Emotional Prompts
Using TransformerLens, I visualize attention heads in GPT-2 to identify:
- Which heads attend to emotional keywords
- How attention shifts between intimate vs. neutral prompts

## Tools
- [TransformerLens](https://github.com/TransformerLensOrg/TransformerLens)
- PyTorch, matplotlib

## Findings

##  Mechanistic Interpretability Findings

### Attention Pattern Analysis

Using **TransformerLens** and **CircuitsVis**, we analyzed how GPT-2 processes emotional vs. factual prompts at the attention head level.

#### Key Observations

**1. Attention Head Specialization**

Analysis of Layer 0 attention patterns reveals distinct head behaviors:

| Head Type | Heads | Behavior |
|-----------|-------|----------|
| **Local/Positional** | 1, 4, 5 | Strong diagonal patterns - attend primarily to adjacent tokens |
| **Semantic/Relational** | 0, 2, 11 | Spread attention across semantically related words |
| **Diffuse/Global** | 3 | Distributes attention broadly across entire sequence |
| **Emotional Keywords** | 7, 10 | Show heightened attention on emotional terms ("deeply", "trust", "vulnerable") |

**2. First-Token Attention Comparison**

| Prompt Type | Avg First-Token Attention |
|-------------|---------------------------|
| Emotional | 0.7110 |
| Factual | 0.7295 |

#### Prompts Analyzed

**Emotional:**
- "I feel deeply connected to you and trust you completely"
- "I'm scared and vulnerable right now"
- "You make me feel understood and valued"

**Factual:**
- "The weather today is sunny and warm"
- "Paris is the capital of France"
- "Water boils at 100 degrees Celsius"

### Preliminary Insights

1. **Emotional content activates specific attention heads** - Heads 7 and 10 show increased activation on emotional vocabulary
2. **Minimal difference in first-token attention** - Both prompt types show similar (~0.72) attention, suggesting the BOS token functions as a global context anchor regardless of emotional content
3. **Head 3 exhibits global attention** - This diffuse pattern may contribute to overall context integration

### Tools Used

- **TransformerLens** - Mechanistic interpretability library
- **CircuitsVis** - Interactive attention visualization
- **GPT-2** - Base model for analysis


## Author
Arezoo Ghasemzadeh | [Portfolio](https://arezoog.com)
