# Reasoning in Large Language Models
Reasoning elicited from model weights.



## Elicit Reasoning
[Chain-of-Thought Prompting Elicits Reasoning in Large Language Models](https://arxiv.org/abs/2201.11903)
- **Chain of Thoughts (CoT)**
    - A series of intermediate reasoning steps.
    - Example:
        - Task: Question Answering
        - input
        - [intermediate steps will be generated]
        - [answer will be generated]


<img src="./CoT/image-2.png" alt="Alt text" style="width:100%; height:auto; display:block; margin-left:auto; margin-right:auto;">


Wide range of tasks:
<img src="./CoT/image-3.png" alt="Alt text" style="width:80%; height:auto; display:block; margin-left:auto; margin-right:auto;">


Contribution
- Chain of thoughts (CoT) = a series of intermediate reasoning steps
- Instead of asking a question directly, provide a series of intermediate reasoning steps.



## Zero-shot CoT (zero-shot reasoning)

[Large Language Models are Zero-Shot Reasoners](https://arxiv.org/abs/2205.11916)

- **Zero-shot**
    - Model has never trained on the task. (as far as we know!)
    - Questions are asked LLMs without any context.


    - Example:
        - Task: Question Answering
        - input
        - [answer will be generated]


- **Few-shot**
    - Again, model has never trained on the task.
    - But, model is given a few examples of the task as follows:
        - Task: Question Answering
        - Examples: 
            - Q1
            - A1
            ...
            - input
            - [answer will be generated]


- **Few-shot-CoT**
    - In each exemplar, model is also given intermediate steps to solve the task.
    - Example:
        - Task: Question Answering
            - Q1
            - Intermediate steps to solve Q1
            - A1
            ...
            - input
            - [intermediate steps will be generated]
            - [answer will be generated]


- **Zero-shot-CoT**
    - Unlike few-shot-CoT, model is not given any intermediate steps.
    - The provided prompt encourages the model to generate intermediate steps by adding "Let's think step by step" at the beginning of the prompt.
    - Example:
        - Task: Question Answering
        - input
        - Let's think step by step.
        - [intermediate steps will be generated]
        - [answer will be generated]


<img src="./CoT/image.png" alt="Alt text" style="width:100%; height:auto; display:block; margin-left:auto; margin-right:auto;">


Contributions
- Let's think step by step.
- It can be complementary to the CoT. E.g., reasoning steps start with "Let's think step by step" and continue with CoT.



## Re-Reading Prompt

[Re-Reading Improves Reasoning in Large Language Models](https://arxiv.org/abs/2309.06275)

- **Zero-shot-CoT**
    - Let's think step by step.
- **Zero-shot-CoT+Re-Reading**
    - Let's think step by step.
    - Re-read the prompt.
    - "bidirectional" understanding of the prompt.


<img src="./CoT/image-1.png" alt="Alt text" style="width:90%; height:auto; display:block; margin-left:auto; margin-right:auto;">


Contributions:
- Provide a prompt twice.



## Self-Ask

[Measuring and Narrowing the Compositionality Gap in Language Models](https://arxiv.org/abs/2210.03350)

Compositional Reasoning:
* Cognitive process of understanding complex concepts or systems by breaking them down into their constituent parts and understanding the relationships between these parts.


<img src="./CoT/image-4.png" alt="Alt text" style="width:100%; height:auto; display:block; margin-left:auto; margin-right:auto;">


Contributions:
- This method can be used with retrieval information.

<img src="./CoT/image-5.png" alt="Alt text" style="width:35%; height:auto; display:block; margin-left:auto; margin-right:auto;">



## Rephrase and Respond

[Rephrase and Respond: Let Large Language Models Ask Better Questions for Themselves](https://arxiv.org/abs/2311.04205)

Motivating Example
<img src="./CoT/image-6.png" alt="Alt text" style="width:80%; height:auto; display:block; margin-left:auto; margin-right:auto;">


**Rephrase and Respond**
- One-step RaR
    - {Question}
    - Rephrase and expand the question, and respond.


- Two-step RaR
    - Let Stronger LLMs Rephrase for Weaker LLMs to Respond.
    - step 1:
        - {Question}
        - Given the above question, rephrase and expand it to help you do better answering. Maintain all information in the original question.
    - step 2:
        - {Question}
        - {Rephrased Question}
        - Use your answer to the rephrased question to answer the original question.


<img src="./CoT/image-7.png" alt="Alt text" style="width:100%; height:auto; display:block; margin-left:auto; margin-right:auto;">


Learning from few-shot exemplars:
<img src="./CoT/image-8.png" alt="Alt text" style="width:100%; height:auto; display:block; margin-left:auto; margin-right:auto;">


Contributions:
- Let LLMs ask better questions for themselves by rephrasing and expanding the question.
- "Rephrase and Respond"
- **One-step RaR** and **Two-step RaR**



## Recursive Decomposition
[Least-to-Most Prompting Enables Complex Reasoning in Large Language Models](https://arxiv.org/abs/2205.10625)

- Easy to hard generalization
- Least to most prompting
- In contrast to CoT, least-to-most prompting starts with the simplest form of the task and gradually increases the complexity of the task by asking questions.


<img src="./CoT/image-9.png" alt="Alt text" style="width:90%; height:auto; display:block; margin-left:auto; margin-right:auto;">


Leat-to-Most Prompting:
1. Decomposition. The prompt in this stage contains constant examples that demonstrate the
decomposition, followed by the specific question to be decomposed.
1. Subproblem solving. The prompt in this stage consists of three parts: (1) constant examples demonstrating how subproblems are solved; (2) a potentially empty list of previously
answered subquestions and generated solutions, and (3) the question to be answered next.



## Contrastive Reasoning
[Contrastive Chain-of-Thought Prompting](https://arxiv.org/abs/2311.09277)
<img src="./CoT/image-11.png" alt="Alt text" style="width:190%; height:auto; display:block; margin-left:auto; margin-right:auto;">



## Self-consistency
[Self-Consistency Improves Chain of Thought Reasoning in Language Models](https://arxiv.org/abs/2203.11171)

<img src="./CoT/image-13.png" alt="Alt text" style="width:80%; height:auto; display:block; margin-left:auto; margin-right:auto;">



## Other Approaches
<img src="./CoT/image-10.png" alt="Alt text" style="width:80%; height:auto; display:block; margin-left:auto; margin-right:auto;">



## References
1. [Chain-of-Thought Prompting Elicits Reasoning in Large Language Models](https://arxiv.org/abs/2201.11903)
2. [Large Language Models are Zero-Shot Reasoners](https://arxiv.org/abs/2103.13425)
3. [Re-Reading Improves Reasoning in Large Language Models](https://arxiv.org/abs/2109.07547)
4. [Measuring and Narrowing the Compositionality Gap in Language Models](https://arxiv.org/abs/2203.11171)
5. [Rephrase and Respond: Let Large Language Models Ask Better Questions for Themselves](https://arxiv.org/abs/2203.11171)
6. [Least-to-Most Prompting Enables Complex Reasoning in Large Language Models](https://arxiv.org/abs/2203.11171)
7. [Self-Consistency Improves Chain of Thought Reasoning in Language Models](https://arxiv.org/abs/2203.11171)
8. [Tree of Thoughts: A Hierarchical Approach to Reasoning in Large Language Models](https://arxiv.org/abs/2203.11171)