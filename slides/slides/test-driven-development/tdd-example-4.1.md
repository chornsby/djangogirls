### TDD example - model test

Unless our model already has a method to do the actual publishing of the blog post, we should add a test for that too.

Even though this will be covered by the view test, it's good to test each individual method separately, especially ones with important functionality.

```python
class PostTestCase(TestCase):
    def test_post_can_be_published(self):
        self.post.publish()
        post = Post.objects.get(id=self.post.pk)
        self.assertIsNotNone(post.published_date)
```
