This project builds a system that extracts text from Delta Air Lines corporate documents, cleans and chunks the text, indexes it for retrieval, 
and allows users to ask questions through a Streamlit interface. The system uses TF-IDF similarity to retrieve relevant evidence and then passes 
it to a language model to generate grounded answers.

Files:

app.py
This is the main application. It loads the cleaned text chunks and KPI summary, initializes the TF-IDF retrieval system, connects to the language 
model, and displays the dashboard. The dashboard has two parts: a company snapshot (KPIs and a model-generated summary) and a question-answering 
section that uses evidence from the documents.

cleaning_and_chunking.ipynb
This notebook extracts text from the Delta corporate documents, cleans the text, and breaks it into overlapping chunks. The chunks are stored in CSV 
format and used by the retrieval system. The pipeline handles formatting issues and uses OCR for pages where PDF text extraction fails.

data_cleaning.ipynb
This notebook performs additional cleaning steps on the extracted text to remove artifacts, normalize spacing, and fix errors caused by PDF formatting.

retrieval.ipynb
This notebook tests and validates the TF-IDF retrieval system. It checks whether queries return relevant text chunks and helps verify the accuracy of 
the retrieval approach.

kpi_extraction.ipynb
This notebook extracts key financial and ESG data from the cleaned text (such as revenue, cargo revenue, number of segments, and fuel savings). It uses 
regex search and manual verification, and saves the results in kpi_summary.json, which is used by the Streamlit app.

Report - DSDA310 – Case Study 2.docx
The full written report explaining the project, the methods used, testing results, limitations, and conclusions.


Set Up and Run

Install dependencies using pip (Streamlit, sklearn, pandas, and Groq client).
Place the extracted and cleaned data files (chunks.csv and kpi_summary.json) in the directory data/delta/.
Run the Streamlit application with:
streamlit run app.py


Once running, the dashboard lets you:

View a summary of key metrics from Delta’s reports
Ask questions about the company based on retrieved evidence
This setup allows you to explore the Delta documents interactively while ensuring answers are grounded in the extracted text.
