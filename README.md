# DOT Language to Adjacency List
---
## How to use
### Install Java

- Install via CLI

  1. [ArchLinux](https://www.tecmint.com/install-java-on-arch-linux/)
   
	* Now we are going to install the latest version of JRE
		```bash
		sudo pacman -S jre-openjdk
		```

	* Now we are going to install the latest version of JDK
		```bash
		sudo pacman -S jdk-openjdk
		```
   2. Others
		```bash
		sudo apt install openjdk-XX-jdk
		sudo apt install openjdk-XX-jre
		```
		>Install the latest available version for your distro

### Install Antlr
1. Installation
   * Create a virtual enviroment
		```bash
		python -m venv /path/to/new/virtual/environment
		```
   
   * Install Antlr using the file `requirements.txt`
		```bash
		pip install -r requirements.txt
		```
   
   * Verify installation
		```bash
		antlr
		```
  
### Usage
   
   * Create the script `setup.sh`.

		```sh
		#!/usr/bin/sh

		setup(){
			local venvpath="$HOME/path/to/env"

			source "${venvpath}/bin/activate"
			
			export CLASSPATH=.:~/.m2/repository/org/antlr/antlr4/4.13.1/antlr4-4.13.1-complete.jar:$CLASSPATH
			alias grun='java org.antlr.v4.gui.TestRig'
		}

		setup
		```
   * Execute the script
		```bash
		source setup.sh
		```

   * Now we compile boths files.
		```bash
		~ antlr4 -no-listener -visitor DotExpr.g4 
		```

   * With `javac` we compile the java codes generated.
		```bash
		javac *.java
		```

   * If we want to see the gui, run Antlr with `grun`
		```bash
		grun DotExpr graph -gui
        ```
