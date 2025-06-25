# Automated-Metadata-Generator
Open Project: Automated Metadata Generator (MARS)
Submitted by : Aagam Bandi (22124001)

Approach used in the Project:
1. In the problem statement we are told that the files may be of the format txt, docx or pdf. For docx and txt files we can directly extract text without doing ocr as they contain text in digitally recognizable format.
2. For pdf files, we might have to do ocr as they may be a scanned pdf and may not contain the text in digitally recognisable format. So we are using a ocr_fallback_threshold where if the text extracted from the page of pdf is less than a particular threshold (ocr_fallback_threshold) it would mean that the page is scanned and ocr is needed. Otherwise we would directly extract all the text. We are doing ocr for all the pages as it will slow down the process of metadata generation. If there is a little text present in the pdf in form of image elements we can skip them as it won't matter in our overall goal of semantically rich metadata generation.
3. Now since most llms have input token limit, so we cannot give the whole pdf to the llm for metadata generation. So instead we'll be first chunking the pdf, and using the llm to summarize each chunk while preserving the metadata and then combine the summaries of all the chunks.
4. We are also using RAG in our approach. Once the combined summary has been generated we will give the combined summary to the llm telling it to generate relevant questions that can be answered using the pdf and can be used in RAG to retrieve chunks which will be relevant for metadata generation.
5. Now we are giving the chunks retrieved from RAG along with the combined_summary to the llm for metadata generation. And we are getting the metadata as the final output.

IMPORTANT NOTE: 
I have done the whole process step by step in different cells of the ipynb file and then combined all the steps in the last cell block of the ipynb code. You can run the last cell block to generate the local or public url of the interface of the automated metadata generator. Make sure to run the last code cell block to generate a new link for the interface metadata generator.

