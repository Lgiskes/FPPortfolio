#Week 8
[terug naar navigatie menu](Portfolio.md)

##Algemene reflectie
Ongeacht te aparte omstandigheden tot betrekking met de uitbraak van het corona-virus is iedereen bijelkaar gekomen in een Discord room om de laatste paar dingen af te ronden.
Ook deze week heb ik doorgezet om een planning en todo lijst bij te houden voor de laatste paar dagen.
Hier heb ik ook een prioriteits waarde bijgezet zodat de focus op het succesvol afronden van het project niet verslapt.

##Inhoudelijke reflectie
Het product werkt nu grotendeels daarom heb ik me deze week vooral gebogen over de code netter maken en een paar "quality of life" verbeteringen te maken.
Dingen zoals het toevoegen van de functionaliteit van de stage capacity. Met deze functionaliteit gaan er niet meer bezoekers naar een show als er meer bezoekers dan de capaciteit van de show erheen gaan.
Hier volgt code hiervoor:  
````
    public PopularityTracker() {
        peopleAtShows = new HashMap<>();
        ArrayList<Show> activeShows = DataController.getInstance().getPlanner().getActiveShows();
        for (Show show : activeShows) {
            peopleAtShows.put(show, 0);
        }
    }

    /**
     * Looks if there is room for one extra visitor in a show,
     * if there is room: add one to the amount of people going to the show and return true
     * Otherwise return false
     *
     * @param show the show the visitor wants to go to
     * @return true if there is room, false if the show is full
     */
    boolean canGoToShow(Show show) {
        for (Show activeShow : peopleAtShows.keySet()) {
            if (show.equals(activeShow)) {
                if (show.getStage().getCapacity() >= peopleAtShows.get(show) + 1) {
                    peopleAtShows.put(show, peopleAtShows.get(show) + 1);
                    return true;
                }
            }
        }

        return false;
    }
````