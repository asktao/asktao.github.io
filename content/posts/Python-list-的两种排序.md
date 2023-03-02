---
title: "Python List 的两种排序"
date: 2021-10-09T10:44:00+08:00
draft: false
tags: [programming,Python]
---


1.
```python
# import a groupby() method
# from itertools module
from itertools import groupby

# dictionary
INFO = [
	{'employee': 'XYZ_1', 'company': 'ABC_1'},
	{'employee': 'XYZ_2', 'company': 'ABC_2'},
	{'employee': 'XYZ_3', 'company': 'ABC_3'},
	{'employee': 'XYZ_4', 'company': 'ABC_3'},
	{'employee': 'XYZ_5', 'company': 'ABC_2'},
	{'employee': 'XYZ_6', 'company': 'ABC_3'},
	{'employee': 'XYZ_7', 'company': 'ABC_1'},
	{'employee': 'XYZ_8', 'company': 'ABC_2'},
	{'employee': 'XYZ_9', 'company': 'ABC_1'}
]

# define a fuction for key
def key_func(k):
	return k['company']

# sort INFO data by 'company' key.
INFO = sorted(INFO, key=key_func)

for key, value in groupby(INFO, key_func):
	print(key)
	print(list(value))
```

输出
```python
ABC_1
[{'employee': 'XYZ_1', 'company': 'ABC_1'}, {'employee': 'XYZ_7', 'company': 'ABC_1'}, {'employee': 'XYZ_9', 'company': 'ABC_1'}]

ABC_2
[{'employee': 'XYZ_2', 'company': 'ABC_2'}, {'employee': 'XYZ_5', 'company': 'ABC_2'}, {'employee': 'XYZ_8', 'company': 'ABC_2'}]

ABC_3
[{'employee': 'XYZ_3', 'company': 'ABC_3'}, {'employee': 'XYZ_4', 'company': 'ABC_3'}, {'employee': 'XYZ_6', 'company': 'ABC_3'}]
```

2.
```python
# import required methods
from itertools import groupby
from operator import itemgetter

# dictionary
students = [
	{'mark': '65', 'grade': 'C'},
	{'mark': '86', 'grade': 'A'},
	{'mark': '73', 'grade': 'B'},
	{'mark': '49', 'grade': 'D'},
	{'mark': '91', 'grade': 'A'},
	{'mark': '79', 'grade': 'B'}
]

# Sort students data by grade key.
students = sorted(students,
				key = itemgetter('grade'))

# Display data grouped by grade
for key, value in groupby(students,
						key = itemgetter('grade')):
	print(key)
	for k in value:
		print(k)
```

输出
```python
A
{'mark': '86', 'grade': 'A'}
{'mark': '91', 'grade': 'A'}

B
{'mark': '73', 'grade': 'B'}
{'mark': '79', 'grade': 'B'}

C
{'mark': '65', 'grade': 'C'}

D
{'mark': '49', 'grade': 'D'}
```

