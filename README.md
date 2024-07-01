# Claude Sonnet 3.5 OS (by Phidata)

This repo contains the code for running the Anthropic Claude Operating System

Inspired by Andrej Karpathy [in this tweet](https://twitter.com/karpathy/status/1723140519554105733), [this tweet](https://twitter.com/karpathy/status/1707437820045062561) and [this video](https://youtu.be/zjkBMFhNj_g?t=2535).


## Running Claude OS:

> Note: Fork and clone this repository if needed

### 1. Create a virtual environment

```shell
python3 -m venv ~/.venvs/aienv
source ~/.venvs/aienv/bin/activate
```

### 2. Install libraries

```shell
pip install -r requirements.txt
```

### 3. Export credentials

- Our implementation uses Claude Sonnet 3.5, so export your Anthropic API Key

```shell
export ANTHROPIC_API_KEY=***
```

- To use Exa for research, export your EXA_API_KEY (get it from [here](https://dashboard.exa.ai/api-keys))

```shell
export EXA_API_KEY=xxx
```

- To use VoyageAI for embeddings, export your VOYAGE_API_KEY (get it from [here](https://dash.voyageai.com/api-keys))

```shell
export VOYAGE_API_KEY=xxx
```

### 4. Run PgVector

We use PgVector to provide long-term memory and knowledge to the Clause OS.
Please install [docker desktop](https://docs.docker.com/desktop/install/mac-install/) and run PgVector using either the helper script or the `docker run` command.

- Run using a helper script

```shell
./run_pgvector.sh
```

- OR run using the docker run command

```shell
docker run -d \
  -e POSTGRES_DB=ai \
  -e POSTGRES_USER=ai \
  -e POSTGRES_PASSWORD=ai \
  -e PGDATA=/var/lib/postgresql/data/pgdata \
  -v pgvolume:/var/lib/postgresql/data \
  -p 5532:5432 \
  --name pgvector \
  phidata/pgvector:16
```

 - On Windows

```powershell
docker run -d `
  -e POSTGRES_DB=ai `
  -e POSTGRES_USER=ai `
  -e POSTGRES_PASSWORD=ai `
  -e PGDATA=/var/lib/postgresql/data/pgdata `
  -v pgvolume:/var/lib/postgresql/data `
  -p 5532:5432 `
  --name pgvector `
  phidata/pgvector:16
```

### 5. Run the Claude OS App

```shell
streamlit run app.py
```

- Open [localhost:8501](http://localhost:8501) to view Claude OS.
- Add a news post to knowledge base: https://www.anthropic.com/news/claude-3-5-sonnet
- Ask: What is Claude 3.5 Sonnet?
- Web search: Whats happening in france?
- Calculator: Whats 10!
- Enable shell tools and ask: is docker running?
- Enable the Research Assistant and ask: write a report on the ibm hashicorp acquisition
- Enable the Investment Assistant and ask: shall i invest in nvda?

### 6. Message on [discord](https://discord.gg/4MtYHHrgA8) if you have any questions

### 7. Star ⭐️ the project if you like it.
