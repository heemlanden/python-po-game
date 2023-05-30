# Python Game PO

## Beschrijving opdracht

In deze PO laat je zien dat je met behulp van de Pygame package een eenvoudig spelletje kunt maken in Python. Zo laat je zien:

* hoe je een main game loop maakt
* hoe je iets tekent op het scherm
* hoe je een element kunt laten bewegen
* hoe je gebruikersinput verwerkt
* hoe je zorgt dat spelelementen niet 'van het scherm lopen'
* hoe je botsingen detecteert
etc.

## Hoe deze repository te gebruiken

Je kunt met Github Desktop deze repository clonen. De bedoeling is dat je vervolgens de basisgame Pong (in [`pong.py`](pong.py)) verder uitbouwt naar eigen inzicht.
Hieronder zie je daarvoor een aantal opties en tips:

## Pygame tips voor kleuren, tekst en geluiden

### Kleuren gebruiken

Je kunt een van de vele [voorgedefinieerde kleuren](https://www.pygame.org/docs/ref/color_list.html) gebruiken, bijvoorbeeld als volgt:

```python
blue_color = pygame.Color('blue')
```

Of je kunt een eigen kleur maken met behulp van rood, groen en blauw (gebruik een [RGB Color Picker](https://www.w3schools.com/colors/colors_rgb.asp)):

```python
my_green = (121,204,97)
```

Nadat je de kleur gemaakt hebt (een tuple met 3 of 4 getallen, nl. rood, groen en blauw en optioneel transparantie) kun je die gebruiken in tekencommando's, bijvoorbeeld als volgt:

```python
pygame.draw.rect(screen, light_grey, player)
```

### Tekst tekenen

Je kunt teksten schrijven in het spelvenster, bijvoorbeeld om een score weer te geven.
Dit doe je in 3 stappen:

1. Definieer een font (boven de game loop)

```python
basic_font = pygame.font.Font('freesansbold.ttf', 32)
```

2. Schrijf de tekst op een vlak met behulp van het font object

```python
textbox = basic_font.render("tekst",False,blue_color)
```

Het tweede argument geeft aan of [antialiasing](https://nl.wikipedia.org/wiki/Anti-aliasing_(digitale_beeldverwerking)) toegepast moet worden om kartelrandjes af te zwakken.
Zie ook de documentatie van [`Font.render()`](https://www.pygame.org/docs/ref/font.html#pygame.font.Font.render).

3. Teken het tekstvlak op het spelscherm

```python
screen.blit(textbox,(400,200))
```

De [`Surface.blit()`](https://www.pygame.org/docs/ref/surface.html?highlight=blit#pygame.Surface.blit) functie zal de tekst tekenen op een positie in het scherm (hier `screen`).
De linkerbovenhoek bevindt zich in dit voorbeeld op `x = 400, y = 200`.

### Geluid toevoegen

1. Initialiseer de mixer:

Een geluid kun je toevoegen via een mixer. In de setup-code bovenaan je programma intialiseer je die:

```python
pygame.mixer.pre_init(44100,-16,1, 1024)
```

2. Laad het geluid in uit een geluidsbestand:

Vervolgens kun je geluiden maken door een geluidsbestand in te lezen.
De geluidsbestanden [`pong.ogg`](pong.ogg) en [`score.ogg`](score.ogg) zijn bijgevoegd, maar je kunt ook andere geluidsbestandjes vinden op [internet](https://opengameart.org/content/library-of-game-sounds). Of je kunt er zelf een opnemen met een tool als Audacity.

```python
score_sound = pygame.mixer.Sound("score.ogg")
```

3. Speel het geluid op het juiste moment af:

```python
pygame.mixer.Sound.play(score_sound)
```

## Inleveren van de opdracht

Tot slot beantwoord je nog de volgende vragen in het bestand [`vragen.md`](vragen.md):

* 'Op welk stukje code ben jij trots?'
* 'Wat vond je moeilijk aan deze opdracht?'.

Met de beantwoording van deze vragen kun je 2 punten verdienen. Als je hier mee klaar bent, lever je het in door alle wijzigingen te committen en te pushen in Github Desktop!
