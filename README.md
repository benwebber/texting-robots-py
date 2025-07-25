# texting-robots-py

Python binding for [Texting Robots](https://github.com/Smerity/texting_robots).
Refer to that project for details.

## Usage

```python
from texting_robots import Robot

txt = b'''
User-Agent: FerrisCrawler
Allow: /ocean
Disallow: /rust
Disallow: /forest*.py
Crawl-Delay: 10
User-Agent: *
Disallow: /
Sitemap: https://www.example.com/site.xml
'''

robot = Robot('FerrisCrawler', txt)

assert robot.delay == 10

assert robot.sitemaps == ['https://www.example.com/site.xml']

assert robot.allowed('https://www.rust-lang.org/ocean')
assert robot.allowed('/ocean')
assert robot.allowed('/ocean/reef.html')
assert not robot.allowed('/rust')
assert not robot.allowed('/forest/tree/snake.py')
```

## Versions

This project will follow the same version scheme as Texting Robots.
That is, version 0.2.2 of this project corresponds to the same version of the Rust library.
If necessary, this project will use [post releases](https://packaging.python.org/en/latest/specifications/version-specifiers/#post-releases) for changes specific to the Python package.

## Licence

This project is dual-licensed under the Apache 2.0 and MIT licences, just like Texting Robots.
