## Backend Actions in `bingo/index.php`

### `bingo/new`
Create a new bingo game (lobby).
#### Parameters
- user name
- optional game password (plain text, is whatever)
#### Responses
- failed (game already exists, invalid password, just not feeling it)
- success
  - user GUID
  - game GUID

### `bingo/join`
Join a bingo game (lobby).
#### Parameters
- host user name
- optional game password (plain text...)
#### Responses
- failed (game doesn't exist, wrong password, just not feeling it)
- success
  - user GUID
  - game GUID

### `bingo/sync`
Get the UTC time the game should sync to.
#### Parameters
None.
#### Responses
- success
  - current server UTC time

### `bingo/start`
Start the bingo game (from lobby).
#### Parameters
- host user GUID (for 'authentication')
- game GUID (for more 'authentication')
#### Responses
- failed (unknown game/user)
- success
  - no data

### `bingo/status`
Get the game status.
- connected player names
- player board statuses
- UTC start time
- UTC end time
- (looping) numbers list
- game state (lobby/starting/running/ended)
#### Parameters
- game GUID (for 'authentication')
- desired data
#### Responses
- failed (unknown game)
- success
  - the data

### `bingo/try`
Try to cross off a bingo square.
#### Parameters
- user GUID (for 'authentication')
- game GUID (for more 'authentication')
- board index (0-24)
#### Responses
- failed (unknown game/user)
- success
  - number matched or number failed
