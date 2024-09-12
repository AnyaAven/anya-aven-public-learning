### Python Interpreter

Python Interpreter?! Yikes, what a nightmare to set up with an existing venv.

If you are starting a new project it is lovely and very plug and play!
The documentation led me to believe that I needed an SDK configuration inside of
my project structure. But alas, if you look at the project configuration of
the "New Project" with Python and an existing venv it shows "no sdk".
It has a `module SDK`, look for 'modules' on the left side.
The SDK should point to something similar to 'project/venv/bin/python'

