# Cascade Layers

In dit artikel ga ik het hebben over CSS Cascade Layers. Dit onderdeel van CSS kwam ik tegen terwijl ik aan het kijken was naar wat er allemaal nieuw is op het gebied van CSS en het leek mij erg interessant om hier meer over te weten te komen. Als developer ben je veel bezig met het bedenken hoe je code nou eigenlijk gaat schrijven. Ik probeer vaak voordat ik met het schrijven van CSS ga beginnen een lijstje te maken van wat voor hoofdonderdelen ik in het ontwerp dat ik na ga maken zie. Met dit lijstje kan ik vaak een goede start maken met het opzetten van een net CSS-document. Wanneer ik dit niet doe of wanneer ik in een ouder project met verschillende CSS-bestanden ga werken kan het zijn dat ik tegen specificiteit problemen ga aanlopen. Hierdoor kan het zijn dat ik dingen ga proberen te overschrijven met !important wat waarschijnlijk niet nodig is.

Daarom is er nu een nieuwe CSS-feature waarmee je lagen in je CSS-bestand kan aanmaken, genaamd Cascade layers. Haal dit niet in de war met lagen die gebruikt met z-index, dit is namelijk het visueel op elkaar zetten van lagen. Cascade layers gaat over het schrijven van je code in lagen.

## Wat is CSS Cascade Layers?

Met CSS Cascade Layers verdeel je je CSS-bestand op in verschillende lagen, dit helpt je de controle te behouden wanneer de stijling die je schrijft anderen overschrijven. Hierbij wordt het probleem opgelost dat je bij het stijlen de selector steeds specifieker gaat maken, niet om een kleinere selectie elementen te pakken, maar om stijling die al op het element staat te overschrijven.

Een voorbeeld:

Je hebt een stuk tekst deze zitten in een p element met daarom een aantal classes. Je pakt de eerste class.

```css
.text {
  color: hotpink;
}
```

Nadat je deze stijling hebt toegevoegd zie je dat deze niet wordt gepakt. In de inspector zie je dat de tekst al eens eerder is gestijld met de tagname van het element vervolgd met een classname. Dit heeft een hogere specificteit dan stijling met maar alleen een classname, waardoor je de tagname ook aan het element gaat toevoegen om ervoor te zorgen dat het element goed wordt gestijld.

```css
p.text {
  color: darkgray;
}
```

Door het gebruiken van Cascade Layers kun je deze specificiteit problemen vermijden.

## Hoe werkt de CSS Cascade eigenlijk?

De cascade is een algoritme dat definieert in welke volgorde declaraties moeten worden gelezen.

Eerst is het handig om de basisprincipes van cascade lagen te begrijpen. Wanneer je namelijk je website in de browser opent worden er namelijk stijlen samengesteld van drie primaire lagen:

- User agent styles -> De stijling die door de browser wordt meegegeven.
- User styles -> Stijling die mogelijk door de browser wordt toegestaan, zoals standaardkleuren of lettertype.
- Author styles -> De stijling die jij aan de website mee geeft.

De author styles is de hoogste die de twee andere kan overschrijven, zodat jij je website kan maken zoals jij wilt.

Als volgende heb je de cascade sorting order hierbij wordt gekeken welke stijling er wordt toegepast. Er wordt per onderdeel gekeken of er stijling is die daarbij hoort zo niet dan wordt er naar de volgende gekeken totdat er een is gevonden die wint.

De volgorde gaat als volgt:

1. Oorsprong en wat is het belangrijkste
2. Context
3. Stijling dat aan een element is toegevoegd, zoals
   ```html
   <h1 style="”color:red”">Hello</h1>
   ```
4. Specificity
5. Volgorde van plaatsing -> De laatste wint

Wanneer cascade layers worden gebruikt wordt de volgorde als volgt:

1. Oorsprong en wat is het belangrijkste
2. Context
3. Stijling dat aan een element is toegevoegd, zoals
   ```html
   <h1 style="”color:red”">Hello</h1>
   ```
4. Cascade Layers
5. Specificity
6. Volgorde van plaatsing -> De laatste wint

Het gebruiken van Cascade layers geven je de controle over specificiteit en volgorde weer terug.

## Hoe kun je CSS Cascade Layers gebruiken?

Een layer kun je op verschillende manieren aanmaken. Let er wel op dat de volgorde waarin je de lagen zet ertoe doet. Hier kom ik later terug eerst laat ik zien hoe je op verschillende manieren layers kunt aanmaken.

De eerste manier is door @layer met daarachter de naam die je aan de layer wilt toevoegen, met daarin dan meteen alle CSS die je in die layer wilt hebben. Het is niet verplicht om een layer een naam te geven, maar wanneer je dit niet doet kun je niet later in een bestand opnieuw een layer benoemen om iets toe te voegen aan die layer.

```css
@layer naam {
   H1 {
       …
   }
}
```

Een andere manier hoe je @layers aan kunt maken is door eerst helemaal boven aan het bestand alle layers die je wilt gaan gebruiken te benoemen. Dit doe je als volgt:

```css
@layer reset, base, theme, components;
```

De laatste manier om een layer aan te maken van een bestand bijvoorbeeld van een framework is doormiddel van @import. Dit doe je als volgt:

```css
@import url(bootstrap.css) layer(bootstrap);
```

Wanneer je meerdere keren @import wilt gebruiken moet je deze altijd bij elkaar zetten, anders wordt degene die na een @layer staat niet uitgevoerd. Hier een voorbeeld hoe je het wel en niet moet doen:

Hoe je het niet moet doen:

```css
@layer bootstrap, framework, reset, theme, components;

@import url(bootstrap.css) layer(bootstrap);

@layer reset {
    Body {
        …
    }
}

@import url(framework.css) layer(framework);
```

Hoe je het wel moet doen:

```css
@layer bootstrap, reset, theme, components;

@import url(bootstrap.css) layer(bootstrap);
@import url(framework.css) layer(framework);

@layer reset {
    Body {
        …
    }
}
```

## Nesten van Cascade Layers

Met `@layer` kun je ook nesten, dit kan op verschillende manieren.

Manier 1:

```css
@layer framework {
  @layer rest, base, components;
}
```

Manier 2:

```css
@layer framework.reset {
    .text {
        …
    }
}
```

Manier 3:

```css
@layer framework.reset, framework.base, framework.components;
```

## Overschrijven van stijling in cascade layers

Als je al een aantal layers hebt aangemaakt en daarna maak je nieuwe layers aan dan hebben de nieuwe layers meer prioriteit. Dit kan ervoor zorgen dat elementen die je al in een eerdere layer hebt gestijlt en nog een keer misschien in een latere layer nog een keer benoemd wordt overschreven, ook al heeft de selector in een eerdere layer een betere selector.

Bij het nesten in een @layer is dit niet zo daar geld wel dat wanneer de selector specifieker is, dat die dan wordt gepakt.

Een voorbeeld:

```css
@layer base {
  Header h1 {
    color: red;
  }
}

@layer components {
  H1 {
    color: hotpink;
  }
}
```

De h1 wordt nu hotpink doordat deze als laatste layer staat die de header h1 in eerder layer overschrijft.

## Styling outside a @layers

Wanneer je stijling buiten een @layer zet winnen deze het van de stijling die in de @layer staat. Omdat deze als laatste worden gelezen en dat betekent dat wat in de @layer wordt overschreven.

## !important

Indien je in een van je layers !important gebruikt, dan veranderd de hele specificerings volgorde. Als je bijvoorbeeld in de eerste @layer de h1 een color: blue geeft met daarachter !important, dan wordt dit de belangrijkste en wordt de h1 blauw. Ook al zet je in een latere @layer dat de h1 groen moet zijn met daarbij !important. Door !important draaien namelijk de lagen om.

## Conclusie

Ik hoop dat je na het lezen van dit artikel meer te weten bent gekomen over Cascade layers en dat je het misschien ook gaat gebruiken. Zelf zou ik het niet snel in kleine projecten waar alleen ik zelf aan werk gebruiken, maar het lijkt mij wel erg handig om te gebruiken in bijvoorbeeld team projecten of grote projecten. Om op deze manier een beter overzicht te krijgen.

## Bronnen:

Damme, B.V. (2022) The future of CSS: Cascade Layers (CSS&nbsp;@layer), Bram.us. Available at: https://www.bram.us/2021/09/15/the-future-of-css-cascade-layers-css-at-layer/ (Accessed: May 2, 2023).

Eckles, S. (2022) Getting started with CSS cascade layers, Smashing Magazine. Available at: https://www.smashingmagazine.com/2022/01/introduction-css-cascade-layers/ (Accessed: May 2, 2023).

No more specificity issues?! (or all new ones 🤔) - A look at CSS Cascade Layers (2022) YouTube. YouTube. Available at: https://www.youtube.com/watch?v=NDNRGW-_1EE (Accessed: May 2, 2023).
