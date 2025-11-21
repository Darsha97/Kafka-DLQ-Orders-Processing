# Kafka Orders – Assignment

## Overview
This project simulates an order stream using Apache Kafka.  
A Python producer sends order messages in Avro format.  
A Python consumer reads the orders, maintains a running average of order prices,
and implements retry logic plus a Dead Letter Queue (DLQ) for failed messages.


## Architecture

- **Producer (`producer/producer.py`)**
  - Generates random order events.
  - Serializes each event to Avro using the shared schema.
  - Publishes messages to the Kafka topic **`orders`**.

- **Consumer (`consumer/consumer.py`)**
  - Subscribes to the **`orders`** topic.
  - Deserializes Avro messages.
  - Maintains a **running average** of order prices.
  - Implements **retry logic** for temporary errors.
  - Sends permanently failed messages to the **`orders-dlq`** topic.

- **DLQ Consumer (`consumer/dlq_consumer.py`)**
  - Subscribes to **`orders-dlq`**.
  - Prints failed records, error reasons, and timestamps for analysis.

## Topics
- `orders` – main order stream
- `orders-dlq` – dead letter queue for permanently failed messages

## How to run

1. Start Kafka and Zookeeper:
   ```bash
   docker compose up -d


2. Install Python dependencies
   ```bash
   pip install -r requirements.txt

3. Run the Producer
   ```bash
   cd producer
   
   python producer.py

4. Run the Consumer and DLQ Consumer
   ```bash
   cd consumer

   python consumer.py

   python dlq_consumer.py
