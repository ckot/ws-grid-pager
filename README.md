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

To use with Fluxbox, I suggest the following changes to your ~/.fluxbox/keys
file:



