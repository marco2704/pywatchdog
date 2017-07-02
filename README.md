# Pywatchdog
**Inotify** is a Linux kernel subsystem that provides a mechanism for monitoring filesystem events. It was merged into the Linux kernel mainline in the kernel version 2.6.13 released on August 28, 2005. 

**inotify-tools** is a set of command-line programs for Linux providing a simple interface to inotify and consists of two utilities:

* **inotifywait** simply blocks for inotify events, making it appropriate for use in shell scripts.

* **inotifywatch** collects filesystem usage statistics and outputs counts of each inotify event.

##### Pywatchdog is a simple python script that uses **inotifywait** for monitoring filesystem events from a python application in a easy way. #####

## Installation
```sh
$ apt-get install inotify-tools
```

The installation as pip package not available yet.

## Usage
```python
from watch_dog import FileSystemWatchDog

def run():

    watch_dog = FileSystemWatchDog(['/home/test_01','/home/test_02'])
    watch_dog.release_the_watch_dog()

    input()
    
    dam_list = watch_dog.get_caught_dams()
    
    if dam_list is not None:
        for dam in dam_list:
            print(dam.path)
            for event in dam.events:
                print(event.__dict__)

    watch_dog.hold_on_to_the_watch_dog()

if __name__ == "__main__":
    run()

```

input:

```
/home/test_01/
{'target': '.new_file.txt.swp', 'time': '02/07/17', 'events': 'CREATE'}
{'target': '.new_file.txt.swp', 'time': '02/07/17', 'events': 'DELETE'}
{'target': '.new_file.txt.swp', 'time': '02/07/17', 'events': 'MODIFY'}
{'target': 'new_file.txt', 'time': '02/07/17', 'events': 'MODIFY'}
/home/test_02/test_folder/
{'target': '.new_file_02.txt.swp', 'time': '02/07/17', 'events': 'CREATE'}
{'target': '.new_file_02.txt.swp', 'time': '02/07/17', 'events': 'DELETE'}
{'target': '.new_file_02.txt.swp', 'time': '02/07/17', 'events': 'MODIFY'}
{'target': 'new_file_02.txt', 'time': '02/07/17', 'events': 'MODIFY'}
{'target': 'new_file_02.txt', 'time': '02/07/17', 'events': 'DELETE'}
```

## Contributing

It could be great to get feedback and coding improvements from you! 
