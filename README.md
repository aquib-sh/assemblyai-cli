# AssemblyAI CLI

![Release](https://img.shields.io/github/v/release/assemblyai/assemblyai-cli)
![Build](https://img.shields.io/github/workflow/status/assemblyai/assemblyai-cli/Release%20workflow)
![License](https://img.shields.io/github/license/assemblyai/assemblyai-cli)

The AssemblyAI CLI helps you quickly test our latest AI models right from your terminal, with minimal installation required.

![Thumbnail](./assets/thumbnail.png)

## Installation

The CLI is simple to install, supports a wide range of operating systems like macOS, Windows, and Linux, and makes it more seamless to build with AssemblyAI.

### Homebrew

If you're on macOS, you can install it using Homebrew:

```bash
brew tap assemblyai/assemblyai
brew install assemblyai
```

### macOS or Linux

If you don't have Homebrew installed, or are running Linux:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/AssemblyAI/assemblyai-cli/main/install.sh)" &&

case "$SHELL" in
    *bash*)
        if [ -f "$HOME/.bashrc" ]; then
            # if the shell contains "bash" and .bashrc is present
            source $HOME/.bashrc
        fi
        ;;
    *zsh*)
        if [ -f "$HOME/.zshrc" ]; then
            # if the shell contains "zsh" and .zshrc is present
            source $HOME/.zshrc
        fi
        ;;
    *)
        echo "Unknown shell or required configuration file not found."
        ;;
esac
```

### Windows

The CLI is available on Windows either via Scoop or by script. 

Via Scoop:

```powershell
scoop bucket add assemblyai https://github.com/assemblyai/scoop-assemblyai.git
scoop install assemblyai
````

Or via PowerShell as an administrator:

```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
irm https://raw.githubusercontent.com/AssemblyAI/assemblyai-cli/main/install.ps1 | iex
New-Alias -Name assemblyai -Value $Env:Programfiles/AssemblyAI/assemblyai.exe
```

## Getting started

Get started by configuring the CLI with your AssemblyAI token. If you don't yet have an account, create one [here](https://app.assemblyai.com/).

```bash
assemblyai config [token]
```

This command will validate your account, and store your token safely in `~/.config/assemblyai/config.toml` later to be used when transcribing files.

You can now transcribe local files, remote URLs, or YouTube videos.

```bash
assemblyai transcribe https://youtu.be/0wvBu014E5o --auto_highlights --entity_detection
```

## Usage

Installing the CLI provides access to the `assemblyai` command:

```bash
assemblyai [command] [--flags]
```

## Commands

### Transcribe

With the CLI, you can transcribe local files, remote URLs, and YouTube links.

```bash
assemblyai transcribe [local file | remote url | youtube links] [--flags]
```

<details>
  <summary>Flags</summary>
  
  > **-j, --json**  
  > default: false  
  > example: `-j` or `--json`  
  > If true, the CLI will output the JSON.

> **-p, --poll**  
> default: true  
> example: `-p` or `--poll`  
> The CLI will poll the transcription every 3 seconds until it's complete.

> **-s, --auto_chapters**  
> default: false  
> example: `-s` or `--auto_chapters`  
> A "summary over time" for the audio file transcribed.

> **-a, --auto_highlights**  
> default: false  
> example: `-a` or `--auto_highlights`  
> Automatically detect important phrases and words in the text.

> **-c, --content_moderation**  
> default: false  
> example: `-c` or `--content_moderation`  
> Detect if sensitive content is spoken in the file.

> **-d, --dual_channel**  
> default: false  
> example: `-d` or `--dual_channel`  
> Enable dual channel

> **-D, --disfluencies**  
> default: false  
> example: `-D` or `--disfluencies`  
> Include Filler Words in your transcript

> **-e, --entity_detection**  
> default: false  
> example: `-e` or `--entity_detection`  
> Identify a wide range of entities that are spoken in the audio file.

> **-f, --format_text**  
> default: true  
> example: `-f=false` or `--format_text=false`  
> Enable text formatting

> **-u, --punctuate**  
> default: true  
> example: `-u=false` or `--punctuate=false`  
> Enable automatic punctuation

> **-r, --redact_pii**  
> default: false  
> example: `-r` or `--redact_pii`  
> Remove personally identifiable information from the transcription.

> **-i, --redact_pii_policies**  
> default: drug,number_sequence,person_name  
> example: `-i medical_process,nationality` or `--redact_pii_policies medical_process,nationality`  
> The list of PII policies to redact ([source](https://www.assemblyai.com/docs/Models/pii_redaction)), comma-separated. Required if the redact_pii flag is true.

> **-x, --sentiment_analysis**  
> default: false  
> example: `-x` or `--sentiment_analysis`  
> Detect the sentiment of each sentence of speech spoken in the file.

> **-l, --speaker_labels**  
> default: true  
> example: `-l=false` or `--speaker_labels=false`  
> Automatically detect the number of speakers in the file.

> **-t, --topic_detection**  
> default: false  
> example: `-t` or `--topic_detection`  
> Label the topics that are spoken in the file.

> **-w, --webhook_url**  
> example: `--webhook_url "https://example.com/"`  
> Receive a webhook once your transcript is complete.

> **-b, --webhook_auth_header_name**  
> example: `--webhook_auth_header_name "Authorization"`  
> Containing the header's name which will be inserted into the webhook request.

> **-o, --webhook_auth_header_value**  
> example: `--webhook_auth_header_value "foo:bar"`  
> Receive a webhook once your transcript is complete.

> **-n, --language_detection**  
> default: false  
> example: `-n` or `--language_detection`  
> Automatic identify the dominant language that’s spoken in an audio file.
> [Here](https://www.assemblyai.com/docs/Models/speech_recognition#automatic-language-detection) you can view the ALD list for supported languages

> **-g, --language_code**  
> example: `-g es` or `--language_code es`  
> Manually specify the language of the speech in your audio file.
> Click [here](https://www.assemblyai.com/docs/Concepts/faq#supported-languages) to view all the supported languages

> **-m, --summarization**  
> default: false  
> example: `-m` or `--summarization`  
> Generate a single abstractive summary of the entire audio.

> **-q, --summary_model**
> default: bullets  
> example: `-q conversational` or `--summary_model conversational`  
> Type of summary generated.
> Click [here](https://www.assemblyai.com/docs/Models/summarization) to view all the supported types

> **-y, --summary_type**
> default: bullets  
> example: `-y paragraph` or `--summary_type paragraph`  
> Model of summary generated.
> Click [here](https://www.assemblyai.com/docs/Models/summarization) to view all the supported types

> **-k, --word_boost**
> example: `-k "sally mcmanus,the IQEZ iPhone app"` or `--word_boost "sally mcmanus,the IQEZ iPhone app"`  
> Any term included will have its likelihood of being transcribed boosted.

> **-z, --boost_param**
> example: `-z high` or `--word_boost high`  
> Control how much weight should be applied to your boosted keywords/phrases. This value can be either low, default, or high.
> **--custom_spelling**
> example: `--custom_spelling "[{\"from\": [\"ariana\"], \"to\": \"Arianna\"}]"` or  `--custom_spelling ./custom_spelling.json`
> Specify how words are spelled or formatted in the transcript text.

> **--srt**  
> default: false  
> example: `--srt`  
> Create an SRT file named `[id].srt` in the current directory.

</details>

### Get

If you're not polling the transcription, you can fetch it later:

```bash
assemblyai get [id]
```

<details>
  <summary>Flags</summary>
  
  > **-j, --json**  
  > default: false  
  > example: `--json` or `--json=true`  
  > If true, the CLI will output the JSON.

> **-p, --poll**  
> default: true  
> example: `--poll=false`  
> The CLI will poll the transcription every 3 seconds until it's complete.

> **--srt**  
> default: false  
> example: `--srt`  
> Create an SRT file named `[id].srt` in the current directory.

</details>

### Exporting Output to a File

You can export the output of AssemblyAI CLI commands to a file by using [shell redirection](https://www.gnu.org/software/bash/manual/html_node/Redirections.html). To export the output to a text file, use the `>` operator followed by the name of the file you want to create.

```bash
assemblyai get [id] > transcript.txt
```

To save the raw JSON response from the API, you can do this instead:

```bash
assemblyai get [id] -j > transcript.json
```

Note that if the file you are exporting to already exists, its contents will be overwritten. If you want to append the output to an existing file, use the `>>` operator instead of `>`.

## Contributing

We're more than happy to welcome new contributors. If there's something you'd like to fix or improve, start by [creating an issue](https://github.com/AssemblyAI/assemblyai-cli/issues). Please make sure to follow our [code of conduct](https://github.com/AssemblyAI/assemblyai-cli/blob/main/CODE_OF_CONDUCT.md).

## Telemetry

The AssemblyAI CLI includes a telemetry feature that collects usage data and is enabled by default.

To opt out of telemetry, set the telemetry variable in the `config.toml` file to false.

## Upgrade

Our team regularly releases updates to ensure world-class service, so make sure to update your CLI when a new release is available. You can do so by running the same commands as shown on the [Installation](#installation) section, or, if you've installed using brew, run:

```bash
brew upgrade assemblyai
```

## Feedback

Please don't hesitate to [let us know what you think](https://forms.gle/oQgktMWyL7xStH2J8)!

## Uninstall

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/AssemblyAI/assemblyai-cli/main/uninstall.sh)"
```

We'd love to understand why you're uninstalling the CLI, and what we can do to improve it. Feel free to [reach out](https://forms.gle/oQgktMWyL7xStH2J8).

## License

Copyright (c) AssemblyAI. All rights reserved.

Licensed under the [Apache License 2.0 license](https://github.com/AssemblyAI/assemblyai-cli/blob/main/LICENSE).
