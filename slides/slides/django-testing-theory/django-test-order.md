## Order of tests

Django reorders discovered tests as follows:

<br>

1. All `TestCase` subclasses
2. Any other Django based tests
3. Any other pure `unittest.TestCase` tests

<br>

This ensures all (transactional) `TestCase` tests always run with a clean database.
