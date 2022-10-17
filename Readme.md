# Example to test python packaging

In particular the objective is to clarify how to get editable install working with setuptools and the VS Code tool set

* Build wheel and test wheel content
```
py -3.10 -m venv venv
.\venv\Scripts\Activate.ps1
python -m pip  install -U pip build
python -m build --wheel

7z l .\dist\packaging_example-0.0.1-py3-none-any.whl
```

* Editable install, this works for
    * src layout and flat layout with setuptools==63.4.3
    * src layout with with setuptools==66.5
```
pip install -e .[dev]
```

* Editable install, this works for
    * flat layout with with setuptools==66.5
    * info here: https://github.com/microsoft/pylance-release/blob/main/TROUBLESHOOTING.md#editable-install-modules-not-found
```
pip install -e .[dev] --config-settings editable_mode=compat
```