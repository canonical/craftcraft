**********
Craftcraft
**********

Welcome to Craftcraft! We hope this document helps you get started. Before
contributing any code, please sign the `Canonical contributor licence
agreement`_.

Setting up a development environment
------------------------------------
We use a forking, feature-based workflow, so you should start by forking the
repository. Once you've done that, clone the project to your computer using git
clone's ``--recurse-submodules`` parameter. (See more on the `git submodules`_
documentation.)

Tooling
=======
The following tooling should be installed on your machine:

- Python 3.10
- tox_ version 4.4 or later
- ShellCheck_ (available via snap: ``snap install shellcheck``)
- ruff_ (available via snap: ``snap install ruff``)

Initial Setup
#############

After cloning the repository but before making any changes, it's worth ensuring
that the tests, linting and tools all run on your machine. Running ``tox`` with
no parameters will create the necessary virtual environments for linting and
testing and run those::

    tox

If you want to install the environments but not run the tests, you can run::

    tox --notest

If you'd like to run the tests with a newer version of Python, you can pass a
specific environment. You must have an appropriately versioned Python
interpreter installed. For example, to run with Python 3.10, run::

    tox -e test-py3.10

While the use of pre-commit_ is optional, it is highly encouraged, as it runs
automatic fixes for files when ``git commit`` is called, including code
formatting with ``black`` and ``ruff``.  The versions available in ``apt`` from
Debian 11 (bullseye), Ubuntu 22.04 (jammy) and newer are sufficient, but you can
also install the latest with ``pip install pre-commit``. Once you've installed
it, run ``pre-commit install`` in this git repository to install the pre-commit
hooks.

Tox environments and labels
###########################

We group tox environments with the following labels:

* ``format``: Runs all code formatters with auto-fixing
* ``type``: Runs all type checkers
* ``lint``: Runs all linters (including type checkers)
* ``unit-tests``: Runs unit tests in several supported Python versions
* ``integration-tests``: Run integration tests in several Python versions
* ``tests``: The union of ``unit-tests`` and ``integration-tests``

For each of these, you can see which environments will be run with ``tox list``.
For example::

    tox list -m lint

You can also see all the environments by simply running ``tox list``

Running ``tox run -m format`` and ``tox run -m lint`` before committing code is
recommended.

Code Style
==========

Commits
#######

Format your commits following the conventional_ commit style.

Optionally, use the parens to scope to a particular component where
applicable.

See below for some examples of commit headings::

    feat: inherit context from services
    test: increase unit test stability
    fix: check foo before running bar
    feat(daemon): foo the bar correctly in the baz
    test(daemon): ensure the foo bars correctly in the baz
    fix(test): mock class Foo
    ci(snap): upload the snap artefacts to Github
    chore(deps): update go.mod dependencies


Recommended prefixes are: ``fix:``, ``feat:``, ``build:``, ``chore:``, ``ci:``,
``docs:``, ``style:``, ``refactor:``, ``perf:`` and ``test:``


.. _Black: https://black.readthedocs.io
.. _`Canonical contributor licence agreement`: http://www.ubuntu.com/legal/contributors/
.. _deadsnakes: https://launchpad.net/~deadsnakes/+archive/ubuntu/ppa
.. _`git submodules`: https://git-scm.com/book/en/v2/Git-Tools-Submodules#_cloning_submodules
.. _pre-commit: https://pre-commit.com/
.. _pyproject.toml: ./pyproject.toml
.. _pytest: https://pytest.org
.. _ruff: https://github.com/charliermarsh/ruff
.. _ShellCheck: https://www.shellcheck.net/
.. _tox: https://tox.wiki
.. _conventional: https://www.conventionalcommits.org/en/v1.0.0/#summary
