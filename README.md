# Survey on mitigating hallucination in LLMs

In this project, we are doing a comparative study of techniques to reduce unsupported or "hallucinated" outputs in LLMs

As LLMs are increaingly used for various tasks, they can produce answers that convincing with confifence however, they can
be factually incorrect or may generate unfounded data.

We are trying to explore and benchmark several mitigation strategies, which are aimed to:

1. Understand the existing metrics and exploring other reliable evaluation tools
2. Study implementation details and quantifying the accuracy improvements

## Model

For this survey, we are using **Gemma-2B** which is an open-source transformer-based LLM, for all the methods

## DataSet

We are using **Stanford's WebQuestions** which contains around 5800 natural-language question-answer pairs.
Here is the Source: [Hugging Face Datasets](https://huggingface.co/datasets/stanfordnlp/web_questions)
We are using 80% data for training and 20% data for testing.

## Methods

Here are the methods that we are exploring:

1. **Fine-tuning**
   We are applying LoRA (Low-Rank Adaption) to Gemma-2B by injecting small, trainable rank-decomposition matrices into each
   transformer layer. These adapter weights are upadted which will drastically reduce compute and storage cost.
   We are using Hugging Face **'peft'** library to wrap Gemma-2B's attention and feed-forward modules with LoRA adapters.

2. **Knowledge-Graph**
   We are planning to integrate Wikidata Knowledge Graph by using SPARQL queries and entity linking.
   We will augment the finetuned model with the Wikidata Knowledge Graph and analyse the new results.

3. **Retrieval-Augmented Generation (To Be Decided)**

4. **Reinforcement Learning using Human Factor (Future Scope)**

## HalluLens

We will be using HalluLens : LLM Hallucination Benchmark, which is a comprehensive suite which will help us distinguish extrinsic
vs intrinsic hallucinations.

## Authors

1. Alejandro Danies-Lopez
2. Benjamin Klassen
3. Gaurang Kamat
4. Jigyan (Joy) Xu

## References:

1. SM Tonmoy, SM Zaman, Vinija Jain, Anku Rani, Vipula Rawte, Aman Chadha, and Amitava Das, “A comprehensive survey of hallucination mitigation techniques
   in large language models,” arXiv preprint arXiv:2401.01313, vol. 6, 2024.

2. Garima Agrawal, Tharindu Kumarage, Zeyad Alghamdi, and Huan Liu, “Can knowledge graphs reduce hallucinations in llms?: A survey,” arXiv preprint
   arXiv:2311.07914, 2023.

3. Gemma Team, Thomas Mesnard, Cassidy Hardin, Robert Dadashi, Surya Bhupatiraju, Shreya Pathak, Laurent Sifre, Morgane Rivi`ere, Mihir Sanjay Kale, Juliette Love,
   et al., “Gemma: Open models based on gemini research and technology,” arXiv preprint arXiv:2403.08295, 2024.

4. Muchen Huan and Jianhong Shun, “Fine-tuning transformers efficiently: A survey on lora and its impact,” 2025.

5. Yejin Bang, Ziwei Ji, Alan Schelten, Anthony Hartshorn, Tara Fowler, Cheng Zhang, Nicola Cancedda, and Pascale Fung, “Hallulens: Llm hallucination benchmark,” 2025.

6. Long Ouyang, Jeffrey Wu, Xu Jiang, Diogo Almeida, Carroll Wainwright, Pamela Mishkin, Chong Zhang, Sandhini Agarwal, Katarina Slama, Alex Ray, et al.,
   “Training language models to follow instructions with human feedback,” Advances in neural information processing systems, vol. 35, pp. 27730–27744, 2022.

7. Patrick Lewis, Ethan Perez, Aleksandra Piktus, Fabio Petroni, Vladimir Karpukhin, Naman Goyal, Heinrich K¨uttler, Mike Lewis, Wen-tau Yih, Tim Rockt¨aschel, et al.,
   “Retrieval-augmented generation for knowledge intensive nlp tasks,” Advances in neural information processing systems, vol. 33, pp. 9459–9474, 2020.
