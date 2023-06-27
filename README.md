# AIRO
AIRO stands for AI-Retrieval-Optimization. This concept is inspired by the term [SEO](https://en.wikipedia.org/wiki/Search_engine_optimization) (Search Engine Optimization), a practice of optimizing a website or webpage to increase its visibility in search engine results pages (SERPs).

In today's world, we are witnessing AI systems like Large Language Models (LLM) consume natural language documents, retrieve information, and generate outputs based on the input documents. With the appropriate tools, it often works like magic (e.g. imagine asking an LLM to read the entire 10K report of Microsoft and answer questions for you!) However, it's also clear that the properties of the document itself can significantly influence results.

As an author or maintainer of documents, you may want to learn some tips to help AI understand your document better, thus giving your document better visibility and impact!

## Notes
The tips below are largely influenced by popular LLM frameworks like [LlamaIndex](https://github.com/jerryjliu/llama_index) and [Langchain](https://github.com/hwchase17/langchain). However, they should be generally applicable for other LLM retrieval approaches, including vanilla prompts.

It should also be noted that many of the tips here are beneficial for human readers. After all, AI is trained to mimic the way humans communicate through natural languages :)

## Tips

### 1. Add structure to your document.

Utilize titles, subtitles, headings in your document to make it well-structured. In addition to helping LLMs understand the internal structure and hierarchy of your document, this often helps truncating it into smaller pieces, which is common for AI-retrieval for long documents. 

### 2. Add metadata to your document directly if possible

For example, dates, author, department, status. Although this can be added separately by the indexing framework, it’s often helpful to include them directly in the document, both for the embedding search and for the LLM response synthesis.

### 3. Include explanations and context for terms, jargons, and acronyms

Obviously, this is helpful for human readers as well, although we may be tempted to just include a link to the context/explanation. While indexing frameworks may help retrieve the linked context for you, it’s easier to put the context in the document directly. You also have the opportunity to tailor the context to best fit the document (nobody really wants to read a 20-page long document to learn what DNRX actually means in the context).

### 4. Include a good summary at the beginning.

This helps the LLM quickly understand the document. This is particularly useful for the create-and-refine approach - a good summary at the beginning may help the LLM get a good start for a more complicated task.

### 5. Maintain consistency in format and typing

Examples include always using proper space to separate words, and avoiding typos as much as possible. While more sophisticated LLMs tend to work around these issues better, it still degrades performance with weaker LLMs and affects the embeddings. Bad format or typos can make the vector embedding further away from their semantically similar neighbors.

### 6. Avoid having prompt delimiters in the context text.

An example is when you use \```{context}\``` within your prompt to enclose the context text. However, the context may itself contain ``` already, and this can confuse the model and produce worse results. We should avoid any structural patterns appearing in both the prompt and context text (by addressing it either in the prompt or in the document). If you don't have control or don't want to change the prompt, you may want to examine your document to ensure it doesn't contain the same structural pattern.

Another example: `---------------------` is commonly used in frameworks like [LlamaIndex](https://github.com/jerryjliu/llama_index) as a delimiter. Avoid having this in your document.

### 7. Consider adding keywords/synonyms in the document

This gives a bit of an old-school SEO vibe - but it's still a useful approach for AI understanding. An example use case might be wanting to add some keywords which don’t naturally appear in the document, but help to triage and prompt people about the context and relevancy to other materials.

## Closing Words
This list is a work in progress. If you have tips to add, please feel free to contribute via a PR. Good luck in the AI-Retrieval game!








