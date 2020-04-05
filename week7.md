#Week 7
[terug naar navigatie menu](Portfolio.md)

##Algemene reflectie
Voor deze week heb ik mijn gedrag van vorige week doorgezet en een duidelijke planning gemaakt en die actief bijgehouden gedurende de projectdag.
De groep werd verdeeld in drieëen en ik heb met Ralf samengewerkt.

##Inhoudelijke reflectie
Ik heb samen met Ralf gewerkt aan het optimaliseren van het tekenen van de map. Het programma werkte namelijk erg langzaam na het samenvoegen van de map en NPC's.
Ik kon op twee manieren dit probleem oplossen.

####Optie 1
Ik zou gebruik kunnen maken van twee canvassen. Een voordeel van deze oplossing is dat de map maar een keer getekend hoeft te worden totdat de camera veranderd.
Een groot nadeel echter is dat met het werken met twee canvassen niet bekend met mij noch Ralf was. Ook is de interactie tussen de twee canvassen lastig om te regelen.

####Optie 2
In plaats van dat iedere tile van iedere layer opnieuw moet worden getekend, kan de gehele map in een Buffered Image worden opgeslagen.
Dit heeft een voordeel dat het makkelijk te implementeren is door simpelweg een plaatje te tekenen. Ook is deze manier veel bekender voor mij en Ralf.
Maar door het gebruik te maken van deze BufferedImage moet er met een nieuw Graphics object te tekenen dan gebruikelijk is.

####Resultaat
Nadat ik heb overlegd met Ralf over onze keuzes zijn we het beide over eens om optie 2 te implementeren, het gebruik van een BufferedImage omdat dit de snelste en meest efficiënte manier is om dit probleem op te lossen.

Na het succesvol implementeren van optie twee, zijn Ralf en ik verder wezen werken aan het bugfixen van de camera.
Hier kwamen we echter niet uit.Om niet dezelfde fout te maken als vorige week heb ik mijn senior, Etiënne Goossens, gevraagd om hulp. Hierna was het probleem opgelost.