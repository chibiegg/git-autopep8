autopep8 Git Commit Hook
====================

Installation:

1. ```$ cd your_project```
2. Install the autopep8 program: ```$ pip install autopep8```
3. Save pre-commit with ```$ wget https://raw.githubusercontent.com/chibiegg/git-autopep8/master/pre-commit -O .git/hooks/pre-commit```
4. Mark pre-commit executable: ```$ chmod +x .git/hooks/pre-commit```

In case you want to modify the list of codes to ignore, edit the
```ignore_codes``` list in the pre-commit file.   
If you want to select only specific codes to scan for, use the
```select_codes``` list.
Additional arguments to the pep8 program (e.g., ```--max-line-length=120```) can be added to the ```overrides``` list.

This code was forked from [https://gist.github.com/810399](https://gist.github.com/810399) and [https://github.com/cbrueffer/pep8-git-hook](https://github.com/cbrueffer/pep8-git-hook).

This software is released under the MIT License, see LICENSE.txt.
