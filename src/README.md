## LLM OS

This repo contains the code for running the LLM OS in `dev` and `prd`:

1. `dev`: A development environment running locally on docker
2. `prd`: A production environment running on AWS ECS

## Setup Workspace

1. Clone the git repo

> from the `llm-os` dir:

2. Create + activate a virtual env:

```sh
python3 -m venv aienv
source aienv/bin/activate
```

3. Install `phidata`:

```sh
pip install 'phidata[aws]'
```

4. Setup workspace:

```sh
phi ws setup
```

5. Copy `workspace/example_secrets` to `workspace/secrets`:

```sh
cp -r workspace/example_secrets workspace/secrets
```

6. Optional: Create `.env` file:

```sh
cp example.env .env
```

## Run LLM OS locally

1. Install [docker desktop](https://www.docker.com/products/docker-desktop)

2. Export credentials

We use gpt-4o as the LLM, so export your OpenAI API Key

```sh
export OPENAI_API_KEY=sk-***
```

- To use Exa for research, export your EXA_API_KEY (get it from [here](https://dashboard.exa.ai/api-keys))

```shell
export EXA_API_KEY=xxx
```

**OR** set them in the `.env` file

3. Start the workspace using:

```sh
phi ws up
```

- Open [localhost:8501](http://localhost:8501) to view the Streamlit App.
- If FastApi is enabled, Open [localhost:8000/docs](http://localhost:8000/docs) to view the FastApi docs.

4. Stop the workspace using:

```sh
phi ws down
```
