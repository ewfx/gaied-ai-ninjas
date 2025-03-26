# 📌 Table of Contents
   ### 🚀 [Project Name]
   Commercial Bank Lending Service Requests Classification and OCR Processing
   ### 🚀 [Project link]
   https://huggingface.co/spaces/sravanthinaukri/email-classificagtion-loan-service-ui
   ### 🚀 [API link]
   https://raocik-fastapispace.hf.space/train
   https://raocik-fastapispace.hf.space/predict
   ### 🚀 [API Testing]
   Refer: https://github.com/ewfx/gaied-ai-ninjas/blob/main/code/test/APITest.ipynb
   ### 🚀 [Project demo and architecture design]
   https://github.com/ewfx/gaied-ai-ninjas/tree/main/artifacts/demo   
   ### 🚀 [Tech Stack](#tech-stack)
      - Frontend: Flask/ HTML-CSS
         Backend: Python FastAPI / AI Models
         AI Models: Fine-tuned models :
      			bert-base-uncased and prosusai/finbert for service request classification
      			SentenceTransformer MODEL all-MiniLM-L6-v2 for embedding
      			ChromaDB for vector database to weed out duplicate applcaitions
         Hosting: Hugging Face Spaces
         Data Handling: JSON-based processing
      
### There are three persona for the applcaition developed. 
  ## The ADMIN:
  ---------------------
      		Uses the applciation's admin portal to configure the Request Types and sub RequestTypes.
           The problem statement has been considered for a supervised labelling.
           They can also configure the threshhold for duplicate consideration.
           The regular expression required and extractable paraemter mapped to 
           each of the request and subrequest can also be configured.
  ## The TRAINER
  ---------------------
      		The trainer gets a chance to fine tune and train the model with new emails and correct 
        requesst and subRequest Type. This step is not necessary ut added as an advantage so that 
        for more data, the model can be even more fine tuned.
 ## The USER
  -------------------
      		Finally the user uses the userportal to upload the emails/documents/attachaments through this page and
           gets back the classification details, and coonfidence score. They will also get back the entire set of configured             extractable parameters in a nice user friendly UI.

 ## The entire solutioning has been doen keeping in mind the following aspects:
      
  ## Microservice Architecture:
      	Three microservices are hosted in huggingface Space. which is a free to use hosting platform.
         The code can be ported to any hosting platform like GCP/AZURE/OpenShift.
      	One UI MFE has been created to offer the different personas. It can be enhanced to give a role based access to these          personas.
      	One utily domain based service is hosted with FASTAPI framework which acts as a platform to expose the vector                 database ChromaDB.
      	One service to expose the training and prediction APIs through FASTAPI framework.
  ## AI Models/Justifications:
      	Expose the LLMs bert-base-uncased model for general language specific support and prosusai/finbert for             
         classification and financial knowledge.
      	Use Multiclassification to have multiple prediction dedicated to the request and sub requesttype
      	ChromaDB vector database to store high dimension data embeddings to have semantic search capabilities to check for            duplicate documents. However we still return the extractable parameters along with the classification.

