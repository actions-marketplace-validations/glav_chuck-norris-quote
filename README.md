# Chuck Norris quote action
A github action to output a random chuck norris quote within a wokflow. Supports text, markdown or html output.

# Usage
## A sample workflow to output a quote to the logs
### Inputs
* quote-format : html or text(default) - Format to return the quote in.
* encode-quote : true or false(default) - Whether the quote should be URI encoded or not.
```
name: Chuck Norris test workflow

on:
  workflow_dispatch:

jobs:
  action:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v1

      - name: chuck-norris-quote-action
        uses: ./.github/actions/chuck-norris-quote
```

## A sample workflow to specify markdown output and use it in a subsequent step
```
name: Chuck Norris test workflow markdown

on:
  workflow_dispatch:

jobs:
  action:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v1

      - name: chuck-norris-quote-action-markdown
        id: htmlchuck
        uses: ./.github/actions/chuck-norris-quote
        with:
          quote-format: 'html'
          encode-quote: 'true'

      - name: ShowMarkdownOutput
        run: echo "${{ steps.htmlchuck.outputs.quote }}"
```
## Building this action
Note: To build, you will need to install NCC and build the main.js file into the dist/index.js folder/file.

### Install ncc globally
```npm install -g @zeit/ncc```
### Using ncc
When you use ncc:

```ncc build main.js```


