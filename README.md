# auto-privacy-review-demo
Project for [AI Career Accelerator course taught by Nate Jones](https://maven.com/nate-b-jones/ai-career-accelerator). A tool to automate human led privacy reviews of data science projects. It is common that data scientists have to handle sensitive datasets and GDPR and other legislation enforce strict requirements on how and what data can be retained, transmitted, processed and reused. This tool performs a privacy review on a project proposal written by a data scientist following a predefined template and reasons if the project honors standards and if so, provides a provisional sign-off to be confirmed by a human reviewer.

# High-level design
1. AI system starts with a [data classification standard](grounding/data-classification-standard.md) and diagraming standard as grounding data
2. AI takes as input from the user a text explanation of the project and any relevant diagrams. The tool extracts and paraphrases as much information from the text and diagrams as possible to ensure that it understood the user's intent.
3. A reasoning model runs a privacy review session and either come up with follow up questions and if satisfied, provides a provisional signoff.
