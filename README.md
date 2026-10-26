# Research Paper Reading & Recommendation Agent

## Part 1: Design 

This design describes the **Paper Reading & Recommendation Agent**, an LLM-powered agent for academic literature analysis and relevant paper recommendation.

**PEAS Specification**

- **Performance     measure**: The agent is evaluated by     its ability to accurately extract core findings, methodologies and     experimental metrics from uploaded papers, answer paper-related queries,     recommend thematically relevant literature, and refrain from hallucination     by refusing uncertain answers.
- **Environment**: The environment consists of user natural     language inputs, uploaded academic PDF documents, parsed paper text, and a     local vector knowledge base for retrieval.
- **Sensors**: Text parser for PDF files, user text input     interface, and vector retrieval tool to fetch content from the knowledge     base.
- **Actuators**: Generated natural language responses,     extracted paper summaries, lists of recommended papers, and invocations of     custom Python helper functions for citation formatting and keyword     extraction.

**Environment Properties**

The environment is **partially observable, stochastic, sequential, static, discrete, single-agent**.

1. *Partially     observable*: The agent can only access     papers that have been uploaded and embedded into the knowledge base; it     cannot access external unseen literature or information hidden inside     figures and tables.
2. *Stochastic*: Given the same user query, the underlying     LLM may produce responses with slight variations in wording.
3. *Sequential*: Subsequent turns in conversation depend on     the full dialogue history, and the agent can follow up on prior discussion     about papers.
4. *Static*: Stored paper content and the vector     knowledge base do not change spontaneously while the agent reasons;     modifications only occur when a user manually uploads new documents.
5. *Discrete*: All inputs and agent actions are discrete     textual tokens, with a finite set of available actions: answer the     question, call a Python tool, or refuse to respond.
6. *Single-agent*: Only this paper analysis agent acts within     the environment. The human user is treated as part of the environment     rather than a separate agent.

**Agent Type**

This is a **model-based agent**. The agent maintains an internal state model including conversation history, parsed paper content and the state of the retrieval knowledge base. It makes action decisions (whether to retrieve documents, invoke functions, reply or refuse) based on this stored internal representation of its text environment. It is **not a learning agent** under this course definition: the base LLM is frozen, no fine-tuning or online policy update is implemented, and the agent cannot autonomously improve its decision rules through interaction.

**Limits**

- **Capabilities**: The agent can parse uploaded academic PDFs,     generate summaries, answer questions grounded on stored paper text,     extract keywords, format citations and recommend similar relevant papers     by calling predefined Python functions.
- **Refusal     rules**: The agent must refuse to     answer when (1) the question refers to papers or facts not present inside     its knowledge base; (2) the required information exists only in images,     charts or unparsed parts of the uploaded document; (3) the query is     ambiguous and lacks sufficient context; (4) retrieved evidence is     insufficient to form a confident, reliable answer, to avoid hallucinated     content.

 

  

*Differences between supervised and unsupervised learning*

| Item      | Supervised Learning                                          | Unsupervised Learning                                        |
| --------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Data      | Labelled data (inputs paired with ground-truth  labels)      | Unlabelled raw data, no ground-truth annotations             |
| Objective | Learn input–output mappings to perform prediction  tasks (classification, regression) | Discover intrinsic latent patterns: clustering,  dimensionality reduction, feature extraction |
| Example   | Linear regression, image lesion classification  (images + lesion labels) | K-means clustering, PCA, autoencoders,  contrastive learning pre-training |

 

 

 

 

 

 

 

## References

Sayres, R., Hammel, N., & Liu, Y. (2020). Artificial intelligence, machine learning and deep learning for eye care specialists. *Annals of Eye Science*, *5*, 18. https://doi.org/10.21037/aes.2020.02.05

Neupane, S., Tripathi, H., Mittal, S., Rahimi, S., & Gupta, V. (2025). Towards a HIPAA compliant agentic AI system in healthcare. *arXiv preprint arXiv:2504.17669*. https://arxiv.org/abs/2504.17669

Qiu, Y., Hu, Z., Wang, Z., Li, H., Qiao, Y., Huang, Y., Shang, S., Xu, R., & Sun, M. (2025). BioMARS: A multi-agent robotic system for autonomous biological experiments. *arXiv preprint arXiv:2507.01485*. https://arxiv.org/abs/2507.01485

Ali, M. (2023). Quantifying overfitting: Introducing the overfitting index. *arXiv preprint arXiv:2308.08682*. https://doi.org/10.48550/arXiv.2308.08682

Topol, E. J., Price, W. N., & Narayan, S. (2019). Key challenges for delivering clinical impact with artificial intelligence. *BMC Medicine*, *17*(1). https://doi.org/10.1186/s12916-019-1426-2

 

 