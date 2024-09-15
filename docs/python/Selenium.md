```python
from selenium import webdriver  
from selenium.webdriver.common.by import By  
from selenium.webdriver.common.keys import Keys  
  
chrome_options = webdriver.ChromeOptions()  
chrome_options.add_experimental_option("detach", True)  
  
driver = webdriver.Chrome(options=chrome_options)  
driver.get("https://secure-retreat-92358.herokuapp.com/")  
  
# captcha = WebDriverWait(driver, 10).until(EC.presence_of_element_located((By.LINK_TEXT, "Try different image")))  
# captcha.click()  
  
# WebDriverWait(driver, 10).until(EC.presence_of_element_located((By.CLASS_NAME, "menu")))  
# article_number = driver.find_element(By.XPATH, value='//*[@id="articlecount"]/a[1]')  
# anyone = driver.find_element(By.LINK_TEXT, value='anyone can edit')  
#  
#  
# search = driver.find_element(By.NAME, value='search')  
# search.send_keys('Python')  
# search.send_keys(Keys.RETURN)  
  
first_name = driver.find_element(By.NAME, value='fName')  
last_name = driver.find_element(By.NAME, value='lName')  
email = driver.find_element(By.NAME, value='email')  
  
first_name.send_keys('test')  
last_name.send_keys('tester')  
email.send_keys('test_example@gmail.com')  
email.send_keys(Keys.RETURN)
```


get_attribute

The getAttribute method in Selenium is used to retrieve the value of a specific attribute from a web element. For example, if you have an HTML element like `input type="text" value="Hello"`, you can use getAttribute("value") to get the value "Hello".

Or in the example of the cookie cutter project:




```html
<div class="product unlocked enabled" onmouseout="Game.tooltip.shouldHide=1;"
     onmouseover="Game.tooltip.dynamic=1;Game.tooltip.draw(this,function(){return Game.ObjectsById[0].tooltip();},'store');Game.tooltip.wobble();"
     id="product0">
    <div class="icon off" id="productIconOff0" style="background-position: -64px 0px;"></div>
    <div class="icon" id="productIcon0" style="background-position: 0px 0px;"></div>
    <div class="content">
        <div class="lockedTitle">???</div>
        <div class="title productName" id="productName0">Cursor</div>
        <span class="priceMult" id="productPriceMult0"></span><span class="price" id="productPrice0">15</span>
        <div class="title owned" id="productOwned0"></div>
    </div>
</div>
```



```python

unlocked_items = driver.find_elements(By.CSS_SELECTOR, '.unlocked')  
# This returns a list of items where `unlocked' is in the class name
unlocked_items_ids = [i.get_attribute('id') for i in unlocked_items]
# This looks at the unlocked_items list. For every unlocked_item,, it retrvies the id and its value
```