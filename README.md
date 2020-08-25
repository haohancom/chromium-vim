# [Like cVim? Consider donating! https://www.paypal.me/1995eaton](https://www.paypal.me/1995eaton)

# What is cVim?

Vim for Google Chrome. I hate using the mouse, especially after learning Vim. With my desktop (Linux), I have a lot of key bindings that make doing things easier: I open Chrome with `Alt+w`, I close a window with `Alt+Shift+d`, I open a terminal with `Alt+t`. This is harder to do with Chrome because it has no section for customizing keyboard shortcuts, and it is still necessary to use the mouse to do things like click links. cVim aims to eliminate this problem as best as the Chrome extensions API will allow it to.

# Where can I get cVim?

 * There are two ways:
  * You can install it through the [Chrome web store](https://chrome.google.com/webstore/detail/cvim/ihlenndgcmojhcghmfjfneahoeklbjjh)
  * You can download the `.zip` file [here](https://github.com/1995eaton/chromium-vim/archive/master.zip) and enable cVim by going to the `chrome://extensions` URL and checking developer mode, then pointing Chrome to the unzipped folder via the `Load unpacked extensions...` button.

# Why is this different than Vimium, ViChrome, or Vrome?

These extensions do a wonderful job of adding Vim-like keybindings to Google Chrome, but they lack many of the features that Firefox Addon, Pentadactyl, have.

 * What features does cVim add to Chrome?
  * Google/IMDB/Wikipedia/Amazon/Duckduckgo/Yahoo/Bing search completion
  * Support for custom search engines
  * History and Bookmark search/completion with bookmark folder support
  * Caret/Visual mode
  * Efficient link hints (with support for custom mappings)
  * Support for custom keyboard mappings
  * Regex page search with highlighting
  * Command bar with tab-completion
  * Smooth scrolling

# cVim Help
### cVimrc

 * Boolean cVimrc settings are enabled with the command ```'set' + <SETTING_NAME>``` and disabled with
   the command ```'set' + no<SETTING_NAME>``` (for example, ```set regexp``` and ```set noregexp```)
 * Boolean cVimrc settings can be inversed by adding "!" to the end
 * Other settings are defined with ```=``` used as a separator and are prefixed by ```let``` (for example, ```let hintcharacters="abc"```)

| setting                             | type                               | description                                                                               | default                                                                     |
| ----------------------------------- | ---------------------------------- | ----------------------------------------------------------------------------------------- | --------------------------------------------------------------------------: |
| searchlimit                         | integer                            | set the amount of results displayed in the command bar                                    | 25                                                                          |
| scrollstep                          | integer                            | set the amount of pixels scrolled when using the scrollUp and scrollDown commands         | 70                                                                          |
| timeoutlen                          | integer                            | The amount of time to wait for a `<Leader>` mapping in milliseconds                       | 1000                                                                        |
| fullpagescrollpercent               | integer                            | set the percent of the page to be scrolled by when using the scrollFullPageUp and scrollFullPageDown commands | 0                                                       |
| typelinkhintsdelay                  | integer                            | the amount of time (in milliseconds) to wait before taking input after opening a link hint with typelinkhints and numerichints enabled | 300                            |
| scrollduration                      | integer                            | the duration of smooth scrolling                                                          | 500                                                                         |
| vimport                             | integer                            | set the port to be used with the `editWithVim` insert mode command                        | 8001                                                                        |
| zoomfactor                          | integer / double                   | the step size when zooming the page in/out                                                | 0.1                                                                         |
| scalehints                          | boolean                            | animate link hints as they appear                                                         | false                                                                       |
| hud                                 | boolean                            | show the heads-up-display                                                                 | true                                                                        |
| regexp                              | boolean                            | use regexp in find mode                                                                   | true                                                                        |
| ignorecase                          | boolean                            | ignore search case in find mode                                                           | true                                                                        |
| linkanimations                      | boolean                            | show fade effect when link hints open and close                                           | false                                                                       |
| numerichints                        | boolean                            | use numbers for link hints instead of a set of characters                                 | false                                                                       |
| dimhintcharacters                   | boolean                            | dim letter matches in hint characters rather than remove them from the hint               | true                                                                        |
| defaultnewtabpage                   | boolean                            | use the default chrome://newtab page instead of a blank page                              | false                                                                       |
| cncpcompletion                      | boolean                            | use `<C-n>` and `<C-p>` to cycle through completion results (requires you to set the nextCompletionResult keybinding in the chrome://extensions page (bottom right) | false |
| smartcase                           | boolean                            | case-insensitive find mode searches except when input contains a capital letter           | true                                                                        |
| incsearch                           | boolean                            | begin auto-highlighting find mode matches when input length is greater thant two characters | true                                                                      |
| typelinkhints                       | boolean                            | (numerichints required) type text in the link to narrow down numeric hints                | false                                                                       |
| autohidecursor                      | boolean                            | hide the mouse cursor when scrolling (useful for Linux, which doesn't auto-hide the cursor on keydown) | false                                                          |
| autofocus                           | boolean                            | allows websites to automatically focus an input box when they are first loaded            | true                                                                        |
| insertmappings                      | boolean                            | use insert mappings to navigate the cursor in text boxes (see bindings below)             | true                                                                        |
| smoothscroll                        | boolean                            | use smooth scrolling                                                                      | false                                                                       |
| autoupdategist                      | boolean                            | if a GitHub Gist is used to sync settings, pull updates every hour (and when Chrome restarts)   | false                                                                 |
| nativelinkorder                     | boolean                            | Open new tabs like Chrome does rather than next to the currently opened tab               | false                                                                       |
| showtabindices                      | boolean                            | Display the tab index in the tab's title                                                  | false                                                                       |
| sortlinkhints                       | boolean                            | Sort link hint lettering by the link's distance from the top-left corner of the page      | false                                                                       |
| localconfig                         | boolean                            | Read the cVimrc config from `configpath` (when this is set, you connot save from cVim's options page | false                                                            |
| completeonopen                      | boolean                            | Automatically show a list of command completions when the command bar is opened           | false                                                                       |
| configpath                          | string                             | Read the cVimrc from this local file when configpath is set                               | ""                                                                          |
| changelog                           | boolean                            | Auto open the changelog when cVim is updated                                              | true                                                                        |
| completionengines                   | array of strings                   | use only the specified search engines                                                     | ["google", "duckduckgo", "wikipedia", "amazon"]                             |
| blacklists                          | array of strings                   | disable cVim on the sites matching one of the patterns                                    | []                                                                          |
| mapleader                           | string                             | The default `<Leader>` key                                                                | \                                                                           |
| defaultengine                       | string                             | set the default search engine                                                             | "google"                                                                    |
| locale                              | string                             | set the locale of the site being completed/searched on (see example configuration below)  | ""                                                                          |
| homedirectory                       | string                             | the directory to replace `~` when using the `file` command                                | ""                                                                          |
| qmark &lt;alphanumeric charcter&gt; | string                             | add a persistent QuickMark (e.g. ```let qmark a = ["http://google.com", "http://reddit.com"]```) | none                                                                 |
| previousmatchpattern                | string (regexp)                    | the pattern looked for when navigating a page's back button                               | ((?!last)(prev(ious)?&#124;newer&#124;back&#124;«&#124;less&#124;&lt;&#124;‹&#124; )+) |
| nextmatchpattern                    | string (regexp)                    | the pattern looked for when navigation a page's next button                               | ((?!first)(next&#124;older&#124;more&#124;&gt;&#124;›&#124;»&#124;forward&#124; )+)    |
| hintcharacters                      | string (alphanumeric)              | set the default characters to be used in link hint mode                                   | "asdfgqwertzxcvb"                                                           |
| barposition                         | string ["top", "bottom"]           | set the default position of the command bar                                               | "top"                                                                       |
| langmap                             | string                             | set a list of characters to be remapped (see vims langmap)                                | ""                                                                          |

### Example configuration
```vim
" Settings
set nohud
set nosmoothscroll
set noautofocus " The opposite of autofocus; this setting stops
                " sites from focusing on an input box when they load
set typelinkhints
let searchlimit = 30
let scrollstep = 70
let barposition = "bottom"

let locale = "uk" " Current choices are 'jp' and 'uk'. This allows cVim to use sites like google.co.uk
                  " or google.co.jp to search rather than google.com. Support is currently limited.
                  " Let me know if you need a different locale for one of the completion/search engines
let hintcharacters = "abc123"

let searchengine dogpile = "http://www.dogpile.com/search/web?q=%s" " If you leave out the '%s' at the end of the URL,
                                                                    " your query will be appended to the link.
                                                                    " Otherwise, your query will replace the '%s'.

" This will do the same thing as above, except typing ':tabnew withbase' into to command bar
" without any search parameters will open 'http://www.dogpile.com'
let searchengine withbase = ["http://www.dogpile.com", "http://www.dogpile.com/search/web?q=%s"]

" alias ':g' to ':tabnew google'
command g tabnew google

let completionengines = ["google", "amazon", "imdb", "dogpile"]

let searchalias g = "google" " Create a shortcut for search engines.
                             " For example, typing ':tabnew g example'
                             " would act the same way as ':tabnew google example'

" Open all of these in a tab with `gnb` or open one of these with <N>goa where <N>
let qmark a = ["http://www.reddit.com", "http://www.google.com", "http://twitter.com"]

let blacklists = ["https://mail.google.com/*", "*://mail.google.com/*", "@https://mail.google.com/mail/*"]
" blacklists prefixed by '@' act as a whitelist

let mapleader = ","

" Mappings

" This remaps the default 'j' mapping
map j scrollUp

" This unmaps the default 'k' mapping
unmap k

" This unmaps the default 'h', 'j', 'k', and 'l' mappings
unmap h j k l

" This remaps the default 'j' mapping to the current 'k' mapping
map j k



" Code blocks (see below for more info)
getIP() -> {{
httpRequest({url: 'http://api.ipify.org/?format=json', json: true},
            function(res) { Status.setMessage('IP: ' + res.ip); });
}}
" Displays your public IP address in the status bar
map ci :call getIP<CR>

" Script hints
echo(link) -> {{
  alert(link.href);
}}
map <C-f> createScriptHint(echo)

let configpath = '/path/to/your/.cvimrc'
set localconfig " Update settings via a local file (and the `:source` command) rather
                " than the default options page in chrome
" As long as localconfig is set in the .cvimrc file. cVim will continue to read
" settings from there
```

### Blacklists
 * The blacklists setting uses a custom inplementation of Chrome's @match pattern guidelines.
   See https://developer.chrome.com/extensions/match_patterns for a description of the syntax.


### Site-specific Configuration
 * You can enable certain rc settings for sites using the blacklist match pattern as described above
```vim
" this will enable the config block below on the domain 'reddit.com'
site '*://*.reddit.com/*' {
      unmap j
      unmap k
      set numerichints
}
```

### Running commands when a page loads
 * In a similar fashion to the site-specific configuration described above, cVim can run commands when a page is loaded with the `call` keyword
```vim
" In this case, when pages with a file ending in '.js' are loaded,
" cVim will pin the tab and then scroll down
site '*://*/*.js' {
      call :pintab
      call scrollDown
}
```

### Mappings
 * Normal mappings are defined with the following structure: ```map <KEY> <MAPPING_NAME>```
 * Insert mappings use the same structure, but use the command "imap" instead of "map"
 * Control, meta, and alt can be used also:
```vim
<C-u> " Ctrl + u
<M-u> " Meta + u
<A-u> " Alt  + u
```
 * It is also possible to unmap default bindings with ```unmap <KEY>``` and insert bindings with ```iunmap <KEY>```
 * To unmap all default keybindings, use ```unmapAll```. To unmap all default insert bindings, use ```iunmapAll```

### Tabs
 * Commands that open links (`:tabnew` and `:open`) have three different properties
  * `!` => Open in a new tab
  * `$` => Open in a new window
  * `|` => Open in an incognito window
  * `&` => Open in a new tab (inactive/unfocused)
  * `*` => Pin the tab
  * `?` => Treat the query as a search
  * `=` => Treat the query as a URL
 * The use of these properties are best explained with examples:

```vim
:open! google<CR> " This is the same as :tabnew google<CR>

:open google!<CR> " This is another way of writing the above
                  " (these flags can can be added to either
                  " the base command or the end of the final command)

:open& google<CR> " This will open Google in a new inactive tab

:open$ google<CR> " This will open Google in a new window

:open&* google<CR> " The will open Google in a new inactive, pinned tab

:tabnew google&*<CR> " Once again, this will do the same thing as the above command

:open google&*<CR> " Again, same as above

:open google!& " Here, the & flag will cancel out the ! flag,
               " opening Google in a new inactive tab

" More examples
:bookmarks my_bookmark.com&  " inactive,new tab
:bookmarks&* my_bookmark.com " inactive,pinned,new tab
:bookmarks! my_bookmark.com  " new tab
:bookmarks$ my_bookmark.com  " new window
:bookmarks my_bookmark.com   " same tab
```

### Code blocks
 * Code blocks allow you to interact with cVim's content scripts via the cVimrc.
 * Since code blocks use `eval(...)`, you should only use them if you know what you're doing.

```JavaScript
" To be used by the code block
set hintset_a

" Create a code block named switchHintCharacters
switchHintCharacters -> {{
  // We are now in JavaScript mode

  // Settings are contained in an object named settings
  settings.hintset_a = !settings.hintset_a;
  if (settings.hintset_a) {
    settings.hintcharacters = 'abc'; // equivalent to "let hintcharacters = 'abc'"
  } else {
    settings.hintcharacters = 'xyz';
  }

  // Propagate the current settings to all tabs for the
  // rest of the session
  PORT('syncSettings', { settings: settings });

  // Display cVim's status bar for 2 seconds.
  Status.setMessage('Hint Set: ' + (true ? 'a' : 'b'), 2);
}}

" Run the JavaScript block
map <Tab> :call switchHintCharacters<CR>
```

### Completion Engines
  * These are a list of completion engines that can be used in the command bar. They can be set
    by assigning their names to an array with the `completionengines` variable.
    * google, wikipedia, youtube, imdb, amazon, google-maps, wolframalpha, google-image, ebay,
      webster, wictionary, urbandictionary, duckduckgo, answers, google-trends, google-finance,
      yahoo, bing, themoviedb
  * Example usage:
```vim
let completionengines = ['google', 'google-image', 'youtube'] " Show only these engines in the command bar
```


# Keybindings

| Movement                  |                                                                       | Mapping name                    |
| ------------------------- | :-------------------------------------------------------------------- | :------------------------------ |
| `j`                       | scroll down                                                           | scrollDown                      |
| `k`                       | scroll up                                                             | scrollUp                        |
| `h`                       | scroll left                                                           | scrollLeft                      |
| `l`                       | scroll right                                                          | scrollRight                     |
| `d`                       | scroll half-page down                                                 | scrollPageDown                  |
| `u`                       | scroll half-page up                                                   | scrollPageUp                    |
| `gg`                      | scroll to the top of the page                                         | scrollToTop                     |
| `G`                       | scroll to the bottom of the page                                      | scrollToBottom                  |
| `X`                       | open the last closed tab                                              | lastClosedTab                   |


# Tips

 * You can use `@%` in "open" commands to specify the current URL.
   For example, `:open @%` would essentially refresh the current page.
 * Prepend a number to the command to repeat that command N times
 * Use the up/down arrows in command/find mode to navigate through previously
   executed commands/searches -- you can also use this to search for previously
   executed commands starting with a certain combination of letters (for example,
   entering `ta` in the command bar and pressing the up arrow will search command
   history for all matches beginning with `ta`

# Contributing

Nice that you want to spend some time improving this extension.
Solving issues is always appreciated. If you're going to add a feature,
it would be best to [submit an issue](https://github.com/1995eaton/chromium-vim/issues).
You'll get feedback whether it will likely be merged.

1. Run `npm install` in the repository's root folder
1. Run `make`
1. Navigate to `chrome://extensions`
1. Toggle into Developer Mode
1. Click on "Load Unpacked Extension..."
1. Select the cVim directory.
