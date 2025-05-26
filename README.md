# Aurora Sofle Keymaps
These are my personal keymaps for the Aurora Sofle split keyboard, a 4x6 key plus 5 thumb cluster keys per half setup.

## Standard layout

### Abbreviations
| Abbreviation | Meaning         |
| ------------ | --------------- |
| SPC          |  Space          |   
| BSP          |  Back Space     |
| psc          |  print screen   |
| p.u          |  page up        |
| p.d          |  page down      |
| c.w          |  caps word      |
| hom          |  home           | 

 
#### Base layer (BASE)
    Tap:                                                        Hold: 
       
       ┌───┬───┬───┬───┬───┬───┐       ┌───┬───┬───┬───┬───┬───┐                ┌───┬───┬───┬───┬───┬───┐       ┌───┬───┬───┬───┬───┬───┐
       │ESC│ 1 │ 2 │ 3 │ 4 │ 5 │       │ 6 │ 7 │ 8 │ 9 │ 0 │DEL│                │ESC│ 1 │ 2 │ 3 │ 4 │ 5 │       │ 6 │ 7 │ 8 │ 9 │ 0 │DEL│
       ├───┼───┼───┼───┼───┼───┤       ├───┼───┼───┼───┼───┼───┤                ├───┼───┼───┼───┼───┼───┤       ├───┼───┼───┼───┼───┼───┤
       │TAB│ Q │ W │ E │ R │ T │       │ Y │ U │ I │ O │ P │ ` │                │TAB│ Q │ W │ E │ R │ T │       │ Y │ U │ I │ O │ P │ ` │
       ├───┼───┼───┼───┼───┼───┤       ├───┼───┼───┼───┼───┼───┤                ├───┼───┼───┼───┼───┼───┤       ├───┼───┼───┼───┼───┼───┤
       │SHF│ A │ S │ D │ F │ G │       │ H │ J │ K │ L │ : │SHF│                │SHF│ A │ S │ D │ F │ G │       │ H │ J │ K │ L │ : │SHF│
       ├───┼───┼───┼───┼───┼───┤       ├───┼───┼───┼───┼───┼───┤                ├───┼───┼───┼───┼───┼───┤       ├───┼───┼───┼───┼───┼───┤
       │c.w│ Z │ X │ C │ V │ B │       │ N │ M │ , │ . │ _ │c.w│                │c.w│ Z │ X │ C │ V │ B │       │ N │ M │ , │ . │ _ │c.w│
       └───┴───┴───┴───┴───┴───┘       └───┴───┴───┴───┴───┴───┘                └───┴───┴───┴───┴───┴───┘       └───┴───┴───┴───┴───┴───┘
             ┌───┬───┬───┐                   ┌───┬───┬───┐                            ┌───┬───┬───┐                   ┌───┬───┬───┐
             │   │   │   ├───┐           ┌───┤   │   │   │                            │BLU│MAC│NUM├───┐           ┌───┤NUM│MAC│BLU│
             └───┴───┴───┤SPC├───┐   ┌───┤BSP├───┴───┴───┘                            └───┴───┴───┤SYM├───┐   ┌───┤SYM├───┴───┴───┘
                         └───│RET│   │RET├───┘                                                    └───│NAV│   │NAV├───┘            
                             └───┘   └───┘                                                            └───┘   └───┘                
                                                                         
##### Combo mappings for brackets
| Left Hand | Symbol | Right Hand | Symbol |
|-----------|--------|------------|--------|
| `d + f`   | `"`    | `j + k`    | `'`    |
| `s + f`   | `(`    | `j + l`    | `)`    |
| `a + f`   | `/`    | `j + :`    | `\`    |
| `x + v`   | `{`    | `m + .`    | `}`    |
| `w + r`   | `[`    | `u + o`    | `]`    |

### Symbols layer
//TODO: add these layers

## Functions

### Spacemod, backspacemod
The space and back space keys are modifed with a custom mod morph and hold tap combination. The result gives a key with three functions. 
For the space key, one tap results in a space, holding the key results in activating the symbols layer, and shift-tapping space results in a backspace.

```keymap 
        //Super space key nested into spacemod below: tap - space, hold - momentary layer, shift+tap - backspace
        spaceshift: shift_space_is_backspace { 
            compatible = "zmk,behavior-mod-morph";
            #binding-cells = <0>;
            bindings = <&kp SPACE>, <&kp BACKSPACE>;          
            mods = <(MOD_LSFT|MOD_RSFT)>;       
        };
        spacemod: spaceshift_and_layer_hold {
            compatible = "zmk,behavior-hold-tap";
            #binding-cells = <2>;
            flavor = "hold-preferred";
            tapping-term-ms = <200>;
            bindings = <&mo>, <&spaceshift>;
        };
```
