# CSS DAY 2023

Afgelopen donderdag en vrijdag ben ik naar CSS Day geweest. Dit is de enige conferentie die alleen maar gaat over CSS. Gedurende deze conferentie heb ik naar verschillende talks geluisterd. In dit artikel ga ik het eerst hebben over een aantal talks die ik heb gevolgd en daarna ga ik het hebben over mijn ervaringen met de conferentie.

## State of the CSS community door Una Kravets

De eerste talk die ik heb gevolgd was van Una Kravets. Eerst vertelde zij over wat er in de afgelopen 2.5 jaar allemaal is veranderd in CSS. Zo kunnen we nu gebruik maken van aspect-ratio, dynamic viewport units, individuele transforms (translate, scale en rotate) en cascade layers met @layer (waarover je [hier](https://github.com/Inevdhoven/weekly-nerd/blob/main/articles/article-1.md) meer kunt lezen in een artikel dat ik eerder heb geschreven).

Ook vertelde Una over wat er in de toekomst gaat komen en wat er al bijna is. Zo zijn ze nu hard aan het werk om er voor te zorgen dat we kunnen gaan nesten in CSS, wat je nu bijvoorbeeld met Sass kan.

Before nesting:

```css
nav {
  background-color: hotpink;
}

nav > ul {
  background-color: lightblue;
}

nav > ul > li {
  color: deeppink;
}
```

After nesting:

```css
nav {
  background-color: hotpink;

  > ul {
    background-color: lightblue;

    > li {
      color: deeppink;
    }
  }
}
```

Dan zijn ze op het moment ook veel bezig met het uitbereiden/verbeteren van de kleuren in CSS, met onderandere oklcd en lch. Deze kleuren zijn nu nog niet overal te gebruiken, maar ze zijn er wel mee bezig. Daarnaast zijn ze ook bezig met text-wrap: balance, wat ervoor zorgt dat je tekst mooi verdeeld wordt over meerdere regels.

**`text-wrap: balance;`**

![text-wrap: balance image from https://developer.chrome.com/blog/css-text-wrap-balance/](https://wd.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/lnGFtchLIPk9RnHSurHg.png?auto=format&w=1600)
_image from https://developer.chrome.com/blog/css-text-wrap-balance/_

Verder ging het ook nog in het kort over style queries, waarmee je iets kunt stijlen op basis van de value van een custom property. Ook vertelde Una over state queries, waarmee je iets kunt stijlen op een propertie als bijvoorbeeld sticky.

Voor meer informatie over wat Una nog meer heeft verteld kun je de opname van de talk bekijken op YouTube.

## Dialogs & Popovers door Hidde de Vries

De tweede talk die ik heb gevolgd was van Hidde de Vries. Hij vertelde over wanneer je een dialog en wanneer je een popover kunt gebruiken. Hier wat meer informatie over dialogs en popovers.

Een dialog is een extra window tot je main window dat je opent. Deze kun je nu doormiddel van het HTML element `<dialog>` aanmaken, die je dan met element.showModal() of element.show() in de JavaScript te voorschijn kunt laten komen. Eerder kon je dit doen doormiddel van `<div role="dialog">`. Maar dan moest je zelf de behavior schrijven.

**Een voorbeeld van een dialog die meteen open is:**

```html
<dialog open>
  <form method="dialog">
    <button type="submit" autofocus>Close dialog</button>
  </form>
</dialog>
```

Een popover is een zwevend UI element wat bijvoorbeeld een color picker of date picker kan zijn. Hier heb je geen JavaScript voor nodig. Je kunt de popover als volgt maken:

```html
<button popovertarget="my-popover">Open Popover</button>

<div popover id="my-popover">Hello World!</div>
```

Voor meer informatie over wat Hidde nog meer heeft verteld kun je de opname van de talk bekijken op YouTube.

## Modern CSS Development Tooling & Workflows door Umar Hansa

Op de tweede dag heb ik een talk gevolgd van Umar Hansa over tooling en workflows. In deze talk vertelde hij over een aantal handige tools die je kunt gebruiken in VScode, om je workflow te verbeteren. Zo maakt Umar veel gebruik van Alfred, dit is een tool om je workflow mee te verbeteren en helpt je om sneller toegang te bieden tot verschillende taken. Hier een aantal voorbeelden van wat je allemaal met Alfred kunt doen:

1. Je kunt zelf sneltoetsen en workflows aanmaken, waarmee je bijvoorbeeld meerdere programma's met een sneltoets kunt openen.
2. Alfred slaat op wat je eerder hebt gekopieerd, waardoor je het later nog een keer kunt terug vinden en gebruiken.
3. Je kunt ook tekstsnippets aanmaken, waarmee je een stuk tekst die je vaak gebruikt met een sneltoets kunt invoegen. Op deze manier hoe je dat stuk tekst niet steed opnieuw ergens vandaan te kopiëren en plakken.

Alfred is een betaalde tool, maar er zijn ook een aantal gratis opties als Raycast en Espanso.

Daarna vertelde Umar over AI tools hier noemde hij een aantal tools die handig zijn om te gebruiken. Zo had hij het over Bloop.ai en Copilot Chat. Bloop.ai is een code search engine, in de vorm van een desktop app die je kunt gebruiken om code van GitHub te koppelen en wanneer dit is gesynchroniseerd kun je hierin zoeken. Copilot Chat is een extention op GitHub Copiolot, waarmee je kunt chatten met de AI van GitHub Copilot. Je kunt er vragen aan stellen over code en deze dan ook meteen gebruiken.

Dan vertelde Umar ook dat er in DevTools heel veel keyboard shortcuts zitten, zo is bijvoorbeeld F7 + bg er een om de achtergrond aan te passen.

Verder vertelde hij nog meer over bijvoorbeeld DevTools, CSS performance tooling en Editor tips en Tricks. Meer hierover kun je in de opname zien op YouTube.

## Creative Coding door Jhey Tompkins

Op de vrijdag gaf Jhey Tompkins een presentatie met daarin vanalles wat hij heeft gemaakt met CSS. Zo heeft hij verschillende spelletjes gemaakt in CSS, zoals boter kaas en eieren en vier op een rij. Ook had hij een pagina gemaakt waar allemaal beertjes aan ballonnen hingen en daartussen moest je dan de gouden beer vinden en aanklikken. Het was echt mega leuk om te zien wat hij allemaal heeft gemaakt en het was ook inspirerend om te zien wat er allemaal mogelijk is met CSS.

Hier twee werken van Jhey Tompkins:

## Mijn ervaring op CSS Day

Dat was dan een samenvatting van een aantal talks die ik heb gevolgd. Nu ga ik jullie vertellen over mijn ervaring met CSS Day. Op donderdag kwamen we rond 08:45 uur aan bij de Zuiderkerk, waar CSS Day plaats vond. We mochten ons kaartje van de tafel pakken en daarna konden we boven een ontbijtje pakken. Boven lagen er allemaal croissantjes en drinken klaar. Rond 09:30 begon de eerste talk. Elke talk duurde ongeveer 50 minuten en daarna was er dan even een pauze. Er waren drie wat langere pauze waaronder de lunchpauze gedurenden de dag. Onder de langere pauzes stond er altijd wat de eten en drinken klaar. Bij de lunch kan je kiezen uit verschillende broodjes en een warme maaltijd. Na de laatste talk van de dag kon je nog blijven hangen en kon je wat te drinken halen.

In totaal waren er 14 talks, deze waren verdeeld over de twee dagen. Hier zaten veel talks tussen die ik erg interessant vond en ook een paar die ik niet geheel kon volgen, omdat ik er nog niet genoeg over wist of omdat het te ingewikkeld was. Van alle talks heb ik veel geleerd en ben ik ook geinspireerd geraakt om meer nieuwe CSS te gaan uitproberen en in mijn projecten te gaan gebruiken.

Ik vond het erg leuk om naar CSS Day te gaan en ik heb er veel van geleerd. Ik zou het dan ook zeker aanraden om een keer naar CSS Day te gaan als je de kans krijgt.

## Bronnen:

Werk van Jhey Tompkins: <br>
https://codepen.io/jh3y/pen/MWzwamV <br>
https://codepen.io/jh3y/pen/LYgjpYZ

Andere linkjes: <br>
https://bloop.ai/blog/introducing-bloop <br>
https://www.alfredapp.com/
