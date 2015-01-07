## Testing with a Real Browser is also possible

<br>

    from django.test import LiveServerTestCase
    from selenium.webdriver.firefox.webdriver import WebDriver


    class SeleniumTestCase(LiveServerTestCase):
        def test_browse_to_page(self):
            # Browse to the login page
            self.selenium.get(self.build_absolute_url('/admin/login/?next=/'))

            # Fill out input
            username_input = self.selenium.find_element_by_name("username")
            username_input.send_keys('admin')
            password_input = self.selenium.find_element_by_name("password")
            password_input.send_keys('secretpassword')

            # Log in
            self.selenium.find_element_by_xpath('//input[@value="Log in"]').click()