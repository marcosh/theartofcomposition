---
title: The art of composition
author: Marco Perone @marcoshuttle
patat:
    margins:
        left: 2
        right: 2
...

# L'arte della composizione

## Chi sono?

Marco Perone

twitter.com/marcoshuttle

github.com/marcosh

marcosh.github.com

# Composizione

## Cosa componiamo?

- musica

- un mazzo di fiori

- un numero di telefono

- interfacce utente

- classi

- funzioni

## Cosa vuol dire comporre?

Mettere insieme i pezzi

`|-----|` `|---|` `|------|` `|---|` `|-----|`

    |-----|---|------|---|-----|

## Perchè comporre?

Focus locale

    |-----|---|------|---|-----|

`|-----|` `|---|` `|------|` `|---|` `|-----|`

## Perchè comporre ?

Riutilizzo

    |-----|---|------|---|-----|
                       ^    ^
                       |    |
                       v    v
                     |---|-----|---|----|-----|

# Organizzare l'informazione

## Come persone

Immagazziniamo informazioni

Le organizziamo nel nostro cervello

## Come programmatori

- database

- classi

- funzioni

- architetture

- interfacce

## Dinamica delle informazioni

Mettere insieme le informazioni per produrne di nuove

## Sillogismi

Proposizioni e deduzioni logiche

    "Ogni animale è mortale"

    "Ogni uomo è animale"
            
    "Ogni uomo è mortale"

## Matematica

Insiemi e funzioni

```
f: T1 -> T2

g: T2 -> T3
```

```
g . f: T1 -> T3
```

# Un po' di struttura

## Informazioni

Strutture dati

Nozioni

Conoscenza

## Informazioni

    String

    Nat

    Bool

## Collegamenti

Modalità per passare da un'informazione all'altra

Deduzioni

## Collegamenti

    lenght : String -> Nat

    isEven : Nat -> Bool

## Composizione

Colleghiamo i collegamenti!

    ┌─────────────────┐
    │                 │
    │                 v
    A ─────> B ─────> C

## Composizione

    (String -> Nat) -> (Nat -> Bool) -> (String -> Bool)

    isLengthEven = isEven . length

## Identità

Per ogni informazione/concetto A

    ┌────────┐
    │        │
    │   id   │
    │        v
    └─────── A

## Identità

Passare da un'informazione a se stessa non cambia il ragionamento

```
A ─── id --> A ─── f --> B

A ────────── f ────────> B
```

```
C ─── g --> A ─── id --> A

C ───────── g ─────────> A
```

## Inverso

Permette di esprimere il concetto di "tornare indietro"

    ┌────────┐
    │        │
    │   id   │
    │        v
    └─────── A ─── f --> B
             ^           │
             │           │
             └──── g ────┘

## Associatività

Non importa l'ordine con cui effettuiamo la composizione

    ┌─────────────────┐
    │                 │
    │                 v
    A ─────> B ─────> C ─────> D
             │                 ^
             │                 │
             └─────────────────┘

## Associatività

Comporta la possibilità del parallelismo

    ┌─────────────────┐
    │                 │
    │                 v
    A ─────> B ─────> C ─────> D ─────> E
                      │                 ^
                      │                 │
                      └─────────────────┘

# Formalizziamo una categoria

## Oggetti

Collezione di oggetti `Ob C`

    .     .     .
       .       .
     .       .
        .       .

## Morfismi

Per ogni coppia di oggetti `A, B` in `Ob C`, abbiamo un insieme `Hom(A, B)`

    A ─── Hom(A, B) --> B

## Composizione

Operazione `. : Hom(B, C) x Hom(A, B) -> Hom(A, C)`

    A ─── f --> B ─── g --> C
    
    A ─────── g . f ──────> C

## Identità

Per ogni oggetto `A` esiste un morfismo `1_A`

    ┌────────┐
    │        │
    │   id   │
    │        v
    └─────── A

## Identità

Per ogni morfismo `f : A -> B` abbiamo `f . 1_A = f`

```
A ─── id --> A ─── f --> B

A ────────── f ────────> B
```

Per ogni morfismo `g : C -> A` abbiamo `1_A . g = g`


```
C ─── g --> A ─── id --> A

C ───────── g ─────────> A
```

## Associatività

Per ogni 

`f` in `Hom(A, B)`

`g` in `Hom(B, C)`

`h` in `Hom(C, D)` 

abbiamo

`h . (g . f) = (h . g) . f`

## Associatività

    ┌─────────────────┐
    │                 │
    │                 v
    A ─────> B ─────> C ─────> D
             │                 ^
             │                 │
             └─────────────────┘

# Esempi di categorie

## Sistema logico deduttivo

Oggetti sono le proposizioni

Morfismi sono le deduzioni logiche

```
 A
───
 A
```

```
A => B, B => C
──────────────
    A => C  
```

## Grafo orientato

Oggetti sono i vertici

Morfismi sono i cammini nel grafo

    . --> . --> . --> .
    ^     │     │
    │     │     │
    │     v     v
    . <-- .     .

## Preordine

Relazione riflessiva e transitiva

    a <= a

    a <= b & b <= c => a <= c

Categoria in cui c'è al più un morfismo tra due oggetti

## Monoide

Insieme con un'operazione associativa con elemento identico

    (N, +, 0)

    (N, *, 1)

    0 --> 1 --> 2 --> 3
                ^     │
                │     v
                5 <-- 4

Categoria con un solo oggetto

## Insiemi e funzioni

    A ─── f --> B

    f sottoinsieme di A x B tale che ...

## Linguaggi di programmazione

Tipi e funzioni pure

    A ─── f --> B

    y = f x

# Esempi di "quasi" categorie

## Classi e metodi

    class Foo 
    {
        method bar(): Bar
    }

    class Bar
    {
        method baz(): Baz
    }

    class Baz {}

    foo = new Foo()

    foo->bar()->baz()

## Classi e proprietà

    class Foo 
    {
        Bar bar
    }

    class Bar
    {
        Baz baz
    }

    class Baz {}

    foo = new Foo()

    foo.bar.baz

## Componenti in UI

Quali sono gli oggetti?

Quali sono i morfismi?

Qual'è l'operazione di composizione?

# Cosa rompe la composizione

## Meccanismi alternativi per la trasmissione di informazione

    A ─── f --> B
          │
          │
          v
          C

## Variabili globali

    A ─── f --> B ─── g --> C
          │           │
          │           │
          v           v
          D           D

## Eccezioni

    A ─── f --> B ─── g --> C
          │
          │
          └───> E

## Mondo esterno

    A ─── f --> B
          ^
          │
          v
          IO

## Composizionalità

Trasparenza referenziale

Morfismo definito dalla sua firma

# Funtori

## Perchè i funtori

Abbiamo bisogno di tipi/contesti più espressivi

Costuttori di tipi più complessi

## Definizione

`C` e `D` categorie

    F : Ob C -> Ob D

    F : Hom_C (A, B) -> Hom_D (F(A), F(B))

tale che

    F(1_A) = 1_F(A)

    F(g . f) = F(g) . F(f)

## Esempi

    F : Monoids -> Sets

    PS : Set -> Set

    F : Preorder1 -> Preorder2

## In programmazione

Type constructor `A -> F A`

`map : (A -> B) -> F A -> F B`

# Effetti

## Problema

Gli effetti, se non tracciati, rompono la composizione

## Soluzione

Basta renderli espliciti!

Usando i funtori

## Maybe

    Maybe A = Just A | Nothing

    map : (A -> B) -> Maybe A -> Maybe B
    map f Nothing  = Nothing    
    map f (Just a) = Just (f a)

## List

    List A = Nil | Cons A (List A)

    map : (A -> B) -> List A -> List B
    map f []        = []
    map f (x :: xs) = (f x) :: (map f xs)

## Reader

    Reader E A = E -> A

    map : (A -> B) -> Reader E A -> Reader E B
    map f g = f . g

## IO

`IO A` descrive una computazione che produce un valore di tipo `A`

Computazione viene poi eseguita dal runtime

# Conclusione

## Perchè

Focus locale

Riutilizzo

## Niente paura

Sono solo puntini e freccette

## Standing on the shoulders of giants

Possiamo utilizzare il lavoro già fatto dai matematici

## Cosa serve

Funzioni che fanno solo quello che il loro tipo dichiara

Type system decente

Possibilità di tracciare gli effetti

# Grazie

## Feedback, please!

https://github.com/marcosh/theartofcomposition



twitter.com/marcoshuttle

github.com/marcosh

marcosh.github.com

# Domande?
