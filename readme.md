# Titre de readme.md

https://belmalika.github.io/MalikaFakenews92/

VISUALISATION FAITES PAR Malika BELHADJ ET Massissilia MERAKEB

voici le graphique de notre première visualisation: 

https://docs.google.com/spreadsheets/d/e/2PACX-1vTxUwZ2douMDjLkCG2QLTHhBDiltDKH8M4Qi8-rMuidu033mMVPW-8ZCoNH5RjwEPHcnqPZ2-bE05at/pubhtml?gid=283991522&single=true
On a collecté des données de Wikidata sous forme de sweets dont le contexte général consiste sur la pandémie de la COVID-19 et de l'importance des informations précises en temps de crise sanitaire, l'objectif de la visualisation, qui est de mettre en évidence la présence de fausses informations sur la COVID-19 dans les tweet, cela pourrait inclure le nombre de tweets, la fréquence des termes liés à la désinformation, ou d'autres mesures pertinentes.

voici notre deuxième visualisation: 

https://docs.google.com/spreadsheets/d/e/2PACX-1vSMXQSAZcTo3jQ56amp-ca-L9N1GqmTgOULR56jRMepVr3Zd8I6l95f2u2kRkf0_4DudMuJbTZDYZ-0/pubchart?oid=1051810006&amp;format=interactive">
Pour la deuxième 

voici notre troisème visualisation: 

https://docs.google.com/spreadsheets/d/e/2PACX-1vTJG9Q4OkjPWciwYyKzZsQk-CqOvOfj1XooZbHJMOiuMFdfuLu5YCHzdBDFi2iBbwIY4xcxFpCHxaKo/pubchart?oid=1362692641&amp;format=interactive
Et pour la troisième on pris le nombre de mortalité (de décès) dans certaines villes d'europe pour les personnes atteinte plus de 65 ans.

https://query.wikidata.org/embed.html#SELECT%20%3Fd%C3%A9sinformation_sur_la_pand%C3%A9mie_de_maladie_%C3%A0_coronavirus_de_2019_2020%20%3Fd%C3%A9sinformation_sur_la_pand%C3%A9mie_de_maladie_%C3%A0_coronavirus_de_2019_2020Label%20WHERE%20%7B%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%20%20%3Fd%C3%A9sinformation_sur_la_pand%C3%A9mie_de_maladie_%C3%A0_coronavirus_de_2019_2020%20wdt%3AP921%20wd%3AQ85173778.%0A%7D%0ALIMIT%20100" 

// https://github.com/eclipse/rdf4j
import org.eclipse.rdf4j.query.resultio.sparqljson.SPARQLResultsJSONWriter;
import org.eclipse.rdf4j.repository.RepositoryException;
import org.eclipse.rdf4j.repository.sparql.SPARQLRepository;
import java.util.Collections;

/**
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



