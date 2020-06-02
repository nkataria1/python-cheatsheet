# Lambdas 
Full tutorial: https://caisbalderas.com/blog/iterating-with-python-lambdas/
map(lambda v: v*5, x)  is same as [v*5 for v in x]
map(lambda v: v*5, filter(lambda v:v%2, x))
Multiplies values by 5 that are NOT divisible by 2
Collections
(https://svn.python.org/projects/python/trunk/Lib/collections.py)

# Counters 
class Counter(dict):
    '''Dict subclass for counting hashable items.  Sometimes called a bag
    or multiset.  Elements are stored as dictionary keys and their counts
    are stored as dictionary values.
    
# List
[::-1] : Reverses the entire list
zip(l1,l2): Merges two lists
# Sorting
Sort hashmap by value : 
sorted(x.items(), key=lambda kv: kv[1])
Reverse sort hashmap by value:
sorted_x = sorted(x.items(), key=lambda kv: kv[1], reverse=True)
sorted(list, reverse=True)
Append list.append(elem)
Insert at index list.insert(i, elem)
Pop: list.pop()
Joining
Join characters : “”.join(c),
Join int’s, floats etc: “”.join(map(str, i))

# Comparators:
def mycmp(s1, s2):
   return cmp(len(s2), len(s1)) or cmp(s1.upper(), s2.upper())
print sorted(strings, cmp=mycmp)
OR
strings = "here are Some sample strings to be sorted".split()
 
def mykey(x):
   return -len(x), x.upper()
 
print sorted(strings, key=mykey)

Comparator
class compare(str):
    def __lt__(x, y):
        return x+y > y+x
    
class Solution:
    def largestNumber(self, nums: List[int]) -> str:
        largest_num = ''.join(sorted([str(x) for x in nums], key=compare))
        return '0' if largest_num[0] == '0' else largest_num
https://py.checkio.org/blog/how-did-python3-lose-cmd-sorted/
File Operations
How to check if a file exists
import os; os.path.exists('file_path')
List all files in directory
files = os.listdir(file_path)
Check if a file is a file or  directory
os.path.isdir(file_path)
os.path.isfile(file_path)
Opening a file:
With open(<file_path”, “<mode>”) as file:
# read something here
f.write() 
Reading  a line : sys.stdin.readline().strip() >> Strip() to remove extra spaces and new lines. 
ASCII: lowercase alphabets : 97-122, uppercase alphabets :65-91, numbers : 48-57

# Strings
Check substring : str1 in st2 or str2.find(‘str1’)
Formatting: https://pyformat.info/
String to datetime
datetime.datetime.strptime("1968-08-26T12:00:00Z", "%Y-%m-%dT%H:%M:%SZ").year

Characters 
	ord(c) : Char to int
	chr(97): int to char
	Sys.maxsize: maximum int
	-sys.maxsize-1: minimum int
  
# Queue
q = Q.PriorityQueue()
q.put(10)
q.put(1)
q.put(5)
while not q.empty():
		print q.get(),

# Heap

for num in nums:
      heapq.heappush(heap, -num)

for i in range(k):
      val = heapq.heappop(heap)

# HTTP Requests 

GET

import requests

resp = requests.get('https://todolist.example.com/tasks/')
if resp.status_code != 200:
    # This means something went wrong.
    raise ApiError('GET /tasks/ {}'.format(resp.status_code))
for todo_item in resp.json():
    print('{} {}'.format(todo_item['id'], todo_item['summary']))

r = requests.get(url, headers=headers,  params=payload)
payload={'isbn':9780316069359}

Using urllib
Params = {‘a’ : ‘b’}
Url = 'https://itunes.apple.com/search?’.format(urllib.urlencode(params)) 
Response  = urllib.urlopen(Url) 
json.loads(response.read())
POST (CREATE)

task = {"summary": "Take out trash", "description": "" }
# The shortcut
resp = requests.post('https://todolist.example.com/tasks/', json=task)
# The equivalent longer version
resp = requests.post('https://todolist.example.com/tasks/',
                     data=json.dumps(task),
                     headers={'Content-Type':'application/json'},
if resp.status_code != 201:
    raise ApiError('POST /tasks/ {}'.format(resp.status_code))
print('Created task. ID: {}'.format(resp.json()["id"]))

PUT (CREATE OR UPDATE)
url = _url('/tasks/{:d}/'.format(task_id))
return requests.put(url, json=task) 

DELETE
requests.delete(_url('/tasks/{:d}/'.format(task_id)))


# REGEX
pattern = re.compile(r"\d{3}\.\d{3}\.\d{3}\.\d{3}$") ←-- Compile regex, this is looking for ipv4 address
re.match(pattern, ‘123.123.123.123’) 
m =re.findall(r'(?<=\<)\s*([^\/\s])', "<p><a href=\"http://www.quackit.com/html/tutorial/html_links.cfm\">Example Link</a></p>")


OR 

re.search(pattern, ‘123.123.123.123’) 

.* : 0 and unlimited
‘+’ : 1 and unlimited
? : 0 and 1 

Practice RegeX: https://www.hackerrank.com/domains/regex 
Capturing groups use ()
r'(hackerrank)+' : Matches all occurrences of hackerrank 
Non capturing groups use (?:)
Alternations
| 
If used in capturing groups it will match entire string like (abc|def|ghi) matches abc or def or ghi 
If used with match [], ([a-z]|[A-Z])will match individual characters a to z or A to Z 
Anchors 
^ for start and $ to finish: 
"^[^\n]{3}\.[^\n]{3}\.[^\n]{3}\.[^\n]{3}$: Matches ip addresses 
Whitespace Characters
\s matches whitespace characters
Non Whitespace Characters
\S matches not whitespace characters 
Words
\w matches words
Non words
\W matches non words 
Match one from the group
[] 
[123] will match a single character which should be either 1 or 2 or 3
Negate match 
[^] Do not match any character in the group 
Range
[a-zA-z0-9]{3} : Matches any of lower or upper case alphabets or digits 3 times
[a-zA-z0-9]{1,3} : Matches any of lower or upper case alphabets or digits 1,2,3 times 
[a-zA-z0-9]{3,} : Matches any of lower or upper case alphabet or digits 3 or more times
*
Matches 0 or more characters
?
Matches 0 or 1 characters
+
Matches 1 or more characters 
Word Boundary
Create a boundary inside the word to match
Example: \b[a-zA-Z]*\b will ignore anything before lower and uppercase characters and after them as well
Match already matched group number
(\d)\1 will match 00,11,22,33,44,55,66,77,88,99
Backreferences
Say we matched a pattern earlier and we want to match the same again
Check string is 123456 or 12-34-56 i.e - after every two digits if there was a first dash. If first dash did not exist, no dash should exist in remaining string
Answer r"^\d{2}(-?)\d{2}\1\d{2}$"
Forward References
Match a previous group based on a value in future
Example: /^(\2tic|(tac))+$/ will match if
String consists of tic or tac.
tic should not be immediate neighbour of itself.
The first tic must occur only when tac has appeared at least twice before.
Lookahead
Positive (?=)
Match all a followed by b
r”a(?=b)
Negative (?!)
Match all not followed by c
r”a(?!b)”
Lookbehin
Positive (?<=)
Match all characters that come after an odd number
r”(?<=[13579])\w
NEgative (?<!
