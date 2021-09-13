# Work in Progress

# How to train 6 Billion GPT-J with Hugging Face Transformers and Amazon SageMaker

### GPT-2/GPT and causal language modeling
The following example fine-tunes GPT-2 on WikiText-2. We're using the raw WikiText-2 (no tokens were replaced before the tokenization). The loss here is that of causal language modeling.

```bash
hyperparameters={
    'model_name_or_path':'EleutherAI/gpt-j-6B',
    'dataset_name':'cc_news',
    'per_device_train_batch_size': 2,
    'per_device_eval_batch_size': 2,
    'do_train': True,
    'do_eval': True,
    'num_train_epochs': 2,
   # 'output_dir':'/opt/ml/model',
    'max_steps': 500,
}
```

Get the datasets: you can either provide your own CSV/JSON/TXT training and evaluation files (see below)
or just provide the name of one of the public datasets available on the hub at https://huggingface.co/datasets/
(the dataset will be downloaded automatically from the datasets Hub).

For CSV/JSON files, this script will use the column called 'text' or the first column if no column called
#'text' is found. You can easily tweak this behavior (see below).

To run on your own training and validation files, use the following command:

```bash
hyperparameters={
    'model_name_or_path':'EleutherAI/gpt-j-6B',
    'train_file':'/opt/ml/input/data/train/<my-train-dataset.json>',
    'validation_file':'/opt/ml/input/data/test/<my-test-dataset.json>',
    'per_device_train_batch_size': 2,
    'per_device_eval_batch_size': 2,
    'do_train': True,
    'do_eval': True,
    'num_train_epochs': 2,
   # 'output_dir':'/opt/ml/model',
    'max_steps': 500,
}
