#Week 3
[terug naar navigatie menu](Portfolio.md)

##Algemene reflectie
Het begin van deze week begon weer goed, er was een duidelijke takenverdeling gemaakt en iedereen was maandag goed aan het werk.
Echter begon in de midden van de week miscommunicaties te ontstaan. Voor het einde van de week moest de agenda module af zijn, maar bleek niet voldoende te zijn afgerond na de eerste projectdag.
Ik heb geprobeerd in deze week afspraken te maken om nog eenmaal bijelkaar te komen, maar niet iedereen is komen opdagen. 
Volgende keer moet ik de afwezige groepsgenoten hierop aanspreken zodat we niet nogeens met een paar leden veel werk moeten doen.

##Inhoudelijke reflectie
Deze week heb ik vooral gewerkt aan de logica van het toevoegen van shows. 
Dit houdt in dat ik de elementen van de GUI heb uitgelezen en vervolgens om heb gezet naar een Show.
Dit ging niet zonder problemen, de comboboxen van de tijd lezen en omzetten naar een LocalTime ging niet goed.
Daarvoor heb een aparte functie moeten schrijven die de index van de combobox omzet naar een LocalTime.
Ik heb gekozen om gebruik te maken van de index omdat een index altijd een vaste waarde van tijd had.
Hier volgt de code:  
```
     public LocalTime indexToLocalTime(int index){
        LocalTime time = LocalTime.MIDNIGHT;
        int hours = index / 2;
        if(index % 2 == 1){
            time = time.plusMinutes(30);
        }
        time = time.plusHours(hours);
        return time;
    }
   ```
   
    
