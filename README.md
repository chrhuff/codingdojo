# codingdojo
CodingDojo 2015

Klonen mit 

 git clone --recursive git@github.com:chrhuff/codingdojo.git

 oder:
 git clone https://github.com/chrhuff/codingdojo.git/
 git pull
 git submodule init
 git submodule update --remote


GITHub mit ssh private key

```
$ cat ~/.ssh/config
Host github.com
  IdentityFile ~/.ssh/id_rsa_github
```


Rest-Calls:

initGame
```
content-type: application/json 

POST http://localhost:8080/mining-service/minesweeper/
{
"width"     : 20,
"height"    : 15,
"mineRatio" : 0.2
}
Response: {sessid}
```

submitAction
```
PUT http://localhost:8080/mining-service/minesweeper/{sessid}
{
"position" : {
"x" : 5,
"y" : 7
},
"type" : "UNCOVER"
//UNCOVER -> 0
//FLAG    -> 1
//SOLVE   -> 2
}
Response: ActionResult oder 204 wenn nicht existierende Session angesprochen wurde

{
	"visibleCells" : [{
	"y" : 0,
	"x" : 0,
	"mine" : null,
	"flagged" : false,
	"number" : -1
	}, {
	"y" : 1,
	"x" : 0,
	"mine" : null,
	"flagged" : false,
	"number" : -1
	},
	....
	}, {
	"y" : 14,
	"x" : 16,
	"mine" : null,
	"flagged" : false,
	"number" : -1
	}
	],
	"status" : "CONTINUE"
	//CONTINUE -> 0
	//GAMEOVER -> 1
	//VICTORY  -> 2
}
```

currentGameState
```
GET http://localhost:8080/mining-service/minesweeper/42


Response: ActionResult oder 204 wenn nicht existierende Session angesprochen wurde
{
	"visibleCells" : [{
	"y" : 0,
	"x" : 0,
	"mine" : null,
	"flagged" : false,
	"number" : -1
	}, {
	"y" : 1,
	"x" : 0,
	"mine" : null,
	"flagged" : false,
	"number" : -1
	},
	....
	}, {
	"y" : 14,
	"x" : 16,
	"mine" : null,
	"flagged" : false,
	"number" : -1
	}
	],
	"status" : "CONTINUE"
	//CONTINUE -> 0
	//GAMEOVER -> 1
	//VICTORY  -> 2
}
```

