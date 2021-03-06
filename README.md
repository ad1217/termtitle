termtitle
=========

Sets a custom terminal title.

Settings
--------

The default terminal title format is `%n@%m: %~`, which corresponds to
`username@host: /path/to/working/directory`.

You can set your format using [prompt expansion escape sequences].
The following example sets the format to show the current directory name:

    zstyle ':zim:termtitle' format '%1~'

Apple Terminal does not support the above, but a working directory escape
sequence which is sent instead.

By default, the terminal title is updated before each prompt. The used [hooks]
can be customized with the zstyle below. For example, to have the title updated
when a command is about to be executed and also before each prompt:

    zstyle ':zim:termtitle' hooks 'preexec' 'precmd'

A custom title format can be set for each separate hook using the following
syntax:

    zstyle ':zim:termtitle:<hook>' format '<format>'

For example, to set the title to show the command typed by the user while the
command is being executed and then the current directory name after the command
ended (i.e. before each prompt):

    zstyle ':zim:termtitle' hooks 'preexec' 'precmd'
    zstyle ':zim:termtitle:preexec' format '${1}'
    zstyle ':zim:termtitle:precmd' format '%1~'

[prompt expansion escape sequences]: http://zsh.sourceforge.net/Doc/Release/Prompt-Expansion.html#Simple-Prompt-Escapes
[hooks]: http://zsh.sourceforge.net/Doc/Release/Functions.html#Hook-Functions
