+++
title = 'Allemaal lijnen - patronen met lijnen. '
date = 2024-02-09T15:36:59+01:00
draft = true
+++

In deze tutorial gaan we aan de slag met het tekenen van lijnen, om zo patronen te maken. Op't eerste gezicht een beetje saai zal je denken. Ja, misschien wel, al hoop ik met dit artikel aan te tonen dat lijnen ook heel spannende patronen kunnen opleveren ;)

<!--more-->

## Een eerste paar patronen.
We zullen beginnen met een aantal eenvoudige dingen. Laat ons eerst ons canvas denkbeeldig indelen volgens vierkanten. Vervolgens tekenen we binnen de eerste rij vierkanten, telkens een lijntje dat het vierkant horizontaal mooi doormidden snijdt, en bij de volgende rij maken we daar een verticaal lijntje van.
We zullen eerst, om het wat visueel te maken, de vierkanten tekenen in een lichte kleur, alsof het "hulplijnen" zijn. We gebruiken een variabele ```lengteStreepje``` om de lengte van de streepjes te bepalen. Speel gerust eens met de waarde van deze variabele, en je zal grotere of kleinere vierkantjes zien verschijnen.

{{< p5 height="700" width="450">}}
let lengteStreepje = 20;

function setup() {
  createCanvas(400, 400);
  background(230);
  // omdat ons canvas vierkant is, zijn er evenveel streepjes
  // in horizontale en in vertikale richting
  let aantalStreepjesPerLijn = width / lengteStreepje;
  stroke(0);
  noFill();
  for (x = 0; x < aantalStreepjesPerLijn; x++) {
    for (y = 0; y < aantalStreepjesPerLijn; y++) {
      rect(x * lengteStreepje, y * lengteStreepje, lengteStreepje);
    }
  }
}

function draw() {}
{{< / p5 >}}

Laat ons nu de vierkanten vervangen door lijntjes, op de even rijen een horizontale lijn, op de oneven rijen een verticale lijn. Om te testen of we te maken hebben met een even of een uneven rij, kunnen we de ```y``` variabele in de binnenste ```for-loop``` delen door 2, en de rest van die deling bekijken. Is die 0, dan is het een even rij, bij 1 is dat een oneven rij. De rest van een deling bereken je in Javascript door ```y % 2``` te doen.

{{< p5 height="700" width="450">}}
let lengteStreepje = 20;

function setup() {
  createCanvas(400, 400);
  background(230);
  // omdat ons canvas vierkant is, zijn er evenveel streepjes
  // in horizontale en in vertikale richting
  let aantalStreepjesPerLijn = width / lengteStreepje;
  
  noFill();
  for (x = 0; x < aantalStreepjesPerLijn; x++) {
    for (y = 0; y < aantalStreepjesPerLijn; y++) {
    stroke(0);
     //rect(x * lengteStreepje, y * lengteStreepje, lengteStreepje);
      if (y % 2 == 0 ) { // een even rij, dus horizontaal streepje
        line(x * lengteStreepje, y * lengteStreepje + lengteStreepje / 2,  x*lengteStreepje + lengteStreepje, y * lengteStreepje + lengteStreepje / 2);
      }
      else {
                line(x * lengteStreepje+lengteStreepje/2, y * lengteStreepje,  x * lengteStreepje+lengteStreepje/2, y * lengteStreepje + lengteStreepje);
      }
    }
  }
}

function draw() {}


{{< / p5 >}}
