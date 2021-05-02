Using Haskell Stack and VSCode
=====
- # Linux
    - These instructions are specific to Ubuntu 20.04, but should be similar for other Linux systems, and relevant web pages probably clarify.
    - ## Stack 
        - Stack is a tool for creation of Haskell projects (a file structure to contain code, and settings useful for compilation).
        - Website:  https://docs.haskellstack.org/en/stable/README/
            - ## install
                - ### Script-based install
                    - From the website:
                        - ### How to install
                            - Stack can be installed on most Unix-like (Un*x) operating systems, including macOS, and on Windows.
                            - For most Un*x operating systems, the easiest way to install is to run:
                            - `curl -sSL https://get.haskellstack.org/ | **sh**`
                            - or:
                            - `wget -qO- https://get.haskellstack.org/ | **sh**`
                - Alternative, manual installation
                    - Installation instructions for generic Linux (incluing Ubuntu)
                        - https://docs.haskellstack.org/en/stable/install_and_upgrade/#linux
                        - use installer
                        - unzip/extract folder to Desktop
                        - `mv ~/Desktop/stack-VERSION-NAME ~/.local/bin/` 
                        - `cd ~/.local/bin/`
                        - `sudo apt-get install g++ gcc libc6-dev libffi-dev libgmp-dev make xz-utils zlib1g-dev git gnupg netbase`
            - ## Test Install
                - `stack`
                - A couple of pages of stack documentation should appear.
            - ## Uninstall as necessary
                - (ref: https://github.com/commercialhaskell/stack/issues/3563)
                - `rm -rf ~/.stack`
                - `rm -rf /usr/.local/bin/stack-VERSION-NAME/`
                - Perhaps also `.stack-work/`  folders in any of your Haskell projects.
                - (https://github.com/commercialhaskell/stack/issues/3563)
                - ## First Project
                    - ### Create new project
                        - `$ stack new my-project simple`
                            - **stack** is the basic command.
                            - **new** tells stack to create a new set of files.
                            - **my-project** is the name to be used for the topmost folder/directory for the package.
                            - **simple** is the name of a template to use.
                        - This creates te following structure.
```
$ tree my-project
./my-project/
├── LICENSE
├── my-project.cabal
├── README.md
├── Setup.hs
├── src
│   └── Main.hs
├── stack.yaml
└── stack.yaml.lock
```

                    - ### Install GHC
                        - This will install a version of GHC (Glasgow Haskell Compiler). The feedback text will differ.
                        - ```shell
$ stack setup
Downloaded lts-3.1 build plan.    
Caching build plan
Fetched package index.
Populated index cache.
Downloaded ghc-7.10.2.
Installed GHC.
stack will use a locally installed GHC
For more information on paths, see 'stack path' and 'stack exec env'
To use this GHC and packages outside of a project, consider using:
stack ghc, stack ghci, stack runghc, or stack exec```
                    - ### Run GHCI (a REPL interpreter)
                        - Feedback text will differ slightly.
                        - ```shell
$ stack ghci
Configuring GHCi with the following packages: my-project
GHCi, version 7.10.2: http://www.haskell.org/ghc/  :? for help```
                            - GHCI will start up, and a REPL prompt will appear.
                        - `*Main> `
                    - ### Play Around (then :quit GHCI)
                        - ```shell

*Main> 17
17
*Main> 17 + 42
59
*Main> 3 == 3
True
*Main> :quit
$ ```
                    - ### Compile an executable
                        - ```shell
$ cd my-project 
$ stack build```
                    - ### Execute the executable
                        - ```shell
$ stack exec my-project
Hello World!```
        - ## VSCode
            - https://code.visualstudio.com/
            - ## On Linux
                - https://code.visualstudio.com/docs/setup/linux
                - ## On Unbuntu (I know, Ubuntu)
                    - "The easiest way to install Visual Studio Code for Debian/Ubuntu based distributions is to download and install the [.deb package (64-bit)](https://go.microsoft.com/fwlink/?LinkID=760868)"
                    - ### Install
                        - `$ sudo apt install ./<file>.deb`
                    - ### Run
                        - `$ code`
                        - This should launch VS Code
                    - ### install Haskell extensions
                        - In VSCode, **View > Extensions**
                        - Select and install **sdfs** and **sdfsd**
                    - ### Open Files in your project
                        - In VSCode, **View > Explorer**, then **File > Open Folder**
                        - This will open a file explorer. 
                        - Navigate to, and select, the top-level folder of your **my-project** package.
                        - Explore the files!
                    - ### Open a terminal through VSCode, and run your code using stack exec
                        - In VSCode, **Terminal > New Terminal**
                        - This launches a panel with your default shell.
                        - Navigate to the top directory of your project.
                        - ```shell
$ stack exec my-project
Hello, World!```
                        - Voila! 
                        - **見てご覧！**
                    - ### From the terminal, load your project into GHCI
                    - ```shell
$ stack ghci
Using main module: 1. Package `my-project' component my-project:exe:my-project with main-is file: /home/gt/Haskell/my-project/src/Main.hs
Configuring GHCi with the following packages: my-project
GHCi, version 8.10.4: https://www.haskell.org/ghc/  :? for help
[1 of 1] Compiling Main             ( /home/gt/Haskell/my-project/src/Main.hs, interpreted )
Ok, one module loaded.
Loaded GHCi configuration from /tmp/haskell-stack-ghci/53ae89a3/ghci-script
*Main> ```
                    - ### In GHCI, evaluate a function.
                    - ```shell
*Main> main
Hello, World!```
                    - ### Edit a file, then reload.
                    - Change the word **World** to **Mars**
                    - ```shell
*Main> :reload
Ok, one module loaded.
*Main> main
Hello, Mars!```
                    - ### Assign a value to a variable in a file, then change it in GHCI.
                    - Add a line `foo = 23` to the file **Main.hs**
                    - Save the file.
                    -  In GHCI
                    - ### In GHCI, evaluate a function
                    - ```shell
*Main> :reload
Ok, one module loaded.
*Main> foo
23
*Main> foo = 17
*Main> foo
17```
