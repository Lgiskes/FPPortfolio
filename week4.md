#Week 4
[terug naar navigatie menu](Portfolio.md)

##Algemene Reflectie
De eerste dag van deze week hadden we een beoordeling van de agenda module.
In het algemeen werkte deze best goed, maar miste een paar functies, zoals het aanpassen van artiesten en shows.
Deze week heb ik samen met een paar groepsleden de leden aangesproken die vorige week niet veel aan de agenda hebben gewerkt.
Ze leken de booschap goed te ontvangen en we hebben afgesproken eerder te communiceren als er iets fout dreigt te gaan. 

##Inhoudelijke Reflectie
Terwijl de ene helft van de groep is begonnen aan het ontwerp van het lezen van de map, ben ik bezig geweest om het opslag systeem te verbeteren.
Toen ter tijd was er gebruik gemaakt van Gson en ik begreep niet hoe dat werkte. Ik heb met de groep overlegd hoe we de opslag wilde veranderen.
Uit dit overleg hebben we besloten om over te stappen  naar Json. Ik zou dit implementeren.
Ik heb bijna alle code betreffende Gson verwijderd en van nul begonnen om de planner op te kunnen slaan. Omdat ik niet eerder met Json heb gewerkt was dit even wennen hoe ik het moest gebruiken. Maar na onderzoek te hebben gedaan ben ik er snel achter gekomen.
Aan het eind van de dag was het nieuwe opslag format gereed. Hier volgt de code van de opslag van de planner in Json:  
````
    public void savePlanner() {
        try {
            JsonWriter writer = Json.createWriter(new FileWriter(saveFileName));
            JsonObjectBuilder plannerBuilder = Json.createObjectBuilder();
            JsonArrayBuilder showsBuilder = Json.createArrayBuilder();
            JsonArrayBuilder stagesBuilder =  Json.createArrayBuilder();
            JsonArrayBuilder artistsBuilder = Json.createArrayBuilder();

            for(Stage stage : this.getStages()){
                JsonObjectBuilder stageBuilder = Json.createObjectBuilder();
                stageBuilder.add("name",stage.getName());
                stageBuilder.add("capacity", stage.getCapacity());
                stagesBuilder.add(stageBuilder);
            }

            for(Artist artist : this.getArtists()){
                JsonObjectBuilder artistBuilder = Json.createObjectBuilder();
                artistBuilder.add("name", artist.getName());
                artistBuilder.add("description", artist.getDescription());
                artistBuilder.add("genre", artist.getGenre().getFancyName());
                artistsBuilder.add(artistBuilder);
            }

            for(Show show : this.getShows()){
                JsonArrayBuilder showArtistsBuilder = Json.createArrayBuilder();
                JsonObjectBuilder showBuilder = Json.createObjectBuilder();
                JsonObjectBuilder stageBuilder = Json.createObjectBuilder();

                for(Artist artist : show.getArtists()){
                    JsonObjectBuilder artistBuilder = Json.createObjectBuilder();
                    artistBuilder.add("name", artist.getName());
                    artistBuilder.add("description", artist.getDescription());
                    artistBuilder.add("genre", artist.getGenre().getFancyName());
                    showArtistsBuilder.add(artistBuilder);
                }
                Stage stage = show.getStage();
                stageBuilder.add("name",stage.getName());
                stageBuilder.add("capacity",stage.getCapacity());

                showBuilder.add("name", show.getName());
                showBuilder.add("artists", showArtistsBuilder);
                showBuilder.add("stage", stageBuilder);
                showBuilder.add("beginTime", show.getBeginTimeString());
                showBuilder.add("endTime", show.getEndTimeString());
                showBuilder.add("description",show.getDescription());
                showBuilder.add("genre",show.getGenre().get(0).getFancyName());
                showBuilder.add("expectedPopularity", show.getExpectedPopularity());
                showsBuilder.add(showBuilder);
            }
            plannerBuilder.add("shows",showsBuilder);
            plannerBuilder.add("artists", artistsBuilder);
            plannerBuilder.add("stages",stagesBuilder);

            writer.writeObject(plannerBuilder.build());
            writer.close();


        } catch (IOException e) {
            e.printStackTrace();
   ````