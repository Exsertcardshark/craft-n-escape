# Craft N' Escape

Items and crafting recipes for [The Escapists](http://escapistgame.com/), on one searchable page.

_Because everyone loves it when a plan comes together_

## Features

  - Web-based
  - List of all available items with all their attributes (attack power, illegal, price, etc)
    - Can be filtered by item name
    - (WIP) Items icon
  - (WIP) Crafting recipes for applicable items
  - (WIP) Given a list of items you own, you can get the list of items you can craft

## Prerequisites

  - Should work on any Python 3.x version. Feel free to test with another Python version and give me feedback
  - A [uWSGI](https://uwsgi-docs.readthedocs.io/en/latest/)-capable web server (optional, but recommended)
  - The Escapists game

## Installation

  1. Clone this repo somewhere
  2. `pip install -r requirements.txt`
  3. `export FLASK_APP=cnc.py` (Windows users: `set FLASK_APP=cnc.py`)

## Configuration

Copy the `config.example.py` file to `config.py` and fill in the configuration parameters.

Available configuration parameters are:

  - `SECRET_KEY` Set this to a complex random value
  - `DEBUG` Enable/disable debug mode
  - `LOGGER_HANDLER_POLICY` Policy of the default logging handler

More informations on the three above can be found [here](http://flask.pocoo.org/docs/0.12/config/#builtin-configuration-values).

I'll let you search yourself about how to configure a web server along uWSGI.

## Usage

  - Standalone

Run the internal web server, which will be accessible at `http://localhost:8080`:

```
python local.py
```

Edit this file and change the interface/port as needed.

  - uWSGI

The uWSGI file you'll have to set in your uWSGI configuration is `uwsgi.py`. The callable is `app`.

  - Others

You'll probably have to hack with this application to make it work with one of the solutions described
[here](http://flask.pocoo.org/docs/0.12/deploying/). Send me a pull request if you make it work.

A Flask command (`flask build`) can be used to regenerate the items listing file, i.e when the game has been
updated. Run `flask build --help` for more information.

## How it works

This project is mainly powered by [Flask](http://flask.pocoo.org/) (Python). The Flask part (the backend)
is responsible to provide the `storage/data/items.json` to [Vue.js](http://vuejs.org/) 2 (the frontend).

This file is generated by the `flask build` command by parsing the game's files, especially the
`Data/items_*.dat` ones.

For more information, I suggest you do dive into the code starting with the `cnc.py` file.

## Credits

The Escapists © 2015 - 2017 Mouldy Toof Studios and Team17 Digital Ltd

This project isn't supported nor endorsed by Mouldy Toof Studios and Team17 Digital.