# stackdump2txt
Stack (SO and SE) Data Dump converted to text

# Usage

You can use this by doing:


```
python3 stackdump2txt.py unix.stackexchange.com.7z
```

Where `unix.stackexchange.com.7z` is one of the possible data dump from [here]() and is just an example.
You need to be on a Linux distro, doesn't matter which, but make sure you have:

# Requirements

- 7zip installed
- more than 100GB of drive space
- more than 3GB of ram (6GB is good)

# Stats?
It will handle decompression, so make sure you have (if you're doing this on all data dump or one of the biggest, SO) more than double the amount of what you want to convert to txt (as a rule of thumb). 1TB is good, but if less, 100+ GB is good enough for doing most data dumps.

Also, the result is (obviously) much smaller given it is in plaintext form, instead of the encoding that stack used on their data dumps.
so for the SO data dump, it will go from 21GB for all stackoverflow-* dumps, to less (don't have stats right now, will add them later). Decompressed, it take more than 70GB, but converted to text, it's a little over 58GB (and once compressed, it's smaller than 20GB!)

# Time
This will take a varying amount of time, but on an old i3 cpu of 2GHZ, on one of the biggest data dump, which is the one from SO/main site, it will take roughly 1-4 hours, and a couple of minutes for the other data dumps (I'll upload some stats later, I promise!). 

I know, the time it takes is horrible (although that's only for SO/main site) but the result is somewhat satisfactory (I like the formatting decision I made, but I know they could have been better).

# Formatting
The formatting is the following:

```
###ID###
TITLE:
QUESTION:
TAGS:
COMMENT:
----------------
ANSWER:
COMMENT:
----------------
ANSWER:
COMMENT:
```

They are each separated by either ID (which is the post's id you can usually see on SO/SE urls) or `-` for answers.
Notice how I didn't include:

- names/username
- stars
- upvote/downvote
- history/edits
- answer's id

And many other things. This is a design choice, but I don't mind expanding it to support those too (I made this in two weeks, so please understand).

# Why

Ah yes. There are a lot of reasons for this. The following is a non-exhaustive list of that:

- There was some java tool I found but it used a DB software that needed a lot, ***lot*** of ram! This one only needs roughly more than 3GB (I did that on 6GB of ram)
- None had this kind of formatting decision, where the focus is all answers, all questions, all comments, all ids, and nothing else (As mentioned, I don't mind supporting those though but this was done hastily)
- I did find some that could have worked if I fiddled with it enough, but it depends on third-party libraries, such as panda ***too much***. It also didn't take into account the huge memory usage!
- Yes, I used html2text (a fork of it, which I'll credit, don't worry) both because I wanted a pure python implementation, ***and*** because lxml and bs4 (beautifulsoup) didn't give a satisfactory result (it had errors with some HTML encoding, admittedly)
