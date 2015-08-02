# Prebase

*git-prebase* improves on 'git rebase -i' by adding information per commit regarding which files it touched.
- Each file gets an alpha-numeric identifier at a particular column, a list of which appears below the commit list. (The identifiers wrap around after the 62nd file)
- Commits can be moved up and down safely (without conflicts) as long as their columns don't clash (they did not touch the same file).


# Installation

Add the executable to your path and git will automatically expose it as

    git prebase <commit-ref>

The flow is exactly like an interactive rebase, only that the 'todo' list will now contain the additional information.


# Example

Below is an example of the 'todo' list created by git-prebase.

```
pick d0d13d0    1:removed some bullshit from __entrypoint.d      _________9______
pick a44e878    2:Improvements to object.d and __entrypoint.d    ________89______
pick 12c5b47    3:Add usage to build.d                           ___3____________
pick 318af43    4:Added .gitignore                               ______________e_
pick eb9ad0f    5:Attempting to add more array support           _1_3_56_89abcd__
pick 8b8df05    6:Added some special support for ldc to object.d ________8_______
pick e630300    7:Removed imports from build                     ___3____________
pick 69ae673    8:c-main to d-main                               __2345_7_9______
pick c00b344    9:Implemented write an exit system calls         _1_345678_______
pick 3901cca   10:Add wscript_build file                         0__3____________
pick 349bec4   11:WAF: fix build script                          0_______________
pick 70e1d26   12:Make main module qualified                     __2_____________
pick f22cca0   13:Update to 2.067                                _1______________
pick 06cb727   14:revert to compiling under 2.066                01______________
pick 25c13c4   15:WAF: remove unneeded post()s                   0_______________

# [0] wscript_build                                              0_______________
# [1] ports/posix.d                                              _1______________
# [2] app/main.d                                                 __2_____________
# [3] build.d                                                    ___3____________
# [4] include/__entrypoint.di                                    ____4___________
# [5] ports/linux.d                                              _____5__________
# [6] source/array.d                                             ______6_________
# [7] source/dmain.d                                             _______7________
# [8] source/object.d                                            ________8_______
# [9] source/__entrypoint.d                                      _________9______
# [a] ports/windows.d                                            __________a_____
# [b] source/ports/linux.d                                       ___________b____
# [c] source/ports/posix.d                                       ____________c___
# [d] source/ports/windows.d                                     _____________d__
# [e] .gitignore                                                 ______________e_

# Rebase 9c75315..25c13c4 onto 9c75315
#
# Commands:
#  p, pick = use commit
#  r, reword = use commit, but edit the commit message
#  e, edit = use commit, but stop for amending
#  s, squash = use commit, but meld into previous commit
#  f, fixup = like "squash", but discard this commit's log message
#  x, exec = run command (the rest of the line) using shell
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out
```
