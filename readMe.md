# lscontent

- TreeList und Dateiinhalte auflisten

## Ausführung

- python3 lscontent.py [optional Path, anonsten current path]

## Global Ausführbar

- lscontent nach /usr/local/bin/lscontent verschieben
- chmod +x /usr/local/bin/lscontent

## Output

```
$ lscontent
Verzeichnisbaum:
├── lscontent.py
├── readMe.md
└── lscontent

Datei-Inhalte:

./lscontent.py:
----------------------------------------
#!/usr/bin/env python3

import os
import sys

def list_directory_tree_and_files(start_path='.'):
    # Funktion, um den Verzeichnisbaum auszugeben
    def print_tree(directory, prefix=''):
        try:
            items = [item for item in os.listdir(directory) if item != '.git']
        except Exception as e:
            print(f"{prefix}Fehler beim Lesen von {directory}: {e}")
            return

        for count, item in enumerate(items):
            path = os.path.join(directory, item)
            is_last = (count == len(items) - 1)
            connector = '└── ' if is_last else '├── '
            print(f"{prefix}{connector}{item}")
            if os.path.isdir(path):
                extension = '    ' if is_last else '│   '
                print_tree(path, prefix=prefix + extension)

    # Funktion, um die Dateien aufzulisten und ihren Inhalt auszugeben
    def print_file_contents(directory):
        for root, dirs, files in os.walk(directory):
            # .git-Ordner ausschließen
            if '.git' in dirs:
                dirs.remove('.git')
            for file in files:
                file_path = os.path.join(root, file)
                print(f"\n{file_path}:\n{'-' * 40}")
                try:
                    with open(file_path, 'r', encoding='utf-8') as f:
                        print(f.read())
                except Exception as e:
                    print(f"Fehler beim Lesen der Datei {file_path}: {e}")

    print("Verzeichnisbaum:")
    print_tree(start_path)
    print("\nDatei-Inhalte:")
    print_file_contents(start_path)

# Funktion starten
if __name__ == '__main__':
    start_path = sys.argv[1] if len(sys.argv) > 1 else '.'
    list_directory_tree_and_files(start_path)

./readMe.md:
----------------------------------------
# lscontent

- TreeList und Dateiinhalte auflisten

## Ausführung

- python3 lscontent.py [optional Path, anonsten current path]

## Output

```

```


./lscontent:
----------------------------------------
#!/usr/bin/env python3

import os
import sys

def list_directory_tree_and_files(start_path='.'):
    # Funktion, um den Verzeichnisbaum auszugeben
    def print_tree(directory, prefix=''):
        try:
            items = [item for item in os.listdir(directory) if item != '.git']
        except Exception as e:
            print(f"{prefix}Fehler beim Lesen von {directory}: {e}")
            return

        for count, item in enumerate(items):
            path = os.path.join(directory, item)
            is_last = (count == len(items) - 1)
            connector = '└── ' if is_last else '├── '
            print(f"{prefix}{connector}{item}")
            if os.path.isdir(path):
                extension = '    ' if is_last else '│   '
                print_tree(path, prefix=prefix + extension)

    # Funktion, um die Dateien aufzulisten und ihren Inhalt auszugeben
    def print_file_contents(directory):
        for root, dirs, files in os.walk(directory):
            # .git-Ordner ausschließen
            if '.git' in dirs:
                dirs.remove('.git')
            for file in files:
                file_path = os.path.join(root, file)
                print(f"\n{file_path}:\n{'-' * 40}")
                try:
                    with open(file_path, 'r', encoding='utf-8') as f:
                        print(f.read())
                except Exception as e:
                    print(f"Fehler beim Lesen der Datei {file_path}: {e}")

    print("Verzeichnisbaum:")
    print_tree(start_path)
    print("\nDatei-Inhalte:")
    print_file_contents(start_path)

# Funktion starten
if __name__ == '__main__':
    start_path = sys.argv[1] if len(sys.argv) > 1 else '.'
    list_directory_tree_and_files(start_path)
```
