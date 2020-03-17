# action-youtrack-move

Action for moving cards between YouTrack boards.

## Usage

Basic example with default options for a project where tickets look like _BB-123_.

```yaml
name: YouTrack Issue Move

on:
  pull_request:
    types: [closed]

jobs:
  sync:
    runs-on: ubuntu-latest
    steps:
      - uses: bloobirds-it/action-youtrack-move@v1.0.0
        with:
          githubToken: ${{ secrets.GITHUB_TOKEN }}
          youtrackUrl: ${{ secrets.YOUTRACK_URL }}
          youtrackToken: ${{ secrets.YOUTRACK_TOKEN }}
          youtrackProjectID: "BB"
```

## Parameters

#### `githubToken`

Your usual GitHub token, one is available by default as `${{ secrets.GITHUB_TOKEN }}`.

- **Required:** Yes

#### `youtrackUrl`

Base URL of your YouTrack instance.

- **Required:** Yes
- **Default:** "https://my-yt.myjetbrains.com/youtrack"

#### `youtrackToken`

YouTrack generated permanent token. For more info on [how to generate](https://www.jetbrains.com/help/youtrack/standalone/Manage-Permanent-Token.html).

- **Required:** Yes

#### `youtrackProjectId`

Issue ID prefix used in the projects. Basically the letters before your tickets.

- **Required:** Yes

#### `youtrackColumnField`

Name of the field which represents the ticket state.

- **Required:** No
- **Default:** "Stage"

#### `youtrackColumnTriggers`

Which columns will trigger the action. In other words, from which columns is the card allowed move to the target.

- **Required:** No
- **Default:** "To Do, To Fix, In Progress"

#### `youtrackColumnTarget`

To which column should the related tickets be moved.

- **Required:** No
- **Default:** "PR Open"

## License

The scripts and documentation in this project are released under the MIT License
