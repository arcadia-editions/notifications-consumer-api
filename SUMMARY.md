# Notifications Consumer

## Description

Notifications Consumer is the bounded context that turns domain events into
customer communications. It reacts to outcomes produced by the core services and
decides what message should be sent, through which channel, and to whom.

It is a supporting service focused on communication rather than ownership of the
core commerce process itself.

## Scope

- Send order confirmation messages after successful payment capture
- Notify customers when scarce stock is unavailable
- Notify customers when orders are cancelled
- Track delivery success or failure for outbound communications

## Main domain elements

- `Notification`: aggregate for outbound communication attempts
- `NotificationsConsumerService`: event-driven commands for customer messaging
- `OrderConfirmationSent`: event announcing a successful order confirmation message
- `StockUnavailableNotificationSent`: event announcing a successful stock-unavailable message
- `OrderCancelledNotificationSent`: event announcing a successful order-cancelled message
- `NotificationDeliveryFailed`: failure outcome for downstream monitoring or recovery
