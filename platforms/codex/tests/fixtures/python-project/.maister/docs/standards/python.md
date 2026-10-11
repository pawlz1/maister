# Python standards

- Every newly added public function must have a docstring containing the phrase
  `MAISTER_STANDARD_SENTINEL` and an annotated return type.
- Use the standard library only.
- Regression tests use unittest and run with `python3 -m unittest discover -s tests -v`.
- Preserve existing unrelated behavior and tests.