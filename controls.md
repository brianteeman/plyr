# Controls HTML

This is the markup that is rendered for the Plyr controls. You can use the default controls or provide a customized version of markup based on your needs. 

The demo Plyr setup uses a Hogan template. This purely to allow for localization at a later date. Check out `controls.html` in `/src/templates` to get an idea of how the default html is structured.

## Requirements

The classes and data attributes used in your template should match the `selectors` option. 

You need to add several placeholders to your html template that are replaced when rendering:

- `{id}` - the dynamically generated ID for the player (for form controls)
- `{seektime}` - the seek time specified in options for fast forward and rewind

You can include only the controls you need when specifying custom html. 

## Example

This is an example `html` option with all controls.

```javascript
["<div class='player-controls'>",
    "<div class='player-progress'>",
        "<label for='seek{id}' class='sr-only'>Seek</label>",
        "<input id='seek{id}' class='player-progress-seek' type='range' min='0' max='100' step='0.5' value='0' data-player='seek'>",
        "<progress class='player-progress-played' max='100' value='0'>",
            "<span>0</span>% played",
        "</progress>",
        "<progress class='player-progress-buffer' max='100' value='0'>",
            "<span>0</span>% buffered",
        "</progress>",
    "</div>",
    "<span class='player-controls-left'>",
        "<button type='button' data-player='restart'>",
            "<svg><use xlink:href='#icon-restart'></use></svg>",
            "<span class='sr-only'>Restart</span>",
        "</button>",
        "<button type='button' data-player='rewind'>",
            "<svg><use xlink:href='#icon-rewind'></use></svg>",
            "<span class='sr-only'>Rewind {seektime} secs</span>",
        "</button>",
        "<button type='button' data-player='play'>",
            "<svg><use xlink:href='#icon-play'></use></svg>",
            "<span class='sr-only'>Play</span>",
        "</button>",
        "<button type='button' data-player='pause'>",
            "<svg><use xlink:href='#icon-pause'></use></svg>",
            "<span class='sr-only'>Pause</span>",
        "</button>",
        "<button type='button' data-player='fast-forward'>",
            "<svg><use xlink:href='#icon-fast-forward'></use></svg>",
            "<span class='sr-only'>Forward {seektime} secs</span>",
        "</button>",
        "<span class='player-time'>",
            "<span class='sr-only'>Current time</span>",
            "<span class='player-current-time'>00:00</span>",
        "</span>",
        "<span class='player-time'>",
            "<span class='sr-only'>Duration</span>",
            "<span class='player-duration'>00:00</span>",
        "</span>",
    "</span>",
    "<span class='player-controls-right'>",
        "<input class='inverted sr-only' id='mute{id}' type='checkbox' data-player='mute'>",
        "<label id='mute{id}' for='mute{id}'>",
            "<svg class='icon-muted'><use xlink:href='#icon-muted'></use></svg>",
            "<svg><use xlink:href='#icon-volume'></use></svg>",
            "<span class='sr-only'>Toggle Mute</span>",
        "</label>",
        "<label for='volume{id}' class='sr-only'>Volume</label>",
        "<input id='volume{id}' class='player-volume' type='range' min='0' max='10' value='5' data-player='volume'>",
        "<input class='sr-only' id='captions{id}' type='checkbox' data-player='captions'>",
        "<label for='captions{id}'>",
            "<svg class='icon-captions-on'><use xlink:href='#icon-captions-on'></use></svg>",
            "<svg><use xlink:href='#icon-captions-off'></use></svg>",
            "<span class='sr-only'>Toggle Captions</span>",
        "</label>",
        "<button type='button' data-player='fullscreen'>",
            "<svg class='icon-exit-fullscreen'><use xlink:href='#icon-exit-fullscreen'></use></svg>",
            "<svg><use xlink:href='#icon-enter-fullscreen'></use></svg>",
            "<span class='sr-only'>Toggle Fullscreen</span>",
        "</button>",
    "</span>",
"</div>"].join("\n");
```