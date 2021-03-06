# action-youtrack-move

> Action for moving cards between YouTrack board columns.

Works by doing the following:

1. Find all the tickets on the pull request description.
2. Move those tickets to the desired column.
3. Comment the tickets on YouTrack with the related PR.

Goes well in combination with [action-youtrack-sync](https://github.com/bloobirds-it/action-youtrack-sync).

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
          github-token: ${{ secrets.GITHUB_TOKEN }}
          yt-url: ${{ secrets.YOUTRACK_URL }}
          yt-token: ${{ secrets.YOUTRACK_TOKEN }}
          yt-project-id: "BB"
```

In this example when the PR is closed the tickets starting with _BB_ will be moved from _PR Open_ towards _PreProd_.

## Inputs

#### `github-token`

Usual GitHub token, one is available by default as `${{ secrets.GITHUB_TOKEN }}`.

- **Required:** Yes

#### `yt-url`

Base URL of your YouTrack instance.

- **Required:** Yes
- **Default:** "https://my-yt.myjetbrains.com/youtrack"

#### `yt-token`

YouTrack generated permanent token. For more info on [how to generate](https://www.jetbrains.com/help/youtrack/standalone/Manage-Permanent-Token.html).

- **Required:** Yes

#### `yt-project-id`

Issue ID prefix used in the projects. Basically the letters before your tickets.

- **Required:** Yes

#### `yt-column-field`

Name of the field which represents the ticket state.

- **Required:** No
- **Default:** "Stage"

#### `yt-column-triggers`

From which columns is the card allowed to move to the target.

- **Required:** No
- **Default:** "To Do, To Fix, In Progress"

#### `yt-column-target`

To which column should the related tickets be moved.

- **Required:** No
- **Default:** "PreProd"

## License

The scripts and documentation in this project are released under the MIT License
