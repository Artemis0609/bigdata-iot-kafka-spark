# Sistema de Procesamiento de Datos en Tiempo Real y Batch (Kafka + Spark)

## Descripción de la solución
Pipeline de Big Data implementado para la captura, procesamiento y análisis de datos. Contempla tanto el procesamiento en tiempo real de datos simulados de sensores IoT mediante **Apache Kafka** y **Apache Spark Streaming** (cálculo de agregaciones por ventanas de tiempo), como el procesamiento por lotes (Batch) analizando archivos estructurados desde HDFS con PySpark.

## Requisitos del entorno
- Ubuntu Linux (VM VirtualBox)
- Apache Kafka 3.9.2
- Apache Spark 3.5.3 con Python 3

---

## Instrucciones de ejecución

### 1. Iniciar ZooKeeper
Abre una terminal y ejecuta el servidor de ZooKeeper:
```bash
cd kafka_2.12-3.9.2
bin/zookeeper-server-start.sh config/zookeeper.properties

## 2. Iniciar el Servidor de Kafka
Abre una segunda terminal y arranca el broker de Kafka:

cd kafka_2.12-3.9.2
bin/kafka-server-start.sh config/server.properties

## 3. Crear el tópico de Kafka
Crea el tópico requerido para los datos de los sensores:

cd kafka_2.12-3.9.2
bin/kafka-topics.sh --create --topic sensor_data --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1

## 4. Ejecutar el Consumidor de Spark Streaming
Abre una tercera terminal y lanza el script consumidor:

spark-submit --packages org.apache.spark:spark-sql-kafka-0-10_2.12:3.5.3 spark_streaming_consumer.py

##5. Ejecutar el Productor de Datos IoT
Abre otra terminal y ejecuta el script productor:

python3 tarea3.py

---

<FollowUp>
¿Pudiste guardar los cambios del README y ver cómo quedó tu repositorio en GitHub?
</FollowUp>

<ElicitationsGroup>
</ElicitationsGroup>
