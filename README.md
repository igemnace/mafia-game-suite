# Mafia Game Suite

This project is a suite of files and scripts that is designed to facilitate
Mafia games smoothly, with as much automation and as little repetition as
possible.

The suite itself relies on the powerful text and file management capabilities of
Unix, and so requires a Unix-like environment. Information is spread out across
files and written in plain text by design, to allow the Unix tools to work their
magic.

## About Mafia

Mafia is a popular social deduction game where a faction of Civilians attempt to
discover members of a secret Mafia.

The Mafia pick out and kill a Civilian once a night. During the day, the town
arranges a vote for Civilians to lynch a suspected Mafia member. The Mafia
masquerade as Civilians and so have the right to vote to lynch as well.

The Civilians only win when the entire Mafia is lynched. The Mafia only win when
they outnumber the Civilians.

## Roles

At the beginning of a game, roles are assigned to players. In a basic game, the
only roles are Civilian and Mafia.

To make games more exciting, game masters assign specialized roles to players,
allowing them to perform actions other than the normal day lynch vote and Mafia
night kill.

Popular roles include:

- **Detective:** a Civilian who can investigate players to determine whether
  they are Mafia (usually once per night)
- **Vigilante:** a Civilian who can perform his own kill at night, to try to
  eliminate the Mafia himself (usually given one bullet every two nights)
- **Doctor:** a Civilian who can protect a player from being the target of any
  action during the night, possibly stopping them from being killed or
  investigated (usually once per night)
- **Godfather:** a Mafia who is undetectable even under a Detective's
  investigation

## Starting a Game

1. Add the names of all players to the `players` file, with each name on its own
   line.
2. Similarly, add all roles to the `roles` file. The Mafia role has to be
   declared but the Civilian role does not. If more than one of a role is
   required (e.g. two Mafia players), add the corresponding number of entries.
3. Run the `generate_roles.sh` script. This will populate the `secret` file with
   a randomized list of players with role assignments.
4. Inform each player of their role.

*Note:* To help ensure that players only see their own roles and not someone
else's, it is recommended never to open the `secret` file in a text editor.

Instead, make use of `grep`. `grep John secret` will display only the line
containing "John", which might display "John Mafia" for example. If no role
appears beside a player's name, that player is a Civilian.

## Day-Night Cycle

The `game` file is meant to contain all the game master's notes through out a
game. This is the ideal place to write the events of each day and night, to keep
track of which players were killed and when, which roles did which actions, how
many bullets the Vigilante has, etc.

## Licensing

This project is licensed under the GNU General Public License v3 (GNU GPLv3).

## TODO

The suite is functional but not fully automated at the moment.

Because of the file structure of the project, it is possible to run full,
complicated games with just a few good Unix tools (`grep`, `cut`, `paste`, etc.)
and a text editor.

However, to make the game master's job as frictionless as possible, this project
aims to automate mundane tasks such as generating roles or typing up a template
for a day cycle in the `game` file. To this end, the following actions are due
to be automated:

- drafting a day/night cycle in the `game` file
- incrementing Vigilante bullets 
- keeping track of alive and dead players
