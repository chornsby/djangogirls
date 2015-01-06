## Running tests

<br>

Running all the tests
```bash
python manage.py test
```


Running a single app

```bash
python manage.py test blog
```

Running a single test case

```bash
python manage.py test blog.tests.BlogPostViewTestCase
```


Running a single test in a test case

```bash
python manage.py test blog.tests.BlogPostViewTestCase.test_view_renders
```


Running all tests under a path

```bash
python manage.py test blog/
```

