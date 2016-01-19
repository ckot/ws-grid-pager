# ws-grid-pager
A workspace pager supporting grid layout for EMWH-compliant X.org window managers

Many minimalistic window managers don't natively support workspaces layed
out as a grid.  This software treats the workspaces as if they actually
are layed out as a grid. Currently, this implemtation requires that the
environment variables: WORKSPACE_ROWS and WORKSPACE_COLUMNS be defined,
although I plan to make this optional if the xprop property _NET_DESKTOP_LAYOUT
is properly set.

Although this is designed/tested (manually) for Fluxbox, it *should* work for
any window manager which is at least minimally EMWH compliant.  Currently, I've
only tested for my own layout 4x3, which is why I have this listed as 'Beta'
software


# Installation
The only dependency is that you have `wmctrl` installed.  I *believe* that
`xprop` will already be present on any X.org system, but if not, you'll need
to install that as well.

`sudo pip install grid-pager`

Depending on your system's configuration, you may be able to drop the `sudo` bit

If you'd rather get the latest from git,

`sudo pip install -e https://github.com/ckot/grid-pager.git`

Alternatively, you can always download a .zip file from the github repo.


# Usage

This package installs 4 command-line programs:
- ws-grid-pager
- gp-switch-workspace
- gp-send-window
- gp-take-window

All 4 programs require a `-d|--direction left|right|up|down` argument as well
as an optional `-w|--wrap` parameter if you'd prefer that left/right from the
first/last column switches to the workspace/sends a window to the last/first
column respectively. The same goes for up/down with the last/first row

The ws-grid-pager program, being generic, also requires the argument:
`-a|--action switch-workspace|send-window|take-window`

A description of the cmd-line arguments will be listed if you run any of the
programs at the cmd-line either without any arguments or with -h|--help

# Suggested Usage with Fluxbox

~/.fluxbox/keys:

    # change to previous/next workspace
    #Control Mod1 Left :PrevWorkspace
    #Control Mod1 Right :NextWorkspace
    Control Mod1 Left        :Exec gp-switch-workspace -d left
    Control Mod1 Right       :Exec gp-switch-workspace -d right
    Control Mod1 Up          :Exec gp-switch-workspace -d up
    Control Mod1 Down        :Exec gp-switch-workspace -d down
    Shift Control Mod1 Left  :Exec gp-switch-workspace -d left   -w
    Shift Control Mod1 Right :Exec gp-switch-workspace -d right  -w
    Shift Control Mod1 Up    :Exec gp-switch-workspace -d up     -w
    Shift Control Mod1 Down  :Exec gp-switch-workspace -d down   -w

    # send the current window to previous/next workspace
    #Mod4 Left  :SendToPrevWorkspace
    #Mod4 Right :SendToNextWorkspace
    Mod4 Left        :Exec gp-send-window -d left
    Mod4 Right       :Exec gp-send-window -d right
    Mod4 Up          :Exec gp-send-window -d up
    Mod4 Down        :Exec gp-send-window -d down
    Shift Mod4 Left  :Exec gp-send-window -d left  -w
    Shift Mod4 Right :Exec gp-send-window -d right -w
    Shift Mod4 Up    :Exec gp-send-window -d up    -w
    Shift Mod4 Down  :Exec gp-send-window -d down  -w

    # send the current window and follow it to previous/next workspace
    #Control Mod4 Left :TakeToPrevWorkspace
    #Control Mod4 Right :TakeToNextWorkspace
    Control Mod4 Left        :Exec gp-take-window -d left
    Control Mod4 Right       :Exec gp-take-window -d right
    Control Mod4 Up          :Exec gp-take-window -d up
    Control Mod4 Down        :Exec gp-take-window -d down
    Shift Control Mod4 Left  :Exec gp-take-window -d left  -w
    Shift Control Mod4 Right :Exec gp-take-window -d right -w
    Shift Control Mod4 Up    :Exec gp-take-window -d up    -w
    Shift Control Mod4 Down  :Exec gp-take-window -d down  -w
