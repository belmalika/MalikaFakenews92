# Titre de readme.md

https://belmalika.github.io/MalikaFakenews92/

VISUALISATION FAITES PAR Malika BELHADJ ET Massissilia MERAKEB

voici le graphique de notre première visualisation: 

https://docs.google.com/spreadsheets/d/e/2PACX-1vTxUwZ2douMDjLkCG2QLTHhBDiltDKH8M4Qi8-rMuidu033mMVPW-8ZCoNH5RjwEPHcnqPZ2-bE05at/pubhtml?gid=283991522&single=true

voici notre deuxième visualisation: 

https://docs.google.com/spreadsheets/d/e/2PACX-1vSMXQSAZcTo3jQ56amp-ca-L9N1GqmTgOULR56jRMepVr3Zd8I6l95f2u2kRkf0_4DudMuJbTZDYZ-0/pubchart?oid=1051810006&amp;format=interactive">

voici notre troisème visualisation: 

https://docs.google.com/spreadsheets/d/e/2PACX-1vTJG9Q4OkjPWciwYyKzZsQk-CqOvOfj1XooZbHJMOiuMFdfuLu5YCHzdBDFi2iBbwIY4xcxFpCHxaKo/pubchart?oid=1362692641&amp;format=interactive



 * Wikidata RDF4J SPARQL example
 */
public class App
{
    public static void main( String[] args )
    {
        String sparqlEndpoint = "https://query.wikidata.org/sparql";
        SPARQLRepository repo = new SPARQLRepository(sparqlEndpoint);

        String userAgent = "Wikidata RDF4J Java Example/0.1 (https://query.wikidata.org/)";
        repo.setAdditionalHttpHeaders( Collections.singletonMap("User-Agent", userAgent ) );

        String querySelect = "SELECT ?désinformation_sur_la_pandémie_de_maladie_à_coronavirus_de_2019_2020 ?désinformation_sur_la_pandémie_de_maladie_à_coronavirus_de_2019_2020Label WHERE {\n" +
                "  SERVICE wikibase:label { bd:serviceParam wikibase:language \"[AUTO_LANGUAGE],en\". }\n" +
                "  ?désinformation_sur_la_pandémie_de_maladie_à_coronavirus_de_2019_2020 wdt:P921 wd:Q85173778.\n" +
                "}\n" +
                "LIMIT 100";

        try{
            repo.getConnection().prepareTupleQuery(querySelect).evaluate(new SPARQLResultsJSONWriter(System.out));
        } catch ( Exception exception ) {
            exception.printStackTrace();
        }

    }
}


