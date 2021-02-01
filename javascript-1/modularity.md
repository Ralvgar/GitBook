# Modularity

Modularity helps the process of organizing the entire code base. So if modular approach is not applied then the structure will grow and become out of control. The modular approach in javascript programming helps to develop more structured code and make it easily maintainable.

## Modules in ES6 <a id="0046"></a>

Modules in ES6 are very simple to use. Like other usage of modules, ES6 provides a way to export modules so that they can be specified as dependencies to other modules.

### Exporting Modules <a id="dbe4"></a>

```javascript
export function setName(name) { ... }export function getName() { ... }export function logPlayer() { ... }
```

```javascript
function addResult() { ... }function updateScoreboard() { ... }export { addResult, updateScoreboard };
```

### Importing Modules <a id="bd3c"></a>

```javascript
import scoreboard from ‘./scoreboard.js’;
```

```javascript
import { getName as getPlayerName, logPlayer } from ‘./player.js’;
```



