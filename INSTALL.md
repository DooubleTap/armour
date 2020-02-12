This is a rudimentary setup instruction gathered by a few different users of the script.

# Let's assume a few things for this install

The bot will be ARMOUR (lower caps) 

And the bot nickame will be MOOSE (lower caps)

# INSTALL DEPENDENCIES

> sudo apt-get install libsqlite3-tcl sqlite3 

cd /home/armour/

# INSTALL EGGDROP
git clone https://github.com/eggheads/eggdrop.git

./configure

make

make config

make install DEST="/home/armour/moose"

cd ..

Edit your eggdrop.conf and save it as: moose-unet.conf

Add this line in moose-unet.conf(after the listen port): set uservar "moose-unet"

ALSO add this line at the bottom of moose-unet.conf: source armour/$uservar.conf

# INSTALL ARMOUR

now in this folder /home/armour/moose/: git clone https://github.com/empus/armour.git

EDIT armour.sample.conf and save it as: moose-unet.conf (yes, same as your eggdrop.conf name)

now, in /home/armour/moose/armour/ create the directory /db/  and in /db/ create /sql/

# LOAD EGGDROP

now it's time to load your eggdrop: ./eggdrop -m moose-unet.conf (your eggdrop.conf file)

This will make the bot generate a users.db file. (Here: /home/armour/moose/armour/db/sql/users.db)

# ADD YOURSELF TO ARMOUR
Make sure that you are in this path: /home/armour/moose/armour/db/sql/ 

type: sqlite3 moose-unet.db

Copy paste this(assuming your nickname is Seb and xusername is also Seb: 

> INSERT into users (user,xuser,level,pass) values('Seb','Seb',500,'foo');

THEN make sure you telnet the eggdrop with NEW as your nickname. (This will create the first account)

in TELNET type this: .tcl userdb:db:load

After that: .rehash

In TELNET make the bot join the 2 channels (console chan and main chan) with .+chan #chan

you should be AUTOLOGIN, if not, just /hop the room.
