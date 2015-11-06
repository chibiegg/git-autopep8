#!/usr/bin/env python
from __future__ import with_statement, print_function
import os
import re
import shutil
import subprocess
import sys
import tempfile

# don't fill in both of these
select_codes = []
ignore_codes = ["E121", "E122", "E123", "E124", "E125", "E126", "E127", "E128", "E129", "E131", "E501"]
# Add things like "--max-line-length=120" below
overrides = ["--max-line-length=120"]


def system(*args, **kwargs):
    kwargs.setdefault('stdout', subprocess.PIPE)
    proc = subprocess.Popen(args, **kwargs)
    out, err = proc.communicate()
    return out


def autopep8(filepath):
    args = ['autopep8', '--in-place']
    if select_codes and ignore_codes:
        print(u'Error: select and ignore codes are mutually exclusive')
        sys.exit(1)
    elif select_codes:
        args.extend(('--select', ','.join(select_codes)))
    elif ignore_codes:
        args.extend(('--ignore', ','.join(ignore_codes)))
    args.extend(overrides)
    args.append(filepath)
    output = system(*args)


def main():
    try:
        import autopep8 as ap8
    except ImportError:
        print("'autopep8' is required. Please install with `pip install autopep8`.", file=sys.stderr)
        exit(1)

    modified = re.compile('^[AM]+\s+(?P<name>.*\.py)', re.MULTILINE)
    basedir = system('git', 'rev-parse', '--show-toplevel').decode("utf-8").strip()
    files = system('git', 'status', '--porcelain').decode("utf-8")
    files = modified.findall(files)

    for name in files:
        filepath = os.path.join(basedir, name)
        autopep8(filepath)
        system("git", "add", filepath)


if __name__ == '__main__':
    main()
