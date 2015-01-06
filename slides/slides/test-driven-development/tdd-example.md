## TDD example

So we have a blog app, but it's missing blog publishing functionality, which is bad, so we will add it now.

We could just write the code for it, but instead **we will write a test for it**.

```python
class SuperUserTestCase(TestCase):
    def test_superuser_can_publish_blog_post(self):
        response = self.client.post(
            reverse("post_publish", kwargs={"pk": self.post.pk}))
        self.assertRedirects(
            response, reverse("post_detail", kwargs={"pk": self.post.pk}))
        post = Post.objects.get(id=self.post.pk)
        self.assertIsNotNone(post.published_date)
```

<small>
<p>Note 1: if this was a live server test case, we could browse to the post and click the button. While that is fine, the publish view can be separately and individually tested by directly posting to it.</p>
<p>Note 2: Of course our class should have a `setUp` which creates a user, an (unpublished) blog post, and logs the user in.</p>
</small>
