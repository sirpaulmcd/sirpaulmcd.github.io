---
layout: default
title: Databasify
permalink: /student-projects/databasify/
parent: Student Projects
# grand_parent: Blog
has_children: false
nav_order: 2
nav_exclude: false
has_toc: false
---

# Databasify
Databasify is a web application written with Flask and Bootstrap that can query song information using the Spotify API. 
The information is populated into a database where users can generate custom playlists based on a number of song metrics beyond those shown in the Spotify app.
Such metrics include properties such as tempo, popularity, and even danceability. 
The project repo can be found [here](https://github.com/rlisowski10/Databasify/).

## Features

<p align="center">
    <img src="/assets/images/databasify/search-artists.png" alt="artist-view.png" width=700>
    <br/>
    Populate SQLite database with custom song data from the Spotify API
</p>

<p align="center">
    <img src="/assets/images/databasify/search-songs.png" alt="song-view.png" width=700>
    <br/>
    Query SQLite database to access dozens of hidden song, album, and artist attributes
</p>

<p align="center">
    <img src="/assets/images/databasify/create-playlist.png" alt="create-playlist.png" width=700>
    <br/>
    Use advanced search functionality to create exciting new playlists
</p>

## Tech and Frameworks
<b>Built with:</b>
- [Flask](https://pypi.org/project/Flask/)
- [SQLAlchemy](https://pypi.org/project/SQLAlchemy/)
- [Bootstrap V4](https://getbootstrap.com/docs/4.0/getting-started/introduction/)
- [SQLite](https://www.sqlite.org/index.html)

## Installation
<b>Installation steps:</b>
- Clone the repository to the local system
- Install Python 3 for your system from [Python.org](https://www.python.org/)
- Install [Flask](https://pypi.org/project/Flask/) using PIP install
- Install [SQLAlchemy](https://pypi.org/project/SQLAlchemy/) using PIP install
- Install [SQLite](https://www.sqlite.org/index.html) for your system

## How to Run
<b>To run the app:</b>
- Open the project in an editor such as VSCode
- Open start.py and run the file
- Follow the local link in the terminal to open the web application
- Explore what the app has to offer!

## License
MIT © [rlisowski10](https://github.com/rlisowski10/)