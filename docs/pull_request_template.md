from selenium import webdriver
from selenium.webdriver.common.by import By


class ValidUserLogin:
     
     url = 'http://demostore.supersqa.com/'
     valid_email = abc123@gmail.com
     valid_password = password!1
     logout_btn_css = 'li.woocommerce-MyAccount-navigation-link--customer-logout a'
     
     def __init__(self):
          self.driver = webdriver.Chrome()
          self.driver.implecitly_wait(10)
     
     def go_to_my_url(self):
          self.driver.get(self.url)
          
     def input_email(self):
          field = self.driver.find_element(By.ID, 'username')
          field.send_keys(self.valid_email)
     
     def input_password(self):
          field = self.driver.find_element(By.ID, 'password')
          field.send_keys(self.valid_password)
     
     def click_login(self):
          self.driver.find_element(By.NAME, 'login').click()
                
     def verify_succesfull_login(self):
          logout_btn = self.driver.find_element(By.CSS_SELECTOR, logout_btn_css)
          
     if logout_btn.is_displayed():
          print ('PASS')
     else: 
        raise Exception ('User is not logged in')
        
     def main(self):
          self.go_to_my_url()
          self.input_email()
          self.input_password()
          self.click_login()
          self.verify_succesfull_login()
          self.driver.quit()
     
if __name__ =='__main__':
    obj = ValidUserLogin()
    obj.main()
     
