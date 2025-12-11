# How to use ``` git restore ``` command ?

## 1. Restore a file in the working directory
```bash
git restore <file>
```
**Usage** : Discards changes in the working directory and restores the file to the last committed state.

## 2. Restore all files in the working directory

```bash
git restore .
```
**Usage** : Discards changes in all files and resets them to the last commit.


## 3. Unstage a file (remove from staging area)

```bash
git restore --staged <file>
```
**Usage** : Removes the file from the staging area but keeps local changes in the working directory.


## 4. Restore a file from a specific commit

```bash
git restore --source <commit-hash> <file>
```
**Usage** : Replaces the file with the version from the specified commit.


## 5. Restore and unstage a file at the same time

```bash
git restore --source <commit-hash> --staged <file>
```
**Usage** : Restores the file from a specific commit and removes it from staging.


### Notes

- git restore only affects uncommitted changes.
- Use --staged to unstage without losing edits.
 - Use --source to restore from any previous commit.
