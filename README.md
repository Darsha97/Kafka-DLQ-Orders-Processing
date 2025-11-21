# Kafka Orders – Assignment

## Overview
This project simulates an order stream using Apache Kafka.  
A Python producer sends order messages in Avro format.  
A Python consumer reads the orders, maintains a running average of order prices,
and implements retry logic plus a Dead Letter Queue (DLQ) for failed messages.

## Topics
- `orders` – main order stream
- `orders-dlq` – dead letter queue for permanently failed messages

## How to run

1. Start Kafka and Zookeeper:
   ```bash
   docker compose up -d
