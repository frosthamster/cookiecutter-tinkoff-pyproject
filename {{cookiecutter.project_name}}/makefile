BIN = .venv/bin/
CODE = {{cookiecutter.project_slug}}

init:
	python3 -m venv .venv
	$(BIN)pip install -r requirements.txt

test:
	$(BIN)pytest -vv --cov=$(CODE) $(args)

lint:
	$(BIN)flake8 --jobs 4 --statistics $(CODE) tests
	$(BIN)pylint --jobs 4 --rcfile=setup.cfg $(CODE)
	$(BIN)black --py36 --line-length=79 --check $(CODE) tests

pretty:
	$(BIN)isort --apply --recursive $(CODE) tests
	$(BIN)black --py36 --line-length=79 $(CODE) tests

precommit_install:
	echo '#!/bin/sh\nmake lint test\n' > .git/hooks/pre-commit
	chmod +x .git/hooks/pre-commit