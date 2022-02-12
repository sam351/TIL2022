
# Lecture 4: Dependency Parsing

## 1. Two views of linguistic structure
### 1) `Context-Free Grammars (CFGs)`
* `Context-Free Grammars (CFGs)` = Constituency = phrase structure grammar
* `phrase` structure organizes `words` into nested `constituents`
* `words` (starting unit) → words combine into `phrases` → phrases can combine into bigger `phrases`

    <img src="images/lecture04_img01.png" width="300">
    <img src="images/lecture04_img02.png" width="450">

### 2) `Dependency structure`
* `Dependency structure` shows which `words` depend on (modify, attach to, or are arguments of) which other `words`
* In modern NLP (starting around 2000), `Dependency Grammar` is most common (ex. `dependency parser`)

    <img src="images/lecture04_img03.png" width="350">

### 3) Why do we need `sentence structure`?
* Humans communicate complex ideas by composing words together into bigger units to convey complex meanings
* Listeners need to work out what modifies(attaches to) what
* A `model` needs to understand `sentence structure` in order to be able to interpret language correctly

<br>

