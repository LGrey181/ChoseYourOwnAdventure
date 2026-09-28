# Choose Your Own Adventure

A small Go web app that serves a choose-your-own-adventure story from a JSON file.

## Overview

This repo contains a simple story engine and HTTP server:

- `story.go` defines the story data model and HTTP handlers
- `gopher.json` is the default adventure story used by the app
- `cmd/cyoaweb/main.go` starts the web server and loads the story

## Story format

Each chapter in the JSON file has:

- `title`: chapter title
- `story`: an array of paragraphs
- `options`: links to the next chapter

Example:

```json
{
  "intro": {
    "title": "The Little Blue Gopher",
    "story": ["Once upon a time..."],
    "options": [
      { "text": "Go to New York", "arc": "new-york" }
    ]
  }
}
```

## Run the app

```bash
go run ./cmd/cyoaweb --port 3000 --file gopher.json
```

Then open:

```text
http://localhost:3000/story/
```

The app serves the story by chapter path and follows the `arc` values in the JSON to navigate through the adventure.
