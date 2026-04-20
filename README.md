
```bash
  ╭─╮╭─╴╭─╮╭─╴╭─╴╭╮╷╶┬╴
  ╰─╮├╴ ├─┤│╶╮├╴ │╰┤ │ 
  ╰─╯╵  ╵ ╵╰─╯╰─╴╵ ╵ ╵
```

### What is it?

A lightweight, hand crafted, artisanal, computer-use agent written in Python. The agent can create, read, and edit files, fetch web pages and search the internet using the Brave search API, can execute arbitrary system commands and can load and create skills for itself.

### How to Run

> **Windows Specific:**
  EXEC command execution requires WSL (Windows Subsystem for Linux) to be installed, see [here](https://learn.microsoft.com/en-us/windows/wsl/install) for instructions on how to install it.

Clone the repo from github details below
```
git clone https://github.com/Yalond/SFAgent.git
cd SFAgent
```
Install the requirements detailed int he requirements.txt
```bash
pip install -r requirements.txt
```

Next, set the following environmental variables in the terminal, or add them into a .env file:

```
#llama.cpp example
CHAT_ENDPOINT=http://127.0.0.1:8080/v1/chat/completions

# Openrouter example
CHAT_ENDPOINT=https://openrouter.ai/api/v1/chat/completions
CHAT_API_KEY=<openrouter key>
MODEL=nvidia/nemotron-3-super-120b-a12b:free

BRAVE_SEARCH_API_KEY=<search key>
```
To run the agent:
```
python Agent.py
```
Optional command line arguments:
```
  -h, --help           show this help message and exit
  --skilldir SKILLDIR  Specify the skill folder, default is the currentdir/Skills
  --debug              Print debug messages
```

This agent supports the /v1/chat/completions openai compatible endpoint only, so you should be able to get it to run with llama.cpp or openrouter easily.

### A Note on Security

This agent is more of **a proof of concept**, it does have some security features built in to it, such as surfacing every exec command and asking you to confirm if you want to run them or not, but it's not designed for security. So **only run** this agent in a test environment such as a VM or dedicated PC.

An additional issue to be aware of is that this agent can **overwrite any file** the user it's running under has access to, without prompting you that it's going to do that. This is by design, but is another reason why you should only run it in a vm or dedicated computer.

This project is really set up as just a reference implementation for a simple agent for myself. I may rewrite this project in typescript or rust or haskell in the future.