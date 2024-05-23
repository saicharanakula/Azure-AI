# Azure-AI
Extracting Text from Documents 
Create a Form Recognizer Resource:

Go to the Azure Portal.
Click on "Create a resource."
Search for "Form Recognizer" and select it.
Click "Create" and configure the resource settings (e.g., subscription, resource group, region).
Review and create the resource.

**Step 2: Prepare Your Document**

Ensure your document is in a supported format (e.g., JPEG, PNG, PDF).
For best results, use high-quality, clear images or PDFs.

**Step 3: Use the Form Recognizer Studio**

Access Form Recognizer Studio:

Go to the Form Recognizer Studio through the Azure Portal or directly via Form Recognizer Studio.
Choose a Prebuilt Model or Custom Model:

Prebuilt Models: For common document types like invoices or receipts.
Custom Models: For unique document layouts.
Analyze a Document Using a Prebuilt Model:

Select "Prebuilt" from the left menu.
Choose the type of document (e.g., Invoice, Receipt).
Upload your document.
Click "Analyze" to extract text and data.
Train a Custom Model (if needed):

Select "Custom" from the left menu.
Create a new project and provide project details.
Upload a set of labeled training documents.
Train the model with the labeled data.
Test the model with new documents to ensure accuracy.

**Step 4: Analyze Documents Using the API**

Get API Endpoint and Key:

Go to the Form Recognizer resource in the Azure Portal.
Copy the API endpoint and key from the "Keys and Endpoint" section.
Call the API:

Use tools like Postman or write a script in your preferred programming language (e.g., Python, C#).
Make an HTTP POST request to the Form Recognizer API endpoint.
Sample Python Code to Analyze a Document:
python
Copy code
import requests

endpoint = "https://<your-form-recognizer-endpoint>.cognitiveservices.azure.com/"
api_key = "<your-form-recognizer-key>"
model_id = "prebuilt-invoice"  # Use appropriate model id like 'prebuilt-receipt', 'prebuilt-invoice', etc.
document_path = "path/to/your/document.pdf"

headers = {
    "Ocp-Apim-Subscription-Key": api_key,
    "Content-Type": "application/pdf"
}

with open(document_path, "rb") as f:
    data = f.read()

response = requests.post(
    f"{endpoint}/formrecognizer/v2.1/layout/analyze?modelId={model_id}",
    headers=headers,
    data=data
)

print(response.json())

**Step 5: Process and Use the Extracted Data**

The API response will be in JSON format, containing the extracted text and structured data.
Parse the JSON response to retrieve the information you need.
Integrate the extracted data into your application or workflow.

**Step 6: Monitor and Optimize**

Use Azure Monitor and Application Insights to monitor the performance of your Form Recognizer service.
Continuously evaluate the accuracy of the extracted data and refine the custom models if necessary.
By following these steps, you can effectively use Azure Form Recognizer to extract text and structured data from various types of documents.
