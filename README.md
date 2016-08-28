# backtothefolder

## Summary
backtothefolder, or bttf, allows you to use arrows keys to navigate forward and backward through your path history.

### Example

Say you visit the following directories using cd.
```
~ $> cd ~/Desktop
~/Desktop $> cd /tmp
/tmp $> cd /Applications/
/Applications $>
```

Press "Shift+Alt+Left" to cd into your previous directory:

```/tmp $>```

Press "Shift+Alt+Right" to cd into the directory you visited next:

```/Applications $>```

## Install
Add a line to your .bash_profile or .bashrc to source this script. Here's an example:

```source ~/foo/bar/bttf```

## How it works
Like a browser maintains a history of the pages you've visited, bttf keeps a history of the paths you've visited in the shell variable `$BTTF_HISTORY`. As you can go backward and forward in the browser, you can use keyboard shortcuts to go backward and forward through your path history.

## Supported Bash versions
3.2-4.0
