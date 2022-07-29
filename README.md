# Abstractive Question Answering


## Welcome

The service receives a pair of text files for the context and the question and uses them as input to the pre-trained model.

## What’s the point?

The service outputs a text string that is the answer to the question in the specified context. 
Context is limited to 1000 tokens, question is limited to 100 tokens.

## Model details:
The service receives a couple of textual sentences in English and uses it as input for the QANet neural model trained to solve the question-answering task on the open-source question-answering SQuAD dataset and outputs the answer for a given question in the specified context. The model runs on a P100 GPU. The model is adapted to work with a long context at the architecture level, the input sequences are limited to 1000 and 100 words for a context and the question respectively.

## How does it work?

The user must provide the following inputs in order to start the service and get a response:

Inputs:

 -   `endpoint`: lqa.naint.tech.
 -   `method`: qa.
 -   `input_path`: Path to '\*.txt' file containing JSON representation of input arguments 'context' and 'question', and their respective values.

Example of input file content:

```
{"context": "Computational complexity theory is a branch of the theory of computation in theoretical computer science that focuses on classifying computational problems according to their inherent difficulty, and relating those classes to each other. A computational problem is understood to be a task that is in principle amenable to being solved by a computer, which is equivalent to stating that the problem may be solved by mechanical application of mathematical steps, such as an algorithm.", "question": "What branch of theoretical computer science deals with broadly classifying computational problems by difficulty and class of relationship?"}
```
You can call the service from SingularityNET CLI (`snet`).

Assuming that you have an open channel (`id: 0`) to this service:

```
$ snet client call 0 0.1 lqa.naint.tech qa samples/sample.txt
Read call params from the file: samples/sample.txt

answer: "Computational complexity theory"
```

## What to expect from this service?

Input data:

Context:  `Computational complexity theory is a branch of the theory of computation in theoretical computer science that focuses on classifying computational problems according to their inherent difficulty, and relating those classes to each other. A computational problem is understood to be a task that is in principle amenable to being solved by a computer, which is equivalent to stating that the problem may be solved by mechanical application of mathematical steps, such as an algorithm.`

Question: `What branch of theoretical computer science deals with broadly classifying computational problems by difficulty and class of relationship?`

Response:
`answer: "Computational complexity theory"`
