# is it possible to create a team with CrewAI AND Autogen ?

- crewAi https://docs.crewai.com/how-to/Creating-a-Crew-and-kick-it-off/#introduction
- autogen https://microsoft.github.io/autogen/
- with ollama backend https://ollama.com/download

# backend
 ## ollama sound long time response
- install ollama

```bash
ollama run openhermes
```

## igora protocol
- https://scenaristeur.github.io/igora/



# virtual environment

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

# fix crewai for igora

- https://github.com/joaomdmoura/crewAI/issues/202#issuecomment-2016921916

replace in .venv/lib/python3.10/site-packages/crewai/agentt.py:line 280 
```python
self.agent_executor = CrewAgentExecutor(
            agent=RunnableAgent(runnable=inner_agent), **executor_args
)
```
by
```python

self.agent_executor = CrewAgentExecutor(
            agent=RunnableAgent(runnable=inner_agent, stream_runnable=False), **executor_args
)
```

# test basic agents

```bash
python crewai_basic.py
```

```bash
python autogen_basic.py
```
