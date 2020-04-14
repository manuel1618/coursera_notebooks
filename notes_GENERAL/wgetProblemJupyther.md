# Solving the wget Problem

- !wget does not work on local jupyther files
- So this:

```python
!wget -O moviedataset.zip https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/ML0101ENv3/labs/moviedataset.zip
print('unziping ...')
!unzip -o -j moviedataset.zip 
```

- becomes: 

```python
import requests
try:
    !unzip -o -j moviedataset.zip 
except:
    fname = 'moviedataset.zip'
    url = 'https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/ML0101ENv3/labs/' + fname
    r = requests.get(url)
    open(fname , 'wb').write(r.content)
    !unzip -o -j moviedataset.zip 
```

and the easy version without any zipping

```python
import requests
def downloadFile(url,fileName):
    fname = fileName
    url = url + "/" +fileName
    r = requests.get(url)
    open(fname , 'wb').write(r.content)
    print('Data downloaded!')
    return

downloadFile("https://cocl.us/new_york_dataset",'newyork_data.json')
```

Eventuell reicht auch das nur:

'''python
Download: https://eternallybored.org/misc/wget/
put it into sys32
'''