# AIRFLOW TUTORIAL 

## Introducción

Diseñado como un Gráfico Acíclico Dirigido (DAG, por sus siglas en inglés), Apache Airflow es una herramienta de código abierto para orquestar complejos flujos de trabajo computacionales y procesamiento de datos. 

Al crearse un flujo de trabajo, se debe pensar cómo podría dividirse en tareas que se pueden ejecutar de forma independiente. Luego estas tareas se fusionan en un todo lógico representado en un gráfico.

*Imagen*

La forma del gráfico decide la lógica general del flujo. Un DAG puede incluir varias ramas y se puede decidir cuáles seguir o cuáles omitir en el momento de la ejecución.

### Observaciones

* El flujo puede detenerse por completo y los flujos en ejecución se reanudarán reiniciando la última tarea inacabada.

* Al diseñar operadores es importante tener en cuenta que pueden ejecutarse más de una vez. Cada tarea debe ser idempotente, es decir, tener la capacidad de aplicarse varias veces sin producir consecuencias no deseadas.

## Nomenclatura

Breve descripción de algunos términos utilizados al diseñar flujos Airflow

* Los DAG se componen de tareas.
* Cada tarea se crea con instancias de una clase **Operador**.
* Una instancia configurada de un operador se convierte en una tarea.
* Cuando se inicia un DAG, Airflow crea una entrada **DAG Run** en su base de datos.
* Cuando 

## Configuracion e Instalación

### Prerrequisitos

Airflow está escrito en Python, por lo cual será necesario Python 3. Así mismo por buenas prácticas, instalar Virtualbox.

### Instalación Airflow

Dentro de la carpeta donde se almacenará el proyecto.

    $ virtualenv -p /usr/bin/python3 entorno-virtual
    $ source entorno-virtual/bin/activate

Para este caso se trabaja con Airflow 1.10.9

    $ pip install apache-airflow==1.10.9

Se establece la carpeta del proyecto como variable de entorno.

    $ export AIRFLOW_HOME=`pwd`/airflow-tutorial

Ahora se ejecuta el siguiente comando:

    $ airflow version

El cual creará su archivo de configuración predeterminado **airflow.cfg** y el archivo **unittests.cfg**.

Inicializar la base de datos

    $ airflow initdb 

Iniciar el servicio web, el puerto por defecto es el 8080

    $ airflow webserver 

Iniciar el scheduler

    $ airflow scheduler

Ingresar en el navegador a la URL localhost:8080

**Observación**

Airflow viene con una serie de ejemplos de DAGs, estos ejemplos pueden no funcionar hasta que se tenga al menos un archivo de definición de DAG propio **dags_folder**.

# Primer DAG

Crear el **dags_folder**, este es el directorio donde se almacenarán los archivos de definición.

airflow-tutorial/dags


