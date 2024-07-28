---
layout: default
title: "RSS"
---

This is where I will write about RSS tools and ideas.

## YouTube Feeds

You can get a YouTube feed as RSS via this URL

```html
https://www.youtube.com/feeds/videos.xml?channel_id=XXXXXXX
```
Where XXXXXXX is the channel_id of the YouTube channel.
* TODO - document a link on how to find the Channel ID.

## Filtering

I made some python code to filter RSS. i.e. The [Celtic FC](https://www.youtube.com/@CelticFC) RSS feed at https://www.youtube.com/feeds/videos.xml?channel_id=UCBN-bb-hE7jYlcp4exwXRsQ and the keyword "Postecoglou".

* TODO - It is currently hardcoded.
* IDEA - Make an Ideas page that pulls in any IDEAs from the site and puts them on the page. It runs a midnight via cron or manually by hitting a URL.

```python
#!/usr/bin/env python3
import os
import sys
from wsgiref.handlers import CGIHandler
from flask import Flask, Response
import requests
import xml.etree.ElementTree as ET

app = Flask(__name__)

# Configurable list of keywords
KEYWORDS = ['Postecoglou']

def filter_items_by_keywords(entries, keywords):
    filtered_items = []

    for entry in entries:
        title = entry.find('{http://www.w3.org/2005/Atom}title').text
        if any(keyword.lower() in title.lower() for keyword in keywords):
            filtered_items.append(entry)

    return filtered_items

def feed_to_xml_string(root, entries):
    for entry in entries:
        root.remove(entry)

    for entry in filter_items_by_keywords(entries, KEYWORDS):
        root.append(entry)

    return ET.tostring(root, encoding='utf-8', method='xml')

@app.route('/filtered_feed')
def filtered_feed():
    url = "https://www.youtube.com/feeds/videos.xml?channel_id=UCBN-bb-hE7jYlcp4exwXRsQ"
    response = requests.get(url)
    root = ET.fromstring(response.content)
    entries = root.findall('.//{http://www.w3.org/2005/Atom}entry')

    filtered_feed_xml = feed_to_xml_string(root, entries)

    return Response(filtered_feed_xml, content_type='application/rss+xml')

if __name__ == "__main__":
    flask_env = os.environ.get('FLASK_ENV', 'production')
    if flask_env == 'production':
        CGIHandler().run(app)
    else:
        app.run(debug=True, port=8080)
```

IDEA: I want to have an RSS of these topics which is updated every day. If a topic is updated with a certain kind of commit string, I want it those strings to make a new blog post. So, I need to process the commit messages into a summary.
