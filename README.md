# AIRO

AIRO stands for AI-Retrieval-Optimization. This is inspired by the term SEO (Search Engine Optimization), which is a practice of optimizing a website or webpage to increase its visibility in search engine results pages (SERPs). 

In today’s world, we are seeing AIs like Large Language Models (LLM) consuming natural launage documents, retrieving information, and generating outputs based on the documents. With proper tools, it often works like magic (e.g. imagine asking LLM to read the entire 10K report of Microsoft and answer questions for you!). But it’s also clear the property of the document itself can affect results significantly. 

As an author or maintainer of the documents, you may want to learn some tips for help AI understand your document better, and, giving your document better visiblity and impact as a result!

# Notes

The tips below are largely influenced by popular LLM frameworks like LlamaIndex and Langchain. However they should be generally applicable for other LLM retrieval approaches, including vanillia prompts. 

It should be also noted that many of the tips here are also beneficial for human readers. After all, AI is trained to follow the same way human communicate via natural languages : )

# Tips
1. Add structures to your document. 

Utilize title, subtitle, headings in your document to make it structured. 

2. Add metadata to your document directly if possible

E.g. Dates, author, department, status. Although this can be added separately by the indexing framework, it’s often helpful to include them directly in the doc, both for the embedding search and also for the LLM response synthesize. 


3. Include explainations and context for terms, jagons and acronyms

Obviously this is helpful for human readers as well, although we may be tempted to just include a link to the context/explanation. While indexing frameworks may be able to help retrieve the linked context for you, it’s just easier to put the context in the document directly. You would also have the oppotunity to tailor the context to be best fit the document (nobody really wants to read a 20-page long document to learn what DNRX actually means in the context). 

4. Include good summary at the beginning. 

This is helpful for LLM to quickly get a sense about this document. This can particularly useful for create-and-refine approach - a good summary in the beginning may help the LLM get a good start for a more complicated task. 

5. Keep format and typings straight

Examples include always use proper space to separate words, and avoids typo as much as possible. Although more sophisticaed LLMs tend to work around these issue better, it still degrades performance with weaker LLMs. It also affects the embeddings. Bad format or typos makes the vector embedding further away from their semantically similar neighbors. 

6. Avoid prompt delimiters to also appear in the context text.

An example is you use \`\`\`{context}\`\`\` within your prompt to enclose the context text. However, the context may itself contain ``` already, and this confuses the model and produces worse result. We should avoid any structural patterns to appear in both prompt and context text (by addressing it either in the prompt or in the document). If you don't have control or don't want to change the prompt, you may want to examine your document to make sure it doesn't have the same structural pattern. 

For example, `---------------------` is commonly used in frameworks like LlamaIndex as delimiter. Avoid this in your document. 

7. Consider adding keywords in the document

This gives a bit of old school SEO vibe - but still a useful approach for AI understanding. Example use case may be you want to add some keywords which don’t have much chance to appear in the document naturally, but helps to triage and prompt people about the context and relevancy to other materials. 

# Closing words
This list is an work in progress. If you have tips to add to it, feel free to contribute in a PR. Good luck in the AI-Retrieval game!
  

This list is an work in progress. If you have tips to add to it, feel free to contribute in a PR. Good luck in the AI-Retrieval game!
