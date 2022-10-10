# AssemblyAI CLI

[![Ghost Status](https://img.shields.io/badge/Homebrew-FBB040.svg?style=for-the-badge&logo=Homebrew&logoColor=black)](https://assemblyai.com)

A quick and easy way to test assemblyAI's transcription features on your terminal

## Installation

To install AssemblyAI CLI, use any of the following methods:

- ### Homebrew (macOS only)

  For macOS users, you can install via:

    ``` bash
    brew tap assemblyai/assemblyai
    brew install assemblyai
    ```

- ### Curl
  
  - Linux or macOS:
    Paste that in a Terminal or shell prompt.

      ``` bash
      /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/AssemblyAI/assemblyai-cli/main/install.sh)"
      ```

  - Windows Powershell:
    Paste that in a Terminal or shell prompt.

      ``` PowerShell
      Set-ExecutionPolicy RemoteSigned -Scope CurrentUser # Needed to run a remote script the first time
      iex "$(curl https://raw.githubusercontent.com/AssemblyAI/assemblyai-cli/main/install.ps1)"
      Set-Alias -Name assemblyai -Value C:\\'./Program Files\'/AssemblyAI/assemblyai.exe # Needed to add the alias of the command
      ```

## Commands

- `config`: Use the config command to store your authentication token and automatically use it in any subsequent request.
Ex:

  ``` bash
  assemblyai config <token>
  ```

- `transcribe`: Runs the transcription of a local or URL file with all the features specified by the flags.
  Ex:

  ``` bash
  assemblyai transcribe <path | url | youtube url> [flags]
  ```

- `get`: Retrieves a previously transcribed file.
  Ex:

  ``` bash
  assemblyai get <transcription id> [flags]
  ```

## Flags

| Name | Abbreviation | Default | Description |
 |--|--|--|--|
|poll|p|true|The CLI will poll the transcription every 3 seconds until it's complete.|
|speaker_labels|l|true|Automatically detect the number of speakers in the file.|
|punctuate|u|true|Enable automatic punctuation|
|format_text|f|true|Enable text formatting|
|dual_channel|d|false|Enable dual channel|
|json|j|false|If true, the CLI will output the JSON. |
|redact_pii|r|false|Remove personally identifiable information from the transcription.|
|redact_pii_policies*|i|drug,number_sequence,person_name*|The list of PII policies to redact (source), comma-separated. Required if the redact_pii flag is true, with the default value including drugs, number sequences, and person names. |
|auto_highlights|a|false|Automatically detect important phrases and words in the text.|
|content_moderation|c|false|Detect if sensitive content is spoken in the file.|
|topic_detection|t|false|Label the topics that are spoken in the file.|
|sentiment_analysis|x|false|Detect the sentiment of each sentence of speech spoken in the file.|
|auto_chapters|s|false|A "summary over time" for the audio file transcribed.|
|entity_detection|e|false|Identify a wide range of entities that are spoken in the audio file.|
