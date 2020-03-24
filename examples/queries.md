## Ejemplos de consultas sobre bicicleta pública

A continuación se presentan algunos ejemplos de consultas utilizando como referencia un extracto de los  conjuntos de datos de bicicleta pública publicados por el ayuntamiento de Madrid y el ayuntamiento de Zaragoza como datos abiertos. Además se han tomado algunos ejemplos  adicionales de los sitios Web de los ayuntamientos de A Coruña y Santiago de Compostela.

Por ejemplo, en esta [consulta](http://ciudadesabiertas.linkeddata.es/sparql?default-graph-uri=&query=PREFIX+esbici%3A+%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Fdef%2Ftransporte%2Fbicicleta-publica%23%3E%0D%0APREFIX+dct%3A+%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0APREFIX+esequip%3A+%3Chttp%3A%2F%2Fvocab.linkeddata.es%2Fdatosabiertos%2Fdef%2Furbanismo-infraestructuras%2Fequipamiento-municipal%23%3E%0D%0A%0D%0ASELECT+%28COUNT%28*%29+AS+%3Festaciones_operativas%29+%0D%0AWHERE+%7B%0D%0A++%3Fs+a+esbici%3AEstacionBicicleta+.%0D%0A++%3Fs+dct%3Aidentifier+%3Fidentificador+.%0D%0A++%3Fs+esequip%3Anombre+%3Fnombre_estacion+.%0D%0A++%3Fs+esbici%3AestadoEstacion+%3Chttp%3A%2F%2Fvocab.linkeddata.es%2Fdatosabiertos%2Fkos%2Ftransporte%2Fbicicleta-publica%2Ftipo-estado-estacion%2Foperativa%3E+.%0D%0A%7D%0D%0A%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) se pide es número de esatciones que están operativas.

```
PREFIX esbici: <http://vocab.ciudadesabiertas.es/def/transporte/bicicleta-publica#>
PREFIX dct: <http://purl.org/dc/terms/>
PREFIX esequip: <http://vocab.linkeddata.es/datosabiertos/def/urbanismo-infraestructuras/equipamiento-municipal#>

SELECT (COUNT(*) AS ?estaciones_operativas)
WHERE {
  ?s a esbici:EstacionBicicleta .
  ?s dct:identifier ?identificador .
  ?s esequip:nombre ?nombre_estacion .
  ?s esbici:estadoEstacion <http://vocab.linkeddata.es/datosabiertos/kos/transporte/bicicleta-publica/tipo-estado-estacion/operativa> .
}
```

En esta [consulta](http://ciudadesabiertas.linkeddata.es/sparql?default-graph-uri=&query=PREFIX+esbici%3A+%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Fdef%2Ftransporte%2Fbicicleta-publica%23%3E%0D%0APREFIX+dct%3A+%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0APREFIX+esequip%3A+%3Chttp%3A%2F%2Fvocab.linkeddata.es%2Fdatosabiertos%2Fdef%2Furbanismo-infraestructuras%2Fequipamiento-municipal%23%3E%0D%0A%0D%0ASELECT+DISTINCT+%3Fidentificador+%3Fnombre_estacion%0D%0AWHERE+%7B%0D%0A++%3Fs+a+esbici%3AEstacionBicicleta+.%0D%0A++%3Fs+dct%3Aidentifier+%3Fidentificador+.%0D%0A++%3Fs+esequip%3Anombre+%3Fnombre_estacion+.%0D%0A++%3Fs+esbici%3AestadoEstacion+%3Chttp%3A%2F%2Fvocab.linkeddata.es%2Fdatosabiertos%2Fkos%2Ftransporte%2Fbicicleta-publica%2Ftipo-estado-estacion%2Fno-operativa%3E+.%0D%0A%7D%0D%0A%0D%0A%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) se obtiene el listado de todas las estaciones que no están operativas, incluyendo el identificador y el nombre de la estación.

```
PREFIX esbici: <http://vocab.ciudadesabiertas.es/def/transporte/bicicleta-publica#>
PREFIX dct: <http://purl.org/dc/terms/>
PREFIX esequip: <http://vocab.linkeddata.es/datosabiertos/def/urbanismo-infraestructuras/equipamiento-municipal#>

SELECT DISTINCT ?identificador ?nombre_estacion
WHERE {
  ?s a esbici:EstacionBicicleta .
  ?s dct:identifier ?identificador .
  ?s esequip:nombre ?nombre_estacion .
  ?s esbici:estadoEstacion <http://vocab.linkeddata.es/datosabiertos/kos/transporte/bicicleta-publica/tipo-estado-estacion/no-operativa> .
}
```

En la siguiente [consulta](http://ciudadesabiertas.linkeddata.es/sparql?default-graph-uri=&query=PREFIX+esbici%3A+%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Fdef%2Ftransporte%2Fbicicleta-publica%23%3E%0D%0APREFIX+dct%3A+%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0A%0D%0ASELECT+%3Fidentificador+%3Festado%0D%0AWHERE+%7B%0D%0A++%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Frecurso%2Ftransporte%2Fbicicleta-publica%2FBicicleta%2FBIC00002%3E+dct%3Aidentifier+%3Fidentificador+.%0D%0A++%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Frecurso%2Ftransporte%2Fbicicleta-publica%2FBicicleta%2FBIC00002%3E+esbici%3AestadoBicicleta+%3Festado+%0D%0A%7D%0D%0A%0D%0A%0D%0A%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) se obtiene el estado de la bicicleta con identificador "BIC00002".

```
PREFIX esbici: <http://vocab.ciudadesabiertas.es/def/transporte/bicicleta-publica#>
PREFIX dct: <http://purl.org/dc/terms/>

SELECT ?identificador ?estado
WHERE {
  <http://vocab.ciudadesabiertas.es/recurso/transporte/bicicleta-publica/Bicicleta/BIC00002> dct:identifier ?identificador .
  <http://vocab.ciudadesabiertas.es/recurso/transporte/bicicleta-publica/Bicicleta/BIC00002> esbici:estadoBicicleta ?estado
}
```

En la siguiente [consulta](http://ciudadesabiertas.linkeddata.es/sparql?default-graph-uri=&query=PREFIX+esbici%3A+%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Fdef%2Ftransporte%2Fbicicleta-publica%23%3E%0D%0APREFIX+dct%3A+%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0A%0D%0ASELECT+%3Fidentificador%0D%0AWHERE+%7B%0D%0A++%3Fs+a+esbici%3ABicicleta+.%0D%0A++%3Fs+dct%3Aidentifier+%3Fidentificador+.%0D%0A++%3Fs+esbici%3AestadoBicicleta+%3Chttp%3A%2F%2Fvocab.linkeddata.es%2Fdatosabiertos%2Fkos%2Ftransporte%2Fbicicleta-publica%2Ftipo-estado-bicicleta%2Fdisponible%3E%0D%0A%7D%0D%0A%0D%0A%0D%0A%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) se obtiene el listado de todas las bicicletas disponibles.

```
PREFIX esbici: <http://vocab.ciudadesabiertas.es/def/transporte/bicicleta-publica#>
PREFIX dct: <http://purl.org/dc/terms/>

SELECT ?identificador
WHERE {
  ?s a esbici:Bicicleta .
  ?s dct:identifier ?identificador .
  ?s esbici:estadoBicicleta <http://vocab.linkeddata.es/datosabiertos/kos/transporte/bicicleta-publica/tipo-estado-bicicleta/disponible>
}
```

En la siguiente [consulta](http://ciudadesabiertas.linkeddata.es/sparql?default-graph-uri=&query=PREFIX+esbici%3A+%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Fdef%2Ftransporte%2Fbicicleta-publica%23%3E%0D%0APREFIX+schema%3A+%3Chttp%3A%2F%2Fschema.org%2F%3E%0D%0APREFIX+dcterms%3A+%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0APREFIX+smdx%3A+%3Chttp%3A%2F%2Fpurl.org%2Flinked-data%2Fsdmx%2F2009%2Fdimension%23%3E%0D%0ASELECT+%28count%28%3Fusuario%29+as+%3FtotalUsuarios%29%2C+%3FTotalMujeres%2C++%28%28%3FTotalMujeres*100%29%2F%28count%28%3Fusuario%29%29+as+%3FporcentajeMujeres%29%0D%0AWHERE+%7B%0D%0A++++%3Fusuario+a+esbici%3AUsuario+.%0D%0A++++%7B%0D%0A++++SELECT+%28count%28%3Fusuario%29+as+%3FTotalMujeres%29%0D%0A++++WHERE+%7B%0D%0A+++++++++++%3Fusuario+smdx%3Asex+%3Chttp%3A%2F%2Fpurl.org%2Flinked-data%2Fsdmx%2F2009%2Fcode%23sex-F%3E+.%0D%0A++++%7D%0D%0A%7D%0D%0A%7D%0D%0A%0D%0A%0D%0A%0D%0A%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) se obtiene información de la utilización del servicio por parte de las mujeres.

```
PREFIX esbici: <http://vocab.ciudadesabiertas.es/def/transporte/bicicleta-publica#>
PREFIX schema: <http://schema.org/>
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX smdx: <http://purl.org/linked-data/sdmx/2009/dimension#>
SELECT (count(?usuario) as ?totalUsuarios), ?TotalMujeres,  ((?TotalMujeres*100)/(count(?usuario)) as ?porcentajeMujeres)
WHERE {
    ?usuario a esbici:Usuario .
     {
      SELECT (count(?usuario) as ?TotalMujeres)
      WHERE {
           ?usuario smdx:sex <http://purl.org/linked-data/sdmx/2009/code#sex-F> .
     }
   }
}
```

En esta [consulta](http://ciudadesabiertas.linkeddata.es/sparql?default-graph-uri=&query=PREFIX+esbici%3A+%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Fdef%2Ftransporte%2Fbicicleta-publica%23%3E%0D%0APREFIX+schema%3A+%3Chttp%3A%2F%2Fschema.org%2F%3E%0D%0APREFIX+dcterms%3A+%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0APREFIX+smdx%3A+%3Chttp%3A%2F%2Fpurl.org%2Flinked-data%2Fsdmx%2F2009%2Fdimension%23%3E%0D%0ASELECT+%28count%28%3Fusuario%29+as+%3FtotalUsuarios%29%2C+%3FTotalHombres%2C++%28%28%3FTotalHombres*100%29%2F%28count%28%3Fusuario%29%29+as+%3FporcentajeHombres%29%0D%0AWHERE+%7B%0D%0A++++%3Fusuario+a+esbici%3AUsuario+.%0D%0A++++%7B%0D%0A++++SELECT+%28count%28%3Fusuario%29+as+%3FTotalHombres%29%0D%0A++++WHERE+%7B%0D%0A+++++++++++%3Fusuario+smdx%3Asex+%3Chttp%3A%2F%2Fpurl.org%2Flinked-data%2Fsdmx%2F2009%2Fcode%23sex-M%3E+.%0D%0A++++%7D%0D%0A%7D%0D%0A%7D%0D%0A%0D%0A%0D%0A%0D%0A%0D%0A%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) se obtiene información de la utilización del servicio por parte de las mujeres.

```
PREFIX esbici: <http://vocab.ciudadesabiertas.es/def/transporte/bicicleta-publica#>
PREFIX schema: <http://schema.org/>
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX smdx: <http://purl.org/linked-data/sdmx/2009/dimension#>
SELECT (count(?usuario) as ?totalUsuarios), ?TotalHombres,  ((?TotalHombres*100)/(count(?usuario)) as ?porcentajeHombres)
WHERE {
    ?usuario a esbici:Usuario .
      {
        SELECT (count(?usuario) as ?TotalHombres)
        WHERE {
           ?usuario smdx:sex <http://purl.org/linked-data/sdmx/2009/code#sex-M> .
      }
  }
}
```

En esta [consulta](http://ciudadesabiertas.linkeddata.es/sparql?default-graph-uri=&query=PREFIX+esbici%3A+%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Fdef%2Ftransporte%2Fbicicleta-publica%23%3E%0D%0APREFIX+sosa%3A+%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Fsosa%2F%3E%0D%0APREFIX+schema%3A+%3Chttp%3A%2F%2Fschema.org%2F%3E%0D%0APREFIX+dct%3A+%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0APREFIX+smdx%3A+%3Chttp%3A%2F%2Fpurl.org%2Flinked-data%2Fsdmx%2F2009%2Fdimension%23%3E%0D%0A%0D%0ASELECT+%3FanclajesLibres+%3Fidentificador+%3Fdireccion%0D%0AWHERE+%7B%0D%0A++++%3Fobservacion+a+esbici%3AObservacionEstacion+.%0D%0A++++%3Fobservacion+sosa%3AmadeBySensor+%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Frecurso%2Ftransporte%2Fbicicleta-publica%2FEstacionBicicleta%2F1%3E+.%0D%0A++++%3Fobservacion+sosa%3AobservedProperty+%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Fdef%2Ftransporte%2Fbicicleta-publica%23anclajesLibres%3E+.%0D%0A++++%3Fobservacion+sosa%3AresultTime+%222019-06-01T02%3A27%3A16.592588%22%5E%5Exsd%3AdateTime+.%0D%0A++++%3Fobservacion+sosa%3AhasSimpleResult+%3FanclajesLibres+.%0D%0A++++%3Fobservacion+sosa%3AmadeBySensor+%3Fsensor+.%0D%0A++++%3Fsensor+a+esbici%3AEstacionBicicleta+.%0D%0A++++%3Fsensor+dct%3Aidentifier+%3Fidentificador+.%0D%0A++++%3Fsensor+schema%3Aaddress+%3Fdireccion+.%0D%0A%7D%0D%0A%0D%0A%0D%0A%0D%0A%0D%0A%0D%0A%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) se obtiene una observación del número de anclajes libres de la estación número 1 para la fecha "2019-06-01T02:27:16.592588"^^xsd:dateTime.

```
PREFIX esbici: <http://vocab.ciudadesabiertas.es/def/transporte/bicicleta-publica#>
PREFIX sosa: <http://www.w3.org/ns/sosa/>
PREFIX schema: <http://schema.org/>
PREFIX dct: <http://purl.org/dc/terms/>
PREFIX smdx: <http://purl.org/linked-data/sdmx/2009/dimension#>

SELECT ?anclajesLibres ?identificador ?direccion
WHERE {
    ?observacion a esbici:ObservacionEstacion .
    ?observacion sosa:madeBySensor <http://vocab.ciudadesabiertas.es/recurso/transporte/bicicleta-publica/EstacionBicicleta/1> .
    ?observacion sosa:observedProperty <http://vocab.ciudadesabiertas.es/def/transporte/bicicleta-publica#anclajesLibres> .
    ?observacion sosa:resultTime "2019-06-01T02:27:16.592588"^^xsd:dateTime .
    ?observacion sosa:hasSimpleResult ?anclajesLibres .
    ?observacion sosa:madeBySensor ?sensor .
    ?sensor a esbici:EstacionBicicleta .
    ?sensor dct:identifier ?identificador .
    ?sensor schema:address ?direccion .
}
```

En esta [consulta](http://ciudadesabiertas.linkeddata.es/sparql?default-graph-uri=&query=PREFIX+esbici%3A+%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Fdef%2Ftransporte%2Fbicicleta-publica%23%3E%0D%0APREFIX+sosa%3A+%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Fsosa%2F%3E%0D%0APREFIX+schema%3A+%3Chttp%3A%2F%2Fschema.org%2F%3E%0D%0APREFIX+dct%3A+%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0APREFIX+smdx%3A+%3Chttp%3A%2F%2Fpurl.org%2Flinked-data%2Fsdmx%2F2009%2Fdimension%23%3E%0D%0A%0D%0ASELECT+%3FanclajesOcupados+%3Fidentificador+%3Fdireccion%0D%0AWHERE+%7B%0D%0A++++%3Fobservacion+a+esbici%3AObservacionEstacion+.%0D%0A++++%3Fobservacion+sosa%3AmadeBySensor+%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Frecurso%2Ftransporte%2Fbicicleta-publica%2FEstacionBicicleta%2F18%3E+.%0D%0A++++%3Fobservacion+sosa%3AobservedProperty+%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Fdef%2Ftransporte%2Fbicicleta-publica%23anclajesOcupados%3E+.%0D%0A++++%3Fobservacion+sosa%3AresultTime+%222019-06-01T00%3A27%3A15.455361%22%5E%5Exsd%3AdateTime+.%0D%0A++++%3Fobservacion+sosa%3AhasSimpleResult+%3FanclajesOcupados+.%0D%0A++++%3Fobservacion+sosa%3AmadeBySensor+%3Fsensor+.%0D%0A++++%3Fsensor+a+esbici%3AEstacionBicicleta+.%0D%0A++++%3Fsensor+dct%3Aidentifier+%3Fidentificador+.%0D%0A++++%3Fsensor+schema%3Aaddress+%3Fdireccion+.%0D%0A%7D%0D%0A%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) se muestra el número de anclajes ocupados por la estación número 18 en la fecha "2019-06-01T00:27:15.455361"^^xsd:dateTime.

```
PREFIX esbici: <http://vocab.ciudadesabiertas.es/def/transporte/bicicleta-publica#>
PREFIX sosa: <http://www.w3.org/ns/sosa/>
PREFIX schema: <http://schema.org/>
PREFIX dct: <http://purl.org/dc/terms/>
PREFIX smdx: <http://purl.org/linked-data/sdmx/2009/dimension#>

SELECT ?anclajesOcupados ?identificador ?direccion
WHERE {
    ?observacion a esbici:ObservacionEstacion .
    ?observacion sosa:madeBySensor <http://vocab.ciudadesabiertas.es/recurso/transporte/bicicleta-publica/EstacionBicicleta/18> .
    ?observacion sosa:observedProperty <http://vocab.ciudadesabiertas.es/def/transporte/bicicleta-publica#anclajesOcupados> .
    ?observacion sosa:resultTime "2019-06-01T00:27:15.455361"^^xsd:dateTime .
    ?observacion sosa:hasSimpleResult ?anclajesOcupados .
    ?observacion sosa:madeBySensor ?sensor .
    ?sensor a esbici:EstacionBicicleta .
    ?sensor dct:identifier ?identificador .
    ?sensor schema:address ?direccion .
}
```
