Elecciones Argentina 2017
==========================

Exportación de datos en formato CSV del aplicativo provisto por la DINE

http://www.resultados.gob.ar/inimesas.htm


¿Por qué?
---------

Los datos desagregado por mesa que proporciona la Justicia Electoral están empaquetados en una aplicación para Windows
utilizando una base de datos en formato Microsoft Access (.mdb) que es dificil de utilizar con herramientas de análisis estándar


Liberando los datos
---------------------

Los csv se extrajeron a través del software libre `mdbtools <http://mdbtools.sourceforge.net>`_ ::


    $ sudo apt-get install mdbtools



.. code:: python

    In [1]: !mv "App Consulta Mesas - Argentina/program files/Argentina 2017 (Primarias)/DATOS/PR_ARGENTINA2017.mdb" db.mdb


    In [2]: !!mdb-tables db.mdb
    Out[2]: ['IndEle MesasCandidaturaConcejales MesasCandidaturaDProvinciales MesasCandidaturaGobernador MesasCandidaturaPNacionales MesasCandidaturaPRegionales MesasCandidaturaPresidente MesasCandidaturaSNacionales MesasCandidaturaSProvinciales MesasConcejales MesasDProvinciales MesasGobernador MesasPNacionales MesasPRegionales MesasPresidente MesasSNacionales MesasSublemaConcejales MesasSublemaDNacionales MesasSublemaDProvinciales MesasSublemaGobernador MesasSublemaPNacionales MesasSublemaPRegionales MesasSublemaPresidente MesasSublemaSNacionales MesasSublemaSProvinciales NomAmbitos NomCandidatosGobernador NomCandidatosPresidente NomElecciones NomPartidos TotalCandidaturaConcejales TotalCandidaturaDNacionales TotalCandidaturaDProvinciales TotalCandidaturaGobernador TotalCandidaturaPNacionales TotalCandidaturaPresidente TotalCandidaturaSNacionales TotalCandidaturaSProvinciales TotalConcejales TotalDNacionales TotalDProvinciales TotalGobernador TotalPNacionales TotalPresidente TotalSNacionales TotalSProvinciales TotalSubLemaConcejales TotalSubLemaDNacionales TotalSubLemaDProvinciales TotalSubLemaGobernador TotalSubLemaPNacionales TotalSubLemaPRegionales TotalSubLemaPresidente TotalSubLemaSNacionales TotalSubLemaSProvinciales MesasCandidaturaDNacionales MesasDNacionales MesasSProvinciales TotalCandidaturaPRegionales TotalPRegionales ']

    In [3]: tables = _[0].split()

    In [4]: for table in tables:
       ...:     !mdb-export db.mdb {table} > {table}.csv
       ...:


Otras elecciones
----------------

- También están disponibles los datos de las `elecciones de 2013 <https://github.com/mgaitan/elecciones_argentina_2013>`_ y `2015 <https://github.com/mgaitan/elecciones_argentina_2015>`_
