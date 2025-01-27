
# React: JSX, Komponenter och Props  

### Innehåll denna workshop:
* Sätta upp ett Reactprojekt (med Typescript) i Vite 
* Skapa din första Reactkomponent
* Använda dig av JSX
* Använda dig av flera komponenter samt exportera/importera komponenter
* Skicka information från en komponent till en annan komponent (använda props)
* Hantera props med object destructering 
* Hur man renderar listor i React m.h.a map()
* Skriva logik (funktioner) inuti komponenter


### 💬 Diskussionsfrågor

* Vad är JSX? 
* Vad är prop och vad används de till?
* Hur kan man typa props med Typescript? Använda objekt destructering?
* Varför har React namngivning som ex className, htmlFor?
* Hur renderar man en lista i React? Varför behövs en key?
* CSS i React. Vad finns det för lösningar att en viss CSS hör endast till en viss komponent?


# 👩🏽‍💻 Övning: Pokedex

Syftet med övningen är lära sig att bygga en enkel reactapp med flera komponenenter samt använda props som skickar information mellan komponenterna.

### Din uppgift:
Gör en komponent Pokedex som innehåller några utvalda Pokemonkort med respektive information om vardera Pokemon. Renderingen ska se ut (ungefär) som denna bild (del 1 + 2). 
Använd dig av Typescript för att definiera dina typer (använd type eller interface)

![Pokedex](/pokedex.png)

## 1. Sätta upp ett Reactprojekt med Vite 

* Se till att du har Node.js installerat [https://nodejs.org](https://nodejs.org) 
* Navigera i terminalen där du vill installera din reactapplikation.
* Kör sedan du följande instruktion i terminalen

```
npm create vite@latest my-app -- --template react-ts
```
eller


## 2. Implementera komponenterna och props

Du ska skapa 3 olika komponenter: 

### App 
Den här komponenten ska rendera ut endast en Pokedex-komponent, där datat om pokemons ska skickas med som en prop.


### Pokedex 
Den här komponenten ska ta emot datat om pokemens (en array av objekt) och rendera vardera Pokecard. Använd dig av map()!

**Använd dig av följande data om pokemenons:**

```
	[
	  {id: 4,   name: 'Charmander', type: 'fire',     base_experience: 62},
	  {id: 7,   name: 'Squirtle',   type: 'water',    base_experience: 63},
	  {id: 11,  name: 'Metapod',    type: 'bug',      base_experience: 72},
	  {id: 12,  name: 'Butterfree', type: 'flying',   base_experience: 178},
	  {id: 25,  name: 'Pikachu',    type: 'electric', base_experience: 112},
	  {id: 39,  name: 'Jigglypuff', type: 'normal',   base_experience: 95},
	  {id: 94,  name: 'Gengar',     type: 'poison',   base_experience: 225},
	  {id: 133, name: 'Eevee',      type: 'normal',   base_experience: 65}
	]
```

### Pokecard
Den här komponenten visar en Pokemon med namn, bild, typ och experience. För varje PokeCard ska följande bild läsas in enligt id för en pokemon:

`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${id}.png`

Layouten ska vara som ett card. Avänd flexbox eller grid.  Kom ihåg att klassnamn döps till `className`i React och inte `class` som i Vanilla JS. CSS reglerna kan läggas i App.css. Senare i kursen kommer vi titta på andra sätt att använda CSS i React.

## 3. Utöka med Pokegame-komponenten

 Nu ska du även skapa en Pokegame-komponent

1. Modifiera din App-komponent så att den renderar en Pokegame istället för en Pokedex

2. Pokegame ska ta emot data med pokemons och sedan slumpa 2 st "händer" med 4 st pokemons vardera. Pokegame ska alltså rendera 2 st Pokedex. 
* I Pokegame ska du beräkna summan av `base_experience` för vardera hand. Summan för varje ska skickas med som props till vardera Pokedex.
* I Pokegame ska man kunna avgöra vilken hand av pokemonkort som har högst experience. Skicka med ännu en props till Pokedex som heter `isWinner`. `isWinner` är `true` om handen har högst experience, `false` om den inte är det. 
* I Pokedex-komponenten ska det nu också visas en rubrik "This hand wins!" om isWinner är true. 

## 4. Dela upp varje komponent i moduler

***Obs!*** *När man lär sig React i början kan det vara en fördel att låta alla komponenter ligga i samma fil för bättre överblick. D.v.s gör detta steg allra sist*

1. Rita ett komponentträd för de komponenter som du har: App, Pokegame, Pokedex, Pokecard. 
2. Dela upp komponenterna i vardera modul (egen .jsx-fil)
* Lägg alla komponenter förutom App.jsx i en /components-folder i roten. 
* Importera funktionskomponenten i respektive modul - där den behövs enligt parent/child


# 😎 Bonus: Blackjack

Bygg en reactapp som automatisk delar ut 2 kort från en normal kortlek. Du kan också låta ett click-event hantera detta. 

Använd dig av Deck of Cards API för att hämta bilden för respektive kort.

`https://deckofcardsapi.com/static/img/9H.png)`

Regler, kortfattat: 

Alla klädda kort är värda 10 poäng. Ess är värt 1 eller 11 poäng. Skriv ut "Black Jack" om summan av de båda korten är 21.

![Blackjack](/blackjack.png)
