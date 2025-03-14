
# CSV & Excel Data Filtering Chatbot with LLM Integration

This project is a Python-based chatbot that leverages an LLM (using the OpenAI GPT-4-o-mini model) to interact with CSV datasets. It performs the following tasks:

- **Data Loading & Summarization:**  
  Loads a CSV file into a Pandas DataFrame and computes a summary of the dataset.

- **Dynamic Filtering:**  
  Uses the LLM to generate Python code that filters the dataset—both rows and columns—based on a user query. The code is then executed (with precautions) to obtain the filtered dataset.

- **Minimal Answer Generation:**  
  Passes the filtered dataset (both its complete content and summary) to the LLM to generate a final, minimal-answer output with each answer on a separate line, reproducing values exactly as they appear in the table.

- **Submission Processing:**  
  Reads an Excel file containing questions and expected answers, applies the filtering for each question, and appends the results (filtered row indices, filtered column indices, and the generated answer) to the same Excel file.

---



## Requirements



You can install the required packages using pip:

```bash
pip install -r requirements.txt
```

---

## Setup

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/arya2004/infenion-hackathon.git
   cd infenion-hackathon
   ```

2. **Set Up Environment Variables:**

   Create a `.env` file in the project root and add your OpenAI API key:

   ```env
   OPENAI_API_KEY=your_openai_api_key_here
   ```

3. **Prepare Input Files:**

   - **CSV File:**  
     Place your CSV dataset (e.g., `input_table.csv`) in the project folder.
     

---

## Usage

### Running the Chatbot Process

To run the interactive CSV filtering process using the chatbot:

1. Open a terminal in your project directory.
2. Execute the script:

   ```bash
   python main.py
   ```

   - The script will load the CSV file, generate filtering instructions from the LLM, execute them, and then generate a final answer based on the filtered data.

### Processing Submission from Excel

The project also includes a function to process a submission Excel file. This function:

- Iterates over each question in the Excel file.
- Uses the CSV dataset to generate a filtered DataFrame based on the LLM instructions.
- Obtains the final answer from the LLM using the filtered data.
- Updates the Excel file with additional columns after processing each question.

You can adjust developer options by setting the `dev_start` and `dev_end` indices. By default, if both are `-1`, the entire sheet is processed.

---



## Safety Warning

> **WARNING:**  
> The code uses `exec()` to execute Python code generated by the LLM. Executing untrusted code can be extremely dangerous. For production use, consider implementing rigorous sanitization, sandboxing, or alternative approaches to executing dynamically generated code.

---

## License

This project is licensed under the [MIT License](LICENSE).

