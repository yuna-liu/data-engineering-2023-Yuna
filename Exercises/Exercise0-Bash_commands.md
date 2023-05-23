# Exercise 0 - Bash commands

Use windows for linux (WSL), ubuntu bash, git bash or terminal in mac to solve all these exercises, **don’t use GUI**. A lot of the training in these exercises are both to search up commands and also to understand the computer science terminology.

**Tips**: work with exercise X alongside with other exercises.

---

## 0. Setup a git repository (\*)

a) Make a directory called Linux-training.

b) Create the files called

```bash
“note1.txt”, “note2.txt”, “note3.txt”, “note4"
```

---
mkdir Linux-training
cd Linux-training  # Change to the "Linux-training" directory
touch note1.txt note2.txt note3.txt note4.txt  # Create the files

## 1. Navigating and moving (\*)

a) Make a subdirectory called cool_notes

b) Move all .txt files into cool_notes

c) Delete note4

d) Change directory to cool_notes and list all the files there

e) Move note3.txt out from cool_notes into parent directory

f) Navigate to parent directory

g) From here list all files including hidden files

h) Change name on note3.txt to note_home.txt

---
mkdir cool_notes
mv *.txt cool_notes/
rm cool_notes/note4.txt
cd cool_notes 
ls
mv note3.txt ../
cd ..
ls -a
mv note3.txt note_home.txt

## 2. Printing, variables and manipulating text (\*)

a) Print out “hello from note_home” into bash

b) Write this text string into note_home.txt

c) Print out the “current path is: <your current directory path>” in bash

d) Write this string into note_home in a new line so it should contain

```bash
hello from note_home
current_directory is: <your current directory path>
```

e) Print out the content of the note_home.txt

f) Count the number of words in this file

g) Count the number of lines in this file

h) Count the number of files in cool_notes

i) Check the disk usage in your directory and make the format human readable

---
echo "hello from note_home"
echo "hello from note_home" > note_home.txt
echo "current path is: $(pwd)"
echo -e "current path is: $(pwd)" >> note_home.txt
cat note_home.txt
wc -w note_home.txt
wc -l note_home.txt
ls -1 cool_notes | wc -l
du -sh



## 3. Pokeventure (\*)

a) Create a folder called data with a subfolder called pokemons

mkdir data
mkdir data/pokemons

b) Create a file called pokemon_list.txt
touch data/pokemon_list.txt


c) Type in a random list of pokemons, using echo and the bitshift operator

for example:

```bash
pikachu
voltorb
bulbasaur
mew
zapdos
mewtwo
```
echo -e "pikachu\nvoltorb\nbulbasaur\nmew\nzapdos\nmewtwo" > data/pokemon_list.txt

d) Loop through your file and print out the following

```bash
pokemon: pikachu
pokemon: voltorb
pokemon: bulbasaur
pokemon: mew
pokemon: zapdos
pokemon: mewtwo
```
while read -r pokemon; do
  echo "pokemon: $pokemon"
done < data/pokemon_list.txt


e) Now test out the following api manually in your browser [https://pokeapi.co/api/v2/pokemon-species/voltorb](https://pokeapi.co/api/v2/pokemon-species/voltorb)

f) Now test it out using bash, and see that it prints out the same results
curl -s https://pokeapi.co/api/v2/pokemon-species/voltorb

g) Do a for loop on pokemon_list.txt, pick the pokemons on the file and request the api. Save each pokemon into their respective json file. Important: add a pause of 2 seconds after each iteration. Your structure should look something like this now.

```bash
└── data
    └── pokemons
        ├── bulbasaur.json
        ├── mew.json
        ├── mewtwo.json
        ├── pikachu.json
        ├── pokemon_list.txt
        ├── voltorb.json
        └── zapdos.json
```
touch pokemon_api.sh
nano pokemon_api.sh


#!/bin/bash

# Read each line from pokemon_list.txt
while read -r pokemon; do
  # Make API request for the current Pokémon and save the response to a JSON file
  curl -s "https://pokeapi.co/api/v2/pokemon-species/$pokemon" -o "data/pokemons/${pokemon}.json"
  # Pause for 2 seconds before the next iteration
  sleep 2
done < data/pokemon_list.txt


./pokemon_api.sh

h) Remove all files ending with .json using one command
rm data/pokemons/*.json

i) Now move yourself to the same level, i.e. sibling to data directory. Create a bash script file called download_pokemons.sh. Put in bash logic for downloading the pokemons specified in data/pokemon/pokemon_list.txt file and saving it into data/pokemons/ and run it. Your file structure might look like this now. (\*\*)

```bash
├── data
│   └── pokemons
│       ├── bulbasaur.json
│       ├── mew.json
│       ├── mewtwo.json
│       ├── pikachu.json
│       ├── pokemon_list.txt
│       ├── voltorb.json
│       └── zapdos.json
└── download_pokemons.sh
```

---

## X. Commands glossary (\*)

Fill in this table. You can do this in any application, it might be too hardcore to do this with terminal only. Tips you can use man command to check documentation. Also try out the different commands to see them in action.

| Command | What does the command do | Some useful options |
| ------- | ------------------------ | ------------------- |
| cd      |                          |                     |
| ls      |                          |                     |
| touch   |                          |                     |
| wc      |                          |                     |
| grep    |                          |                     |
| mkdir   |                          |                     |
| mv      |                          |                     |
| rm      |                          |                     |
| rmdir   |                          |                     |
| ssh     |                          |                     |
| curl    |                          |                     |
| sudo    |                          |                     |
| apt-get |                          |                     |
| ps      |                          |                     |
| cp      |                          |                     |
| less    |                          |                     |
| top     |                          |                     |
| head    |                          |                     |
| echo    |                          |                     |
| cat     |                          |                     |
| chmod   |                          |                     |
| chown   |                          |                     |
| kill    |                          |                     |
| &&      |                          |                     |
| wget    |                          |                     |
| pwd     |                          |                     |
| >>      |                          |                     |
| >       |                          |                     |
| \*      |                          |                     |
| ./      |                          |                     |
| diff    |                          |                     |
| find    |                          |                     |
