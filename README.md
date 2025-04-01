# -Contextualized-Sentiment-Classification-with-BERT-on-CFIMDB
 Implemented a BERT-based classifier for fine-tuned sentiment analysis on the CFIMDB dataset, leveraging pooled sentence embeddings and dropout-regularized projection layers. Developed data preprocessing and training pipelines to support both pretraining and downstream evaluation.
📚 Contextualized Sentiment Classification with BERT on CFIMDB
This project implements a BERT-based classifier for sentiment analysis on the CFIMDB dataset, adapted from CMU’s 11-747: Neural Networks for NLP course. The system supports both pretraining and fine-tuning modes using Hugging Face’s transformers library.

🛠️ Key Components Implemented
BertSentClassifier (in classifier.py)

Encodes sentences using BERT’s pooled output

Applies dropout regularization and linear transformation for classification

Supports both pretraining and task-specific fine-tuning

BertDataset & create_data

Loads and tokenizes raw text data

Maps sentences and labels to BERT-compatible input format (input IDs, attention masks, labels)

Training & Evaluation Pipelines

Fine-tuned BERT using custom run_exp.sh script

Logged training metrics and saved predictions for dev and test sets in both modes

📁 Directory Structure (Submission Format)
bash
Copy
Edit
CAMPUSID/
├── classifier.py                      # Classifier logic with BERT-based architecture
├── utils.py                           # Utility functions (no changes needed)
├── README.md                          # This file
├── cfimdb-dev-pretrain-output.txt    # Dev predictions (pretrain mode)
├── cfimdb-test-pretrain-output.txt   # Test predictions (pretrain mode)
├── cfimdb-train-pretrain-log.txt     # Training logs (pretrain)
├── cfimdb-dev-finetune-output.txt    # Dev predictions (finetune mode)
├── cfimdb-test-finetune-output.txt   # Test predictions (finetune mode)
├── cfimdb-train-finetune-log.txt     # Training logs (finetune)
├── run_exp.sh                         # Shell script for running experiments
└── setup.sh                           # Environment and dependency setup
🔧 Setup Instructions
Run the following to set up dependencies and environment:

bash
Copy
Edit
bash setup.sh
🚀 Running the Classifier
Replace CAMPUSID with your ID and run:

bash
Copy
Edit
mkdir -p CAMPUSID
python3 classifier.py --option finetune --epochs 3 --lr 2e-5 \
  --train data/sst-train.txt \
  --dev data/sst-dev.txt \
  --test data/sst-test.txt
Also supports --option pretrain for running in pretraining mode.

📈 Output & Evaluation
All output files (dev/test predictions and training logs) are generated and stored in the respective text files, enabling reproducibility and evaluation across both modes.

📜 Acknowledgements
This project builds upon the transformers library (Apache License 2.0) and CMU’s CS11-747 NLP course codebase.
