

## reading note of *Building effective agents*
> [Building Effective Agents](https://www.anthropic.com/engineering/building-effective-agents)
  
LLM(large language model) agents <- most successful is building with **simple, composable patterns**.  

### 1 What are agents?
**agents**: systems where LLMs dynamically direct their own processes and tool usage, maintaining control over how they accomplish tasks.  
**workflows**: systems where LLMs and tools are orchestrated through predefined code paths.  


-> agents can dynamically change and adopt. workflows just obey the settings.

### 2 when and when not to use agents
building applications with LLMs -> finding the simplest solution, **only increasing complexity when needed** (which means may not necessary to build a agentic systems, because agentic systems often trade latency and cost for better task performance -> consider tradeoff)  
-> workflows offer predictability and consistency for well-defined tasks  
-> agents offer fexibility and model-driven decision-making  


<ins> ? for many applications, optimizing single LLM calls[^1] with retrieval and in-context examples is usually enough </ins>

[^1]: call llm: 调用大模型

### 3 when and how to use frameworks
the frameworks can help agent implement:

- [Claude Agent SDK](https://code.claude.com/docs/en/agent-sdk/overview)
- [Strands Agents SDK by AWS](https://strandsagents.com/)
- [Rivet](https://rivet.ironcladapp.com/), a drag and drop GUI[^2] LLM workflow builder
- [Vellum](https://www.vellum.ai/), GUI tool for building and testing complex workflows

[^2]: GUI: Graphical user interfaces  

using these frameworks may add complexity (create extra abstraction layers) and harder to debug
suggest developers start by using LLM APIs directly, if you do use a framework, ensure you understand the underlying code.

<ins> ? learning LLM model </ins>


### 4 Building blocks, workflows, and agents
#### 4.1 Building block: The augmented LLM
the basic building block of agentic systems is an LLM enhanced with augmentations such as retrieval, tools, and memory.
<img width="792" height="412" alt="image" src="https://github.com/user-attachments/assets/71a5faf5-e298-4e68-a382-d877b87b8420" />

focusing on ① tailor these capabilities to your specific use case; ② ensure they provide an easy, well-documented interface for your LLM  

#### 4.2 Workflow: Prompt chaining
prompt chaining decomposes a task into a sequence of steps. each LLM call processes the output of the previous one.   
can add programmatic checks ('gate' in the diagram) on any intermediate steps to ensure the process is still on track
<img width="1230" height="506" alt="image" src="https://github.com/user-attachments/assets/8ef3f045-e582-4708-9879-3fbf27a513b4" />

↑ task can be easily and cleanly decomposed into fixed subtasks can use below workflow. -> main goal is to trade off latency for higher accuracy, by making each LLM call an easier task

#### 4.3 Workflow: Rounting
routing classifies an input and directs it to a specialized followup task.  
allows for separation of concerns, and building more specialized prompts.  
without this, optimizing for one kind of input can hurt performance on other inputs.
<img width="1137" height="588" alt="image" src="https://github.com/user-attachments/assets/f626e78c-6e34-4e88-9102-f266ad21c476" />

↑ complex tasks where there are distinct categories that are better handled separately, and where classification can be handled accurately, either by an LLM or a more traditional classification model/algorithm.  

e.g: directing different types of customer service queries into different downsteam processes, prompts, and tools.

#### 4.4 Workflow: Parallelization
LLM work simultaneously on a task and have their outputs aggregated programmatically.  
manifests in 2 key variations:
* sectioning: breaking a task into independent subtasks run in parallel.
* voting: running the same task multiple times to get diverse outputs.
<img width="1183" height="599" alt="image" src="https://github.com/user-attachments/assets/98a93466-620d-47c5-8d39-feeac5fccfc6" />





