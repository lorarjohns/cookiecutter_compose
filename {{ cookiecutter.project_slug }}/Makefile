# Thanks to https://gist.github.com/mpneuried/0594963ad38e68917ef189b4e6a269db
# import config.
# You can change the default config with `make cnf="config_special.env" build`
# cnf ?= config.env
# include $(cnf)
# export $(shell sed 's/=.*//' $(cnf))

.PHONY: help

# HELP
# This will output the help for each task
# thanks to https://marmelab.com/blog/2016/02/29/auto-documented-makefile.html

help: ## This help.
	@grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}' # pipe sort before awk to sort commands
.DEFAULT_GOAL := help

###########################################################################################################
## SCRIPTS
###########################################################################################################


###########################################################################################################
## VARIABLES
###########################################################################################################

# export PROJECT_NAME={{ cookiecutter.project_slug }}
export PYTHON=python3

###########################################################################################################
## ADD TARGETS SPECIFIC TO "{{ cookiecutter.project_slug }}"
###########################################################################################################


###########################################################################################################
## GENERAL TARGETS
###########################################################################################################


# DOCKER COMMANDS

# Some general ideas borrowed from:
# https://medium.com/applied-data-science/the-full-stack-data-scientist-part-2-a-practical-introduction-to-docker-1ea932c89b57

build: ## Create the two images
	docker-compose build 

up: ## Spin up the containers
	docker-compose up -d
	
bash: ## Load a bash shell inside the app container
	docker-compose exec app bash
	
jupyter-notebook: ## start a Jupyter Notebook server
	jupyter-notebook --ip=0.0.0.0 --allow-root # --no-browser

stop: ## Stop running containers
	docker-compose stop

clean: ## Clean the generated/compiles files
	echo "nothing clean ..."

#  TESTING COMMANDS

test: ## run test cases in tests directory
	$(PYTHON) -m unittest discover

## black: ## format code with black

lint: ## check style with flake8
	flake8 cookie


clean-pyc: ## remove Python file artifacts
	find . -name '*.pyc' -exec rm -f {} +
	find . -name '*.pyo' -exec rm -f {} +
	find . -name '*~' -exec rm -f {} +
	find . -name '__pycache__' -exec rm -fr {} +
