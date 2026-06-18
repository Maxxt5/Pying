# Pying Engine v3.1 🎮

> Tu primer engine de juegos 2D hecho 100% en Python puro para Termux/Celular

**Pying** es un motor de juegos ASCII diseñado para correr sin dependencias raras. Si tu celular abre Termux, puedes crear juegos.

### ¿Qué hace especial a Pying?

Pying no usa pygame, arcade ni librerías pesadas. Todo corre en tu terminal con Python base.

| Feature | Como se usa | Qué hace |
| --- | --- | --- |
| **Nodos** | `py.new("player")` | Crea cualquier objeto: jugador, enemigo, bala, texto |
| **Propiedades** | `py.prop("player").pos = 10` | Modifica posición, forma, color, etc |
| **Física** | `py.prop("player").jump_key = "w"` | Salto y gravedad automáticos |
| **Input** | `py.input_key("a")` | Detecta teclas sin instalar `keyboard` |
| **Colisiones** | `py.coll("player", "enemy")` | Detecta si 2 nodos están en la misma casilla |
| **Labels** | `py.prop("ui").text = "Score: 0"` | Textos con color, font y separación |

### Tu primer juego en 15 líneas

`game.py`
```python
import pying as py

def start():
    py.Pying.floor = {"dist": 20, "form": "_"}
    py.new("player")
    py.prop("player").pos = 5
    py.prop("player").form = "P"
    py.prop("player").jump_key = "w" # Salto con gravedad

def loop():
    if py.input_key("a"): py.prop("player").pos -= 1 # Izquierda
    if py.input_key("d"): py.prop("player").pos += 1 # Derecha

if __name__ == "__main__":
    py.Pying.allSys.code(start, loop)
