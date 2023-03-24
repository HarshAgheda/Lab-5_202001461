# Lab-5_202001461
Git Repository for Lab 5

Repository used : https://github.com/GaiZhenbiao/ChuanhuChatGPT

File used : https://github.com/GaiZhenbiao/ChuanhuChatGPT/ChuanhuChatbot.py

Tool Used Pylint

## Error 1
### Errornous Code:
import os

import logging

import sys

import gradio as gr

![image2](https://user-images.githubusercontent.com/84801162/227498237-56eb2440-f9b4-46c7-b559-34c444d5cce0.png)


### Error Flagged:
ChuanhuChatbot.py:6:0: E0401: Unable to import 'gradio' (import-error) 

![image1](https://user-images.githubusercontent.com/84801162/227498289-d334321c-47fe-4add-9851-a2686c7f3620.png)


### Analysis:
The above mentioned import errors are false positives;They are flagged by mypy because it was unable to locate the one you were attempting to import. These libraries were actually imported and used by the programme, so there is no actual error.

## Error 2
### Errornous Code:

from modules.utils import *

from modules.presets import *

from modules.overwrites import *

from modules.chat_func import *

![image4](https://user-images.githubusercontent.com/84801162/227498454-33a5276d-7e9b-4050-a11c-027b10c5066b.png)


### Errors Flagged:

ChuanhuChatbot.py:8:0: W0401: Wildcard import modules.utils (wildcard-import)

ChuanhuChatbot.py:9:0: W0401: Wildcard import modules.presets (wildcard-import)

ChuanhuChatbot.py:10:0: W0401: Wildcard import modules.overwrites (wildcard-import)

ChuanhuChatbot.py:11:0: W0401: Wildcard import modules.chat_func (wildcard-import)

![image5](https://user-images.githubusercontent.com/84801162/227498519-6608a31f-a541-4304-825b-a8edca5d7afb.png)

### Analysis: 
This type of error in code indicates that some of the modules are wholely which, in larger projects, create confusion.So, instead of importing them as whole, programmer should import only the objects which are needed.


## Error 3
Errornous code:
if os.environ.get("dockerrun") == "yes":
    dockerflag = True
else:
    dockerflag = False

authflag = False

if dockerflag:
    my_api_key = os.environ.get("my_api_key")
    if my_api_key == "empty":
        logging.error("Please give a api key!")
        sys.exit(1)
    # auth
    username = os.environ.get("USERNAME")
    password = os.environ.get("PASSWORD")
    if not (isinstance(username, type(None)) or isinstance(password, type(None))):
        authflag = True
![image3](https://user-images.githubusercontent.com/84801162/227498701-cda8af2a-2723-4074-99a2-ce9d14b4a4d5.png)


### Errors Flagged:
ChuanhuChatbot.py:18:0: C0103: Constant name "my_api_key" doesn't conform to UPPER_CASE naming style (invalid-name)

ChuanhuChatbot.py:21:0: R1703: The if statement can be replaced with 'var = bool(test)' (simplifiable-if-statement)

ChuanhuChatbot.py:22:4: C0103: Constant name "dockerflag" doesn't conform to UPPER_CASE naming style (invalid-name)

ChuanhuChatbot.py:24:4: C0103: Constant name "dockerflag" doesn't conform to UPPER_CASE naming style (invalid-name)

ChuanhuChatbot.py:26:0: C0103: Constant name "authflag" doesn't conform to UPPER_CASE naming style (invalid-name)

ChuanhuChatbot.py:37:8: C0103: Constant name "authflag" doesn't conform to UPPER_CASE naming style (invalid-name)

![image9](https://user-images.githubusercontent.com/84801162/227498734-438ab151-34f9-4fd2-a539-e3243583e784.png)

 
### Analysis: 
These errors indicate that the naming convetion is not properly done, in the sense that, the names of the variables should be in capital letters with use of underscores wherever required.

## Error 4 
### Errornous code:
with open("api_key.txt", "r") as f:

    my_api_key = f.read().strip()
    
![image8](https://user-images.githubusercontent.com/84801162/227498768-5554f3bb-6213-4c07-8df7-968e043cc261.png)


### Errors Flagged:
ChuanhuChatbot.py:44:13: W1514: Using open without explicitly specifying an encoding (unspecified-encoding)

![image1](https://user-images.githubusercontent.com/84801162/227498869-23b01a2a-bb05-4ce8-831f-5264600fd0cc.png)


### Analysis: 
This error specifies that the file is opened using unspecifies encoding in stead, the file should be opened using the UTF-8 encoding, which is a common and widely supported encoding for text files. By specifying the encoding, you can ensure that your code will behave consistently across different platforms and environments.

## Error 5
### Errornous code:

  placeholder=f"在这里输入System Prompt...",
  
  laceholder=f"设置文件名: 默认为.json，可选为.md",
  
  placeholder=f"在这里输入API地址...",
  
  placeholder=f"在这里输入代理地址...",
  
![image6](https://user-images.githubusercontent.com/84801162/227498985-771f1f31-0374-429c-a7ac-98c1cea1da03.png)


### Errors Flagged:
ChuanhuChatbot.py:98:36: W1309: Using an f-string that does not have any interpolated variables (f-string-without-interpolation)

ChuanhuChatbot.py:122:36: W1309: Using an f-string that does not have any interpolated variables (f-string-without-interpolation)

ChuanhuChatbot.py:169:52: W1309: Using an f-string that does not have any interpolated variables (f-string-without-interpolation)

ChuanhuChatbot.py:205:36: W1309: Using an f-string that does not have any interpolated variables (f-string-without-interpolation)

ChuanhuChatbot.py:213:36: W1309: Using an f-string that does not have any interpolated variables (f-string-without-interpolation)

![image7](https://user-images.githubusercontent.com/84801162/227499026-e3807912-06cf-4f52-a4bb-80bd6848cea9.png)


### Analysis: 
These warnings indicate that you are using an f-string, which is a string literal that allows for embedded expressions, but the f-string does not contain any interpolated variables.In other words the string does not actually contain any expressions or variables that need to be evaluated or formatted.While it is allowed to use it  that way but it creates confusion for other developers.
