# OOP Calculator

- **Behavior:** Run with `python -m calculator`. A successful session can run `add` with `10` and `5` to get `15`; entering `hello` as a number shows an error and returns to the prompt, where another calculation can succeed.
- **OOP:** `Add(10, 5)` stores operands `10` and `5` and returns `15`. Abstract `Calculation` defines the shared interface; `Add` and `Subtract` can substitute for it. Each `History` owns its list and returns a copy of that list from `get_history()`.
- **Testing:** `assert Add(10, 5).get_result() == 15` claims the result is `15`. `test_invalid_removal_preserves_entries` checks the missing path: removing index `99` raises `IndexError` and leaves history unchanged.
- **Workflow:** Set up with `python3 -m venv .venv`, `source .venv/bin/activate`, `python -m pip install pytest`, then run `python -m pytest`. The reported CI-style error, `unrecognized arguments: --cov=...`, means coverage flags were configured without the `pytest-cov` plugin; those flags were removed from `pytest.ini`.
- **Transfer:** To add multiplication, implement `Multiply(Calculation)` in `calculator/calculation.py` and register `"multiply": Multiply` in the CLI's `operations` mapping. History needs no changes because it accepts any `Calculation` subclass.
