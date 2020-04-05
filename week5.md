#Week 5
[terug naar navigatie menu](Portfolio.md)

##Algemene reflectie
Deze week was chaotischer dan gewenst. Dit is gekomen omdat we het plan van aanpak in moesten leveren voor het einde van de week.
Dit bleek een groter probleem dan gewenst. Dit had ik kunnen zien aankomen. Ik had als planner af kunnen spreken om tijdens de vakantie af te spreken om aan het plan van aanpak te werken. Dit heb ik niet gedaan omdat ik de taak heb onderschat.
Hierdoor kwam de rest van het project onder druk te staan. Volgende keer moet ik duidelijk en optijd van tevoren afspreken met de groep over oplevermomenten.

##Inhoudelijke reflectie
De projectdag waren we grotendeels bezig aan het werken aan het plan van aanpak. Hierom heb ik niet heel veel gewerkt aan het project.
Wel heb ik Erwin geholpen met het ontwerp van de Person klasse en de indeling van de superGenres.
Ook heb ik bijgedragen met een functie maken voor het spawnen van NPC's en een werkende functie waarmee je een geluidje af kan spelen als je op een person klikt.
Dit was niet erg uitdagend omdat veel onderdelen terug zijn gekomen van het opstartcollege.
De code voor het spawnen van Persons:  
```` 
    public boolean canSpawn(Point2D spawnPosition){
        if(this.people.size() <= 0){
            return true;
        }
        for(Person person : people){
            if(spawnPosition.distance(person.getPosition()) < 64){
                return false;
            }
        }
        return true;
    }

    public void spawnPeople(int amount){
        int failedSpawnAttempts = 0;

        for(int i = 0; i < amount; i++) {
            int number = (int)(Math.random() * ((6 - 1) + 1)) + 1;
            Point2D newSpawnLocation = new Point2D.Double(Math.random()*1800, Math.random()*1000);
            if(canSpawn(newSpawnLocation)) {
                this.people.add(new Person(newSpawnLocation, number));
                failedSpawnAttempts = 0;
            }else {
                failedSpawnAttempts++;
                if(failedSpawnAttempts > amount*0.1){
                    return;
                }

            }
        }
    }
 ````