#Week 6
[terug naar het navigatie menu](Portfolio.md)

##Algemene reflectie
Deze laatste officiële project vergadering was erg slecht uitgevoerd. Er was niet goed voorbereid voor deze vergadereing.
Ook ik heb grote fouten gemaakt. De planning die ik heb opgesteld was niet concreet en niet compleet.
Ook was het probleem van vorige week niet geadresseerd. Na deze feedback terug te krijgen van mijn tutor, Pieter Kop Jansen.
Erg teleurgesteld in mezelf, heb ik voorgenomen om na deze vergadering samen alles recht te zetten door een goede vergadering te houden.
We hebben een duidelijke planning gemaakt en vanaf dit moment ging alles beter. De communicatie ging goed en iedereen deed actief zijn werk.
Om te compenseren van vorige week heb ik deze week meer gedaan dan normaal.

##Inhoudelijke reflectie
Deze week heb ik de logica van het route volgen en gedrag van de Persons.
Dit vond ik zelf het leukste onderdeel van het project, maar ook het meest uitdagende.
Mijn taak was om met behulp van een DistanceMap en een WalkableMap Persons laten lopen over het veld.
Dit heb ik op meerdere manieren kunnen doen:  
####Optie 1
Ik zou gebruik kunnen maken van een vector map, dat is een map waarin met behulp van een distancemap een richting wordt opgeslagen per tile.
Een groot voordeel hiervan is dat het heel weinig rekenkracht kost om personen van tile naar tile hoeft te verplaatsen omdat je bij het opstarten van de applicatie de Vectormap in kan laden.
Een nadeel is dat je al een distancemap klasse klaar hebt moeten liggen.

####Optie 2 
In plaats van de vector map, kan ik gebruik maken van een klasse die voor iedere persoon de nieuwe positie uitrekent.
Een voordeel is dat je makkelijk aanpassingen kan maken van het bewegingsgedrag en hiermee is de kans veel kleiner dat de personen lopen op plekken waar ze niet mogen komen.
Een nadeel is dat het meer logica en rekenkracht kost.

####Resultaat
Ik heb uiteindelijk gekozen voor optie 2 omdat ik graag een flexibele oplossing wil verzinnen wat makkelijk aanpasbaar is.  

####Uitvoering
Ik heb een klasse genaamd PathCalculator aangemaakt om het gedrag van Persons te berekenen. Iedere keer als een person op een nieuwe tile is krijgt het persoon een commando om een nieuwe tile op te zoeken.
Als het persoon aan is gekomen op de eindbestemming krijg het persoon een nieuwe distancemap aangeboden en begint zo opnieuw.
Hier volgt de code voor het opzoeken van een nieuwe tile:  
````
    static Point2D nextPositionToTarget(Point2D currPos, DistanceMap distanceMap) {
        double tileSize = MapDataController.getTileSize();

        int xIndex = (int) Math.floor(currPos.getX() / tileSize);
        int yIndex = (int) Math.floor(currPos.getY() / tileSize);

        Point2D middlePointCoords = new Point2D.Double(distanceMap.getTarget().getMiddlePoint().getX() * tileSize, distanceMap.getTarget().getMiddlePoint().getY() * tileSize);

        if (middlePointCoords.distance(currPos) <= tileSize) {
            return new Point2D.Double(-100, -100);
        }

        int lowest = Integer.MAX_VALUE;
        int lowestIndexX = Integer.MAX_VALUE;
        int lowestIndexY = Integer.MAX_VALUE;

        int maxX = MapDataController.getMapWidth(), maxY = MapDataController.getMapHeight();

        for (int yOffset = -1; yOffset <= 1; yOffset++) {
            for (int xOffset = -1; xOffset <= 1; xOffset++) {
                int currX = xIndex + xOffset;
                int currY = yIndex + yOffset;
                if (currX > -1 && currX < maxX - 1 && currY > -1 && currY < maxY - 1) {
                    int value = distanceMap.getMap()[currX][currY];
                    if (value < lowest) {
                        lowest = value;
                        lowestIndexX = currX;
                        lowestIndexY = currY;
                    }
                }
            }
        }

        return new Point2D.Double(lowestIndexX * tileSize + tileSize * 0.5, lowestIndexY * tileSize + tileSize * 0.5);
    }
   ````
   #### Reflectie
   Het was erg leuk om alleen te stoeien met dit probleem, maar daardoor ben ik wel langer bezig geweest wanneer ik met iemand samen zou werken.
   Dus voor de volgende keer zal ik om hulp vragen als ik merk dat ik voor een langere tijd vast loop.
  
    
