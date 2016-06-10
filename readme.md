# highman-special

Проект для пикап-бота HIGHMAN-а

### Установка и запуск

```sh
git clone https://github.com/em92/highman-special.git
cd ./highman-special
npm update
node main.js
```

### Способ применения

* Допустим собрались 4 игрока для чтобы поиграть _gametype_, где _gametype_ может быть ctf или tdm. У этих игроков следующие дискорд-ид:
	* 178940495014133760
	* 177850342959087616
	* 178861087674859520
	* 178820047370846208
* Выполняешь запрос:
	* http://localhost:3330/shuffle/_gametype_/178940495014133760+177850342959087616+178861087674859520+178820047370846208
* В успешном ответе на этот запрос будет ответ в формате json:
	* ok - индикатор успешности (в данном случае true)
	* red, blue - составы команд
	* red_elo, blue_elo - средние показатели эло для команды
	* unrated - массив, содержащий дискорд-ид игроков, для котороых не определены steamid64
* В безуспешном ответе ответ будет содержать
	* ok - индикатор успешности (в данном случае false)
	* error_code - код ошибки
	* error_msg - описание ошибки
* Для присвоения steamid64 76561197983318796 игроку с дискорд-ид 183254040266670080 нужно выполнить один из следующих запросов:
	* http://localhost:3330/map/183254040266670080/76561197983318796
	* http://localhost:3330/force_map/183254040266670080/76561197983318796
* Первый запрос от второго отличается тем, что в первом при попытке перепределить изначально определенную пару (дискорд-ид, steamid64) будет возвращать { ok: false }

