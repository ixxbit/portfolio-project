# Download Instagram profile pic using Python

Instagram is a photo and video-sharing social networking service owned by Facebook, Python provides powerful tools for web scraping of Instagram.

**Modules required and Installation:**

**requests –**   
  


```text
pip install requests
```

**concept –**  
For a given user profile, open _view-source_ and find _“profile\_pic\_url\_hd”_ . To find press ctrl+f and type _“profile\_pic\_url\_hd”_ the link with it is our data or profile pic.  
link will look link : 

```text
https://scontent-bom1-1.cdninstagram.com/vp/d2df9b2d162969e87200984ee763cc27/5DC590F2/t51.2885-19/s320x320/61851740_845288152518430_7068999703693623296_n.jpg?_nc_ht=scontent-bom1-1.cdninstagram.com
```

![](https://media.geeksforgeeks.org/wp-content/uploads/20190809214848/Screenshot-from-2019-08-09-16-51-572.png)

Below is the stepwise implementation of the project – 

**Step 1:** import all dependence filter\_none

brightness\_4

| `import` `requestsfrom` `bs4` `import` `BeautifulSoup as bsimport` `jsonimport` `randomimport` `os.path` |
| :--- |


**Step 2:** Ask for username and send a response to Instagram.filter\_none

brightness\_4

| `insta_url='`[`https://www.instagram.com`](https://www.instagram.com/)`'inta_username=` `input('enter username of instagram : ')`  `response` `=` `requests.get(f"{insta_url}/{inta_username}/")` |
| :--- |


**Step 3:** if the response is ok, find profile photo linkfilter\_none

brightness\_4

| `if` `response.ok:    html=response.text`      `bs_html=bs(html, features="lxml")    bs_html=bs_html.text    index=bs_html.find('profile_pic_url_hd')+21`      `remaining_text=bs_html[index:]    remaining_text_index=remaining_text.find('requested_by_viewer')-3    string_url=remaining_text[:remaining_text_index]`      `print(string_url,` `"\n \n downloading..........")` |
| :--- |


**Step 4:** Now, create a loop and download photo.filter\_none

brightness\_4

| `while` `True:    filename='pic'+str(random.randint(1,` `100000))+'.jpg'    file_exists` `=` `os.path.isfile(filename)`      `if` `not` `file_exists:        with` `open(filename,` `'wb+') as handle:            response` `=` `requests.get(string_url, stream=True)            if` `not` `response.ok:                print(response)            for` `block` `in` `response.iter_content(1024):                if` `not` `block:                    break                handle.write(block)    else:        continue    breakprint("\n                downloading completed ..............")` |
| :--- |


**Complete code :**filter\_none

brightness\_4

| `import` `requestsfrom` `bs4` `import` `BeautifulSoup as bsimport` `jsonimport` `randomimport` `os.path`  `insta_url` `='`[`https://www.instagram.com`](https://www.instagram.com/)`'inta_username` `=` `input('enter username of instagram : ')`  `response` `=` `requests.get(f"{insta_url}/{inta_username}/")`  `if` `response.ok:    html` `=` `response.text    bs_html` `=` `bs(html, features` `="lxml")    bs_html` `=` `bs_html.text    index` `=` `bs_html.find('profile_pic_url_hd')+21    remaining_text` `=` `bs_html[index:]    remaining_text_index` `=` `remaining_text.find('requested_by_viewer')-3    string_url` `=` `remaining_text[:remaining_text_index]`      `print(string_url,` `"\n \n downloading..........")`   `` `while` `True:    filename` `='pic'+str(random.randint(1,` `100000))+'.jpg'    file_exists` `=` `os.path.isfile(filename)`      `if` `not` `file_exists:        with` `open(filename,` `'wb+') as handle:            response` `=` `requests.get(string_url, stream` `=` `True)            if` `not` `response.ok:                print(response)            for` `block` `in` `response.iter_content(1024):                if` `not` `block:                    break                handle.write(block)    else:        continue    breakprint("\n                downloading completed ..............")` |
| :--- |


**Output:**   
![](https://media.geeksforgeeks.org/wp-content/uploads/20190809215437/Screenshot-from-2019-08-09-21-52-06.png)  
  
  


### Recommended Posts:

* [Like instagram pictures using Selenium \| Python](https://www.geeksforgeeks.org/like-instagram-pictures-using-selenium-python/)
* [Post a picture automatically on Instagram using Python](https://www.geeksforgeeks.org/post-a-picture-automatically-on-instagram-using-python/)
* [How to download Google Images using Python](https://www.geeksforgeeks.org/how-to-download-google-images-using-python/)
* [Download and Install Python 3 Latest Version](https://www.geeksforgeeks.org/download-and-install-python-3-latest-version/)
* [Simple Multithreaded Download Manager in Python](https://www.geeksforgeeks.org/simple-multithreaded-download-manager-in-python/)
* [Python \| Download YouTube videos using youtube\_dl module](https://www.geeksforgeeks.org/python-download-youtube-videos-using-youtube_dl-module/)
* [How to download and install Python Latest Version on Windows](https://www.geeksforgeeks.org/how-to-download-and-install-python-latest-version-on-windows/)
* [Python \| Program to download complete Youtube playlist](https://www.geeksforgeeks.org/python-program-to-download-complete-youtube-playlist/)
* [Pytube \| Python library to download youtube videos](https://www.geeksforgeeks.org/pytube-python-library-download-youtube-videos/)
* [How to download and install Python Latest Version on macOS / Mac OS X](https://www.geeksforgeeks.org/how-to-download-and-install-python-latest-version-on-macos-mac-os-x/)
* [How to download and install Python Latest Version on Android](https://www.geeksforgeeks.org/how-to-download-and-install-python-latest-version-on-android/)
* [Python \| How to download windows lock-screen wallpapers](https://www.geeksforgeeks.org/python-how-to-download-windows-lock-screen-wallpapers/)
* [YouTube Media/Audio Download using Python \| pafy](https://www.geeksforgeeks.org/youtube-mediaaudio-download-using-python-pafy/)
* [How to download and install Python Latest Version on Linux](https://www.geeksforgeeks.org/how-to-download-and-install-python-latest-version-on-linux/)
* [Python \| CAP - Cumulative Accuracy Profile analysis](https://www.geeksforgeeks.org/python-cap-cumulative-accuracy-profile-analysis/)

![](https://media.geeksforgeeks.org/auth/profile/jgefxv492547gczcf7e9)[**its\_vinayak**](https://auth.geeksforgeeks.org/user/its_vinayak/articles)Check out this Author's [contributed articles](https://auth.geeksforgeeks.org/user/its_vinayak/articles).

