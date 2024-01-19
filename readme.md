# Titre de readme.md

https://belmalika.github.io/MalikaFakenews92/

VISUALISATION FAITES PAR Malika BELHADJ ET Massissilia MERAKEB

voici le graphique de notre première visualisation: 

https://docs.google.com/spreadsheets/d/e/2PACX-1vTxUwZ2douMDjLkCG2QLTHhBDiltDKH8M4Qi8-rMuidu033mMVPW-8ZCoNH5RjwEPHcnqPZ2-bE05at/pubhtml?gid=283991522&single=true

voici notre deuxième visualisation: 

https://docs.google.com/spreadsheets/d/e/2PACX-1vSMXQSAZcTo3jQ56amp-ca-L9N1GqmTgOULR56jRMepVr3Zd8I6l95f2u2kRkf0_4DudMuJbTZDYZ-0/pubchart?oid=1051810006&amp;format=interactive">

voici notre troisème visualisation: 

https://docs.google.com/spreadsheets/d/e/2PACX-1vTJG9Q4OkjPWciwYyKzZsQk-CqOvOfj1XooZbHJMOiuMFdfuLu5YCHzdBDFi2iBbwIY4xcxFpCHxaKo/pubchart?oid=1362692641&amp;format=interactive

# pip install sparqlwrapper
# https://rdflib.github.io/sparqlwrapper/

import sys
from SPARQLWrapper import SPARQLWrapper, JSON

endpoint_url = "https://query.wikidata.org/sparql"

query = """SELECT ?désinformation_sur_la_pandémie_de_maladie_à_coronavirus_de_2019_2020 ?désinformation_sur_la_pandémie_de_maladie_à_coronavirus_de_2019_2020Label WHERE {
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
  ?désinformation_sur_la_pandémie_de_maladie_à_coronavirus_de_2019_2020 wdt:P921 wd:Q85173778.
}
LIMIT 100"""


def get_results(endpoint_url, query):
    user_agent = "WDQS-example Python/%s.%s" % (sys.version_info[0], sys.version_info[1])
    # TODO adjust user agent; see https://w.wiki/CX6
    sparql = SPARQLWrapper(endpoint_url, agent=user_agent)
    sparql.setQuery(query)
    sparql.setReturnFormat(JSON)
    return sparql.query().convert()


results = get_results(endpoint_url, query)

for result in results["results"]["bindings"]:
    print(result)

