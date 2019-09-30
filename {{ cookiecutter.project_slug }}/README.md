# {{ cookiecutter.project_name }}

This cookiecutter package enables you to generate a Python 3 data science project template 
from the command line, with an eye toward creating virtual environments for NLP projects.
Just define your project parameters from the command line:

```
{
	
	"project_name": "codebase_semantic_search",
    "project_slug": "python_code",
    "author_name": "lrj",
    "docker_username": "lorarjohns",
    "docker_password": "password",
    "repo_name": "lorarjohns/python_code",
    "jupyter_host_port": "8888"
}
```

Unless you suppress it with --no-input, you'll be asked for an input:

- Prompts are the keys in cookiecutter.json.
- Default responses are the values in cookiecutter.json.
- Prompts are shown in order.

The docker-compose file is structured to persist the files that you create on the virtual
machine to your physical drives.

## Requirements

* [Docker version 17 or later](https://docs.docker.com/install/#support)
* [Python 3](https://www.python.org)
* [make](https://www.gnu.org/software/make/)
* [cookiecutter](https://cookiecutter.readthedocs.io/en/latest/installation.html)

## Set up development environment

Make sure you have [cookiecutter](https://github.com/cookiecutter/cookiecutter) installed.

Navigate to the directory where you want to create your files. Initiate a local project by executing

```
cookiecutter https://github.com/lorarjohns/cookiecutter_compose.git
```

at the command line.

## Development with Docker container

After you've created the project, cd into the new directory and run

```
make
```

to see the available commands. Run any given command by executing:

```
make <command>
```

The key components are the **docker compose** file and the **Dockerfile**.
Together, they provide a basic development environment for manipulating data in Python.
Several tools and libraries in the **requirements.txt** file are particularly suited to small- 
or medium-scale natural-language processing projects:

- spaCy (including the pre-trained English models)
- nltk
- gensim
- sumy
- textacy
- pyLDAvis
 
To run the Docker container, execute:

1. make build
2. make up


You can view running containers via

```
docker container ps
```
To access a bash shell within the container, execute:

```
make bash
```

### Use Jupyter Notebook

To access a Jupyter notebook, run:

```
jupyter notebook --ip 0.0.0.0 --no-browser --allow-root
```

and copy the URL provided into your browser of choice. (This method is the one I prefer, at least.)

### Stopping containers

To stop the running container, execute:

```
make stop
```

### Edit source code

This project is a work in progress; bugs are sure to pop up and the current framework is meant to be vanilla, for the end user to customise.
That said, I'll be adding options and fleshing out functionality for more machine learning tasks,
optimizing caching, speed, and error handling (requirements.txt is currently brittle), fixing the tests, and integrating Travis.








# Credits

This package was created with [Cookiecutter](https://github.com/audreyr/cookiecutter) and the [cookiecutter-docker-science](https://docker-science.github.io/) project template.

References:

[Medium](https://medium.com/applied-data-science/the-full-stack-data-scientist-part-2-a-practical-introduction-to-docker-1ea932c89b57)
[GitHub](https://github.com/chrisgschon/docker-for-ds/blob/master/app/Dockerfile)