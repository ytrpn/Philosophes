
SELECT Distint ?person ?personLabel ?birthYear
WHERE {
  ?person a dbo:Person ;
          dbo:birthDate ?birthDate ;
          dct:subject ?category .
  
  BIND(xsd:integer(SUBSTR(STR(?birthDate), 1, 4)) AS ?birthYear)
  FILTER(?birthYear > 1800)
  
  # Optionnel : récupérer le label en français
  ?person rdfs:label ?personLabel .
  FILTER(LANG(?personLabel) = "fr")
}
ORDER BY ?birthYear