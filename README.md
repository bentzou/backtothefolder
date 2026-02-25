# bttf

Browser-style back/forward navigation for your terminal.

```
~ $> cd ~/Desktop
~/Desktop $> cd /tmp
/tmp $> cd /Applications
/Applications $> # press Shift+Alt+Left
/tmp $> # press Shift+Alt+Left
~/Desktop $> # press Shift+Alt+Right
/tmp $>
```

Like a browser keeps a history of pages you've visited, bttf keeps a history of directories. Go back with `cdl`, go forward with `cdr`.

## Install

Source the script from your `.bashrc` or `.bash_profile`:

```bash
source ~/path/to/bttf
```

## How it works

bttf hooks into `PROMPT_COMMAND` to record your working directory after every prompt. Directories are stored in the `BTTF_HISTORY` array, with index 0 tracking your current position. `cdl` and `cdr` decrement and increment that position and `cd` to the corresponding path.

Under the hood, two readline bindings map Shift+Alt+Arrow to the shell functions `cdl` (back) and `cdr` (forward).

You can also view your full history with `bttf_history` and jump to any entry with `bttf`:

```
~ $> bttf_history
  1: /Users/you
  2: /Users/you/Desktop
  3: /tmp
  4: /Applications

~ $> bttf 3
/tmp $>
```

## Configuration

**History size** defaults to 100 entries. Change it before sourcing:

```bash
BTTF_HISTORY_SIZE=50
source ~/path/to/bttf
```

**Duplicate removal** is on by default — revisiting a directory moves it to the end of the history rather than creating a second entry. To allow duplicates:

```bash
BTTF_NO_DUPLICATES=false
```

**Key sequences** default to Shift+Alt+Arrow (`\e[1;10D` / `\e[1;10C`). If your terminal sends something different, override them before sourcing:

```bash
CD_LEFT_KEY_SEQUENCE='\e[1;10D'
CD_RIGHT_KEY_SEQUENCE='\e[1;10C'
source ~/path/to/bttf
```

## Tests

```bash
bash bttf_test
```

## Supported Bash versions

3.2–4.0
