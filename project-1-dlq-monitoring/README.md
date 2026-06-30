# Project 1 — CloudWatch DLQ Alert Monitoring System

## What This Does
Monitors an SQS Dead Letter Queue and automatically sends an 
email alert via CloudWatch when failed messages appear.
Built to replicate the production monitoring system I managed 
at TCS for Johnson & Johnson hospital infrastructure.

## Architecture
Message → SQS Main Queue → Fails 3 times → Dead Letter Queue
→ CloudWatch Alarm (fires when DLQ ≥ 1) → SNS Topic → Email Alert

## AWS Services Used
- Amazon SQS — Main queue (tcs-demo-main-queue) and Dead Letter Queue (tcs-demo-dlq)
- Amazon CloudWatch — Metric alarm on ApproximateNumberOfMessagesVisible
- Amazon SNS — Email notification (dlq-alert-topic)

## How It Works
1. A message is sent to the main queue
2. If a consumer fails to process it 3 times (maxReceiveCount = 3), 
   SQS automatically moves it to the Dead Letter Queue
3. A CloudWatch alarm monitors the DLQ message count
4. The moment 1 or more messages appear in the DLQ, the alarm 
   triggers an SNS notification
5. SNS sends an email alert immediately

## Status
✅ Complete — Fully tested end to end. Alarm fires correctly 
and email alert is received within minutes of message failure.

## What I Learned
- How to configure SQS redrive policy linking a main queue to a DLQ
- How to create CloudWatch metric alarms on SQS metrics
- How SNS topics, subscriptions, and email confirmations work
- Difference between SNS Standard and FIFO topics
- The complete operational flow from message failure to alert — 
  the exact pipeline I monitored daily in production at TCS

## Real World Connection
At TCS I monitored DLQ alerts daily for J&J hospital systems,
manually checking CloudWatch and escalating issues. This project 
shows I understand not just how to watch alerts but how to BUILD 
the entire alerting pipeline from scratch — the queues, the alarm 
thresholds, and the notification system.

## Screenshots
See the screenshots in this folder showing:
- SQS queue configuration with DLQ redrive policy
- CloudWatch alarm setup and "In alarm" state
- Email alert received in Gmail

## Cost
This project runs entirely within AWS Free Tier — $0 cost.
