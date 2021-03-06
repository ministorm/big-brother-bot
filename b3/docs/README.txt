Big Brother Bot
===============

* [Official website] (http://www.bigbrotherbot.com)
* [Forums] (http://www.bigbrotherbot.com/forums)
* [Documentation] (http://www.bigbrotherbot.com/b3.html)

### Requirements

1. Python 2.3+ - http://www.python.org
2. MySQL-python (Tested with 0.9.2 and 1.0) - http://sourceforge.net/project/showfiles.php?group_id=22307&package_id=15775
3. MySQL (Tested with 3.23) - http://www.mysql.com/
4. Python Elementtree package - http://www.python.org/pypi/elementtree/1.2.6-20050316
5. setuptools - http://peak.telecommunity.com/dist/ez_setup.py (download and run)

### Assumptions

I assume you know how to use python and MySQL. If not you should consult the 
documentation for these if you have problems or questions on how to administer 
each.

### Installation

You have two choices of installation for b3. You can use the easy to install
Python Egg or the source distribution.

#### Installing Python Egg

1. Download and run the setup tools installer if you haven't already.
2. Run `easy_install -U b3`.

   *Note 1*: MySQL-python does not seem to download and install correctly as a
   easy_install package. You should instead install it directly by getting
   the latest install link of the Source Forge page and run easy_install on it.
   The same goes for the Elementtree library.

   *Note 2*: easy_install needs to write into Python's "site-packages"
   directory. You may need root/administrator privileges to do this. For
   advanced users, easy_install can use alternative destinations as well.

It should be that simple. B3 and all its dependancies should be installed. You
can skip the 'Installing Source Distribution' section, and proceed to
'Setting up MySQL'


#### Installing Source Distribution

1. Download the latest source distribution from http://www.python.org/pypi/b3
2. Extract the package to a suitable location, example: /usr/local/games/b3

### Setting up MySQL

1. Create a database in MySQL for B3 to use. Create a user that has full 
   permissions on this database for B3. 
   
   *Note*: You could also do this by running the script b3/docs/b3-db.sql on
   MySQL,but don't forget to edit the password in that file first.

2. Run the B3 database SQL script (b3/docs/b3.sql) on your B3 database.

### Setting up B3

1. Create a directory to store your b3 log files and config files, example:
   /home/b3/conf
2. Copy the config files from /install/path/b3/conf to /home/b3/conf.
3. Modify b3.xml
   Edit database <scheme>://<username>:<password>@<host>/<database> 
	Example: <set name="database">mysql://b3:password@localhost/b3</set>

	Edit logfile 
	Example: <set name="logfile">/home/b3/b3.log</set> 

	Edit game log 
	Example: <set name="game_log">/usr/games/cod/uo/games_mp.log</set> 

	Edit rcon_password 
	Example: <set name="rcon_password">password</set>

	Leave log_level at 9 for debugging, If there is a bug found we will 
	need your b3.log.
4. If you left the publist plugin enabled (default), add "sets _B3 true" to 
   your server config or B3 will exit. Alternatively, you can disable the
   plugin by commenting out its entry in b3.xml.
   

### Running B3

#### Running as a Python Egg

1. Run b3_run specifying your config file:
   `b3_run -c /home/b3/conf/b3.xml`
	
#### Running as a Source Install

1. Change to the install directory:
   `cd /usr/local/games/b3`
2. Run b3_run.py specifying your config file:
   `python ./b3_run.py -c /home/b3/conf/b3.xml`

*Note*: You can run `b3_run --help` for more options.

### Checking Status

1. Check b3.log
	`tail -n100 -f b3.log`
   
### Setup Users

1. Change iamgod to 0 in the b3/conf/plugin_admin.xml
2. Connect to the server and type !iamgod. This will register you as the server
   owner. 
3. Change iamgod back to "none" after you are registered.
