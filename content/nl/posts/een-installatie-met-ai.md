---
title: "Een Installatie Met AI"
date: 2024-03-09T11:56:16+01:00
tags: ['artificiële intelligentie', 'installatie', 'interactieve kunst', 'tutorial']
featured_image: "/images/posts/vierkanten.png"
description: "Laat stoom uit de oren van je toeschouwers komen."
draft: true
---
In een [vorige post]({{< ref "rook-simulatie.md" >}}) zag je hoe je een rooksimulatie kunt maken. In deze post gaan we daarop verderwerken: we gaan het spreekwoord "_er komt stoom uit zijn oren_" even heel letterlijk nemen :) We gaan daarvoor een AI-model gebruiken om beelden gemaakt met onze webcam te herkennen.

<!--more-->
## Posenet - herkennen van lichaamshoudingen
Uit het artikeltje over de rooksimulatie weten we hoe we rook kunnen laten opstijgen. In dat artikel lieten we die rook opstijgen vanaf de plaats waar je met de muis klikte. Dat gaan we wat moeten aanpassen: we willen immers de rook laten vertrekken vanaf de oren. Daartoe zullen we gebruik moeten maken van een webcam en van een AI-model dat houdingen van een lichaam kan herkennen. Gelukkig moeten we dat laatste niet zelf bouwen: er is een model _Posenet_ dat op basis van een foto 17 verschillende onderdelen van een lichaam kan herkennen. Denk aan dingen zoals neus, oren, linkerschouder, enz. Kijk zeker eens naar [dit artikel](https://medium.com/tensorflow/real-time-human-pose-estimation-in-the-browser-with-tensorflow-js-7dd0bc881cd5) voor wat extra uitleg. 

Gelukkig moeten we niet teveel dingen afweten van machine learning om dit model te kunnen gebruiken. Er bestaat een makkelijk te gebruiken bibliotheek (ml5.js)[https://learn.ml5js.org/#/] die het simpel maakt om dit AI-model te gebruiken.

## Aan de slag
Het eerste wat we moeten doen, is de webcam gebruiken in onze sketch. In p5js is kan dat gemakkelijk met de ```createCapture()```-functie. Die kan de beelden van je webcam vastpakken en je daarop laten werken. Hieronder zie je een sketch die het webcam beeld capteert en tekent op een canvas.


