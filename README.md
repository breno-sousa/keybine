# Keybine

[![](https://img.shields.io/github/release/brensio/keybine)](https://github.com/brensio/keybine/releases)
[![](https://img.shields.io/github/license/brensio/keybine)](https://github.com/brensio/keybine/blob/master/LICENSE)
[![](https://img.shields.io/github/issues/brensio/keybine)](https://github.com/brensio/keybine/issues)
[![](https://img.shields.io/github/forks/brensio/keybine)](https://github.com/brensio/keybine/network/members)
[![](https://img.shields.io/github/stars/brensio/keybine)](https://github.com/brensio/keybine/stargazers)

## Introduction
Keybine is an AutoHotKey script for Windows that provides Vim-like hotkeys. These shortcuts are made by a combination of modifiers and keyboard letters. For example, the script's initial configuration allows one to use the keyboard arrows with the CapsLock modifier and the letters J, I, K, and L, hence eliminating the hassle of moving one's hand to the arrow area of the keyboard.

## Features
Keybine comes with 30 hotkeys by default, however, new hotkeys may be added later. These are categorized into one-modifier (CapsLock) and two-modifier (CapsLock + Alt) commands. 

![keybine-kb-nav-min](https://user-images.githubusercontent.com/45995771/50303713-13b7ad00-0475-11e9-9e6c-22478323e12f.png)

Please note that this script does not process text. All it does is set up shortcuts to keys.  Thus, certain commands may work differently depending on the program. You may adjust each function according to your needs.

### One-modifier Commands
| # | Combination | Function |
| :- | :-: | :- |
| 0 | CapsLock + j | Move left |
| 1 | CapsLock + l | Move right |
| 2 | CapsLock + i | Move up |
| 3 | CapsLock + k | Move down |
| 4 | CapsLock + u | Move to the start of the line |
| 5 | CapsLock + o | Move to the end of the line |
| 6 | CapsLock + c | Copy |
| 7 | CapsLock + v | Paste |
| 8 | CapsLock + x | Cut |
| 9 | CapsLock + n | Move left while selecting |
| 10 | CapsLock + m | Move right while selecting |
| 11 | CapsLock + y | Move a page up |
| 12 | CapsLock + h | Move a page down |
| 13 | CapsLock + BackSpace | Delete the next character |
| 14 | CapsLock + p | Combine the current line with the next line |

### Two-modifier
| # | Combination | Function |
| :- | :-: | :-- |
| 0 | CapsLock + Alt + j | Move left by n words (default: 1) |
| 1 | CapsLock + Alt + l | Move right by n words (default: 1) |
| 2 | CapsLock + Alt + i | Move up by n lines (default: 10) |
| 3 | CapsLock + Alt + k | Move down by n lines (default: 10) |
| 4 | CapsLock + Alt + u | Move to the start of the file |
| 5 | CapsLock + Alt + o | Move to the end of the file |
| 6 | CapsLock + Alt + c | Copy from the current character to the end of the line |
| 7 | CapsLock + Alt + v | Clone the current line in a new line |
| 8 | CapsLock + Alt + x | Cut from the current character to the end of the line |
| 9 | CapsLock + Alt + n | Move left while selecting by n words (default: 1) |
| 10 | CapsLock + Alt + m | Move right while selecting by n words (default: 1) |
| 11 | CapsLock + Alt + y | Move up while selecting |
| 12 | CapsLock + Alt + h | Move down while selecting |
| 13 | CapsLock + Alt + BackSpace | Delete the current line |
| 14 | CapsLock + Alt + p | Replace the current word with the text on clipboard |

## Running the script

To run the script, you must first download [AutoHotKey](https://www.autohotkey.com/).

You can make the script run each time you start the computer. Refer to [AutoHotKey FAQ](https://autohotkey.com/docs/FAQ.htm#Startup) for more information. 

## Modifying hotkeys
On the above tables, search for the number of the hotkey you want to modify. Under the `config` file, look for the line `hotkey[number]` and change its value to adjust the hotkey. You can also change its function by opening the file `navigation.ahk` and editing the content of the block `Hotkey[number]`.

You can also change the modifiers via the `config` file. This can be done by editing the values of `primaryModifier` and `secondaryModifier`. You may add new modifiers as well!

## Creating new hotkeys

Before creating a new hotkey, you should first set the key in the `config` file, for example, `hotkey16=r`. Note that the number **must** follow the sequence.

Then, implement your code in the file `navigation.ahk`, within the condition `#If (CheckActiveWindow())`. It should follow the format:

    Hotkey[number]:
        if GetKeyState(secondaryModifier, ksMode)
            ; two-modifier command
        else
            ; one-modifier command
    return

## Disabling the script

To suspend or restore the script, press `CapsLock + Esc` at any time.

You can prevent hotkeys from executing when certain programs are active. To do this, open the `config` file and add the line `program=[window title]`. For instance: `program=LibreOffice Calc`. Doing so will prevent hotkeys from being triggered when a LibreOffice Calc window is active.

## Changing two-modifier command variables

In the `config` file, you can change two-modifier command variables in the following lines: `linesUp`, `linesDown`, `wordsLeft`, `wordsRight`, `wordsLeftSel`, `wordsRightSel`.

For instance, if you change the value of `wordsRight` to 5 and then execute the hotkey `CapsLock + Alt + l`, you will be able to skip five words ahead.