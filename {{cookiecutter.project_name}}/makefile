#!/usr/bin/env bash
CODE = {{cookiecutter.project_slug}}

init:
	pipenv install --dev

test:
	pipenv run pytest -vv --cov=$(CODE) $(args)

lint:
	pipenv run flake8 --jobs 4 --statistics $(CODE) tests
	pipenv run pylint --jobs 4 --rcfile=setup.cfg $(CODE)
	pipenv run black --py36 --line-length=100 -S --check $(CODE) tests

pretty:
	pipenv run isort --apply --recursive $(CODE) tests
	pipenv run black --py36 --line-length=100 -S $(CODE) tests

precommit_install:
	echo '#!/bin/sh\nmake lint test\n' > .git/hooks/pre-commit
	chmod +x .git/hooks/pre-commit
