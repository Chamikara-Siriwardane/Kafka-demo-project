# Kafka Demo Project

A simple demonstration of Apache Kafka with Python, showcasing basic producer and consumer functionality using Docker.

## Overview

This project demonstrates how to:
- Run Kafka locally using Docker Compose (KRaft mode)
- Produce messages to a Kafka topic
- Consume messages from a Kafka topic
- Handle order processing as a practical example

## Prerequisites

- Docker and Docker Compose
- Python 3.x
- `confluent-kafka` Python library

## Installation

1. Clone the repository:
```bash
git clone https://github.com/Chamikara-Siriwardane/Kafka-demo-project.git
cd Kafka-demo-project
```

2. Install Python dependencies:
```bash
pip install confluent-kafka
```

## Usage

### 1. Start Kafka

Start the Kafka broker using Docker Compose:

```bash
docker-compose up -d
```

This will start a single Kafka broker in KRaft mode on `localhost:9092`.

### 2. Run the Consumer

In one terminal, start the order tracker (consumer):

```bash
python tracker.py
```

The consumer will subscribe to the `orders` topic and wait for incoming messages.

### 3. Run the Producer

In another terminal, send an order (producer):

```bash
python producer.py
```

This will send a sample order to the `orders` topic, which will be consumed by the tracker.

## Project Structure

```
.
├── docker-compose.yaml   # Kafka setup with Docker Compose
├── producer.py           # Kafka producer that sends orders
├── tracker.py            # Kafka consumer that receives orders
└── README.md            # This file
```

## How It Works

- **Producer** (`producer.py`): Creates an order with a unique ID, user, item, and quantity, then sends it to the `orders` topic
- **Consumer** (`tracker.py`): Subscribes to the `orders` topic and processes incoming orders in real-time

## Stopping Kafka

To stop the Kafka broker:

```bash
docker-compose down
```

To stop and remove volumes:

```bash
docker-compose down -v
```
