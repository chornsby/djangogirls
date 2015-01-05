## Testing POST requests

<br>

    def test_superuser_can_add_new_blog_post(self):
        title = 'Awesome Title 2'
        text = 'Here is lots of post content... blah blah blah...'

        response = self.client.post(reverse('post_new'), {
            'title': title,
            'text': text,
        }, follow=True)

        post = Post.objects.get(title=title)

        self.assertRedirects(response, reverse('post_detail', kwargs={'pk': post.pk}))
        self.assertContains(response, title)
