# gender_classify
detects if the wirtten Hebrew text is by male or female
[![PyPI download total](https://img.shields.io/pypi/dm/hebrew-tokenizer.svg)](https://pypi.python.org/pypi/hebrew-tokenizer/)  [![PyPI version fury.io](https://badge.fury.io/py/hebrew-tokenizer.svg)](https://pypi.python.org/pypi/hebrew-tokenizer/)
 [![MIT license](https://img.shields.io/badge/License-MIT-blue.svg)](https://lbesson.mit-license.org/) 


# Hebrew Tokenizer
A very simple python tokenizer for Hebrew text.  
No batteries included - No dependencies needed!

### UPDATES
#### 28/04/21
accented letters support was added - great work [Daniel](https://github.com/Gilthans) 馃憡

#### 23/10/2020
Added support for Python 3.8+.   
The Code look like shit now BUT it's working:smile:.   
In the near future I will wrap it up nicely.  

### Installation
1. via pip
    1. ```pip install hebrew_tokenizer```
2. from source
    1. Download / Clone
    2. ```python setup.py install```

### Usage
```python
import hebrew_tokenizer as ht
hebrew_text = "讗转诪讜诇, 8.6.2018, 讘砖注讛 17:00 讛诇讻转讬 注诐 讗诪讗 诇诪讻讜诇转"
tokens = ht.tokenize(hebrew_text)  # tokenize returns a generator!
for grp, token, token_num, (start_index, end_index) in tokens:
    print('{}, {}'.format(grp, token))

>>> HEBREW, '讗转诪讜诇'
>>> PUNCTUATION, ',' 
>>> DATE, '8.6.2018'
>>> PUNCTUATION, ',' 
>>> HEBREW, '讘砖注讛'
>>> HOUR, '17:00'
>>> HEBREW, '讛诇讻转讬'
>>> HEBREW, '注诐'
>>> HEBREW, '讗诪讗'
>>> HEBREW, '诇诪讻讜诇转'

# by default it doesn't return whitespaces but it can be done easily
tokens = ht.tokenize(hebrew_text, with_whitespaces=True)  # notice the with_whitespace flag
for grp, token, token_num, (start_index, end_index) in tokens:
    print('{}, {}'.format(grp, token))
  
>>> HEBREW, '讗转诪讜诇'
>>> WHITESPACE, ''
>>> PUNCTUATION, ',' 
>>> WHITESPACE, ''
>>> DATE, '8.6.2018'
>>> PUNCTUATION, ','
>>> WHITESPACE, ''
>>> HEBREW, '讘砖注讛'
>>> WHITESPACE, ''
>>> HOUR, '17:00'
>>> WHITESPACE, ''
>>> HEBREW, '讛诇讻转讬'
>>> WHITESPACE, ''
>>> HEBREW, '注诐'
>>> WHITESPACE, ''
>>> HEBREW, '讗诪讗'
>>> WHITESPACE, ''
>>> HEBREW, '诇诪讻讜诇转'
```

### Disclaimer
This is __***NOT***__ a POS tagger.   
If that is what you are looking for - check out [yap](https://github.com/habeanf/yap).


### Contribute  
Found a special case where the tokenizer fails?   
1. Try to fix it on your own by improving the regex patterns the tokenizer is based on.  
2. Make sure that your improvement doesn't break the other scenarios in test.py
3. Add you special case to test.py 
4. Commit a pull request.  

### NLPH
For other great Hebrew resources check out [NLPH](https://github.com/NLPH/NLPH_Resources)
