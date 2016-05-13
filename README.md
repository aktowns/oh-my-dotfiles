# Oh my dotfiles

Just a bunch of shell helpers for managing configuration and data across multiple machines

zsh-functions contains two functions for pushing data to/from cloud providers via rclone.  
items are sync'd under a root directory and your current directory with $HOME removed 

```
  /home/ashleyis/Development/projects/bob => root/Development/projects/bob
```

for example

## Pushing files

```
➜  Development $ push
rs: --drive-use-trash --update --filter-from .rclone-filter . cloud:system/Development/
2016/05/14 02:59:57 Google drive root 'system/Development': Not making directory as dry run is set
2016/05/14 02:59:57 Google drive root 'system/Development': Building file list
2016/05/14 03:00:02 Google drive root 'system/Development': Waiting for checks to finish
2016/05/14 03:00:02 Waiting for deletions to finish
2016/05/14 03:00:02 projects/bindings-wlc/src/System/WLC/Types.hs: Not copying as --dry-run
2016/05/14 03:00:02 projects/bindings-wlc/src/Bindings/WLC/Wayland.hsc: Not copying as --dry-run
2016/05/14 03:00:02 projects/bindings-wlc/src/System/WLC/Internal/Types.hs: Not copying as --dry-run
2016/05/14 03:00:02 projects/oh-my-dotfiles/README.md: Not copying as --dry-run
2016/05/14 03:00:02 projects/bindings-wlc/Readme.md: Not copying as --dry-run
2016/05/14 03:00:02 projects/oh-my-dotfiles/zsh-functions: Not copying as --dry-run

Transferred:            0 Bytes (   0.00 kByte/s)
Errors:                 0
Checks:                50
Transferred:           22
Elapsed time:        9.2s

does the above look okay? [y/N]:y
Transferred:        70105 Bytes (   0.95 kByte/s)
Errors:                 0
Checks:                50
Transferred:           22
Elapsed time:     1m12.3s
```

## Pulling files

```
➜  oh-my-dotfiles $ pull
rs: --drive-use-trash --update cloud:system/Development/projects/oh-my-dotfiles/ .
2016/05/14 03:05:01 Local file system at /home/ashleyis/Development/projects/oh-my-dotfiles: Not making directory as dry run is set
2016/05/14 03:05:01 Local file system at /home/ashleyis/Development/projects/oh-my-dotfiles: Building file list
2016/05/14 03:05:03 Local file system at /home/ashleyis/Development/projects/oh-my-dotfiles: Waiting for checks to finish
2016/05/14 03:05:03 testing/Untitled document.docx: Not copying as --dry-run

Transferred:            0 Bytes (   0.00 kByte/s)
Errors:                 0
Checks:                 2
Transferred:            1
Elapsed time:        9.9s

does the above look okay? [y/N]:y
Transferred:         4303 Bytes (   0.96 kByte/s)
Errors:                 0
Checks:                 2
Transferred:            1
Elapsed time:        4.3s

➜  oh-my-dotfiles $ file testing/Untitled\ document.docx
testing/Untitled document.docx: Microsoft Word 2007+
```

