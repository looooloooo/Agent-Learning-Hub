

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



