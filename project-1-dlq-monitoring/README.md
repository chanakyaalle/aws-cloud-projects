# Project 1 — CloudWatch DLQ Alert Monitoring System

## What This Does
Monitors an SQS Dead Letter Queue and automatically sends an 
email alert via CloudWatch when failed messages appear.
Built to replicate the production monitoring system I managed 
at TCS for Johnson & Johnson hospital infrastructure.

## Architecture
Message → SQS Main Queue → Fails 3 times → Dead Letter Queue
→ CloudWatch Alarm (fires when DLQ > 0) → SNS Topic → Email Alert

## AWS Services Used
- Amazon SQS — Main queue and Dead Letter Queue
- Amazon CloudWatch — Metric alarm on DLQ message count
- Amazon SNS — Email notification on alarm trigger

## Status
In Progress — Setting up notification pipeline (SNS confirmed),
SQS queues and CloudWatch alarm coming next.

## What I Learned So Far
- How SNS topics and email subscriptions work end to end
- Difference between Standard and FIFO SNS topics
- How to troubleshoot email delivery issues with SNS

## Real World Connection
At TCS I monitored DLQ alerts daily for J&J hospital systems.
This project shows I understand not just how to watch alerts
but how to BUILD the entire alerting pipeline from scratch.
