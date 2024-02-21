from selenium import webdriver
from selenium.webdriver.common.keys import Keys
import time

def join_google_meet(meeting_code):
    # Specify the path to your Chrome webdriver
    driver = webdriver.Chrome('/path/to/chromedriver')
    
    # Open Google Meet
    driver.get("https://meet.google.com/")
    time.sleep(3)  # Wait for the page to load
    
    # Find and click the "Join or start a meeting" button
    join_button = driver.find_element_by_xpath("//div[@class='CE3oLc']")
    join_button.click()
    time.sleep(2)  # Wait for the next page to load
    
    # Find and enter the meeting code
    code_input = driver.find_element_by_xpath("//input[@placeholder='Enter a code or link']")
    code_input.send_keys(meeting_code)
    code_input.send_keys(Keys.RETURN)
    
    # Wait for the meeting to join
    time.sleep(5)
    
    # Close the browser
    driver.quit()

if __name__ == "__main__":
    meeting_code = input("Enter the Google Meet code: ")
    join_google_meet(meeting_code)
    
