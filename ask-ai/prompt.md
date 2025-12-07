# Ask Claude - Dec 07th, 2025

Consider the following two examples of AI usage.

A user - Daniel - records a one hour audio note on his computer. It contains some notes for an essay.

It's dictation. But the format isn't exceptionally polished. After all, Daniel is speaking off the cuff. 

If he wants to leveraged AI to expedite the process of converting this information into a first draft from which he can begin editing, he has a few options. Each workflow is distinct, technically. 

(START EXAMPLES)

A:

Daniel uses Whisper or some other ASR model in order to get a transcript. 

The raw transcripts of Daniel's speech, however, contains a lot of extraneous data: filler words, pauses for thoughts, instructions like "scratch that ... keep this."

ASR models, at least those which lack innate punctuation restoration logic, will return this as a long string of text. 

The raw text the model reutns might read something like: "ASR is a really .. ehm ... fascinating part of the AI picture that .... has taken a while to ... gain traction ... no, popularity."

Daniel would like the transcript to just read "ASR is a really fascinating part of the AI picture that has taken a while to gain popularity." But an ASR model is not trained to edit text, merely to return it faithfully.

B: 

Daniel uses Whisper to gain the initial transcript. 

Then he uses a large language model with his system prompt, instructing it to clean the text up for better intelligibility. 

A common pairing might be Whisper + GPT 4o.

Through this combination, Daniel can achieve a text that is much closer to what he wished to dictate. The original text can be maintained or treated as throwaway data.

C:

Daniel uses a multimodal model with audio understanding - like Gemini 2.5.

He sends one API call which:

- Uploads the audio binary data for processing 
- Includes a prompt 

Daniel uses the prompt in order to provide the instructions that the model should use to return the text in the desired format. 

In this manner, Daniel achieves workflow B with one single API call. 

(END EXAMPLES)

Your task is to define the nomenclature. 

Consider that AI is a fast evolving field. 

Consider also that vendor descriptions may not always correlate with those used by researchers. Consider finally that the same idea or workflow might be known by different terms in different parts of the world. 

With that in mind

- Provide 5 names for each workflow. The name should be an accurate desciptor
- Provide examples of models that support this workflow, or combinations of them. 
- Suggest benchmarks for each of these modalities. 
- Identify the pros and cons of each of these approaches on the differences that they make towards the ultimate transcription generated. 
- "Multimodal ASR will make traditional STT redundant. " Do you agree with this statement? Provide your reasoning

Complete the task by generating a individual Markdown document answering each of these questions. 

Save each of them here: 

/home/daniel/repos/github/Open-Source-Audio-Multimodals/ask-ai