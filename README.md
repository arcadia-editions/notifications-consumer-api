# notifications-consumer-api

Notifications Consumer is the bounded context that turns domain events into
customer communications. It reacts to outcomes produced by the core services and
decides what message should be sent, through which channel, and to whom.

Unlike the other contexts in the Place Order flow, this service does not own a
core commercial or operational process. Its center of gravity is communication:
interpreting business events and producing the right notification outcome.

## Bounded context scope

- Send order confirmation messages after successful payment capture
- Notify customers when scarce stock is unavailable
- Notify customers when orders are cancelled
- Track delivery success or failure for outbound communications

This service does not own orders, payments, inventory, or shipping rules. It
consumes those facts and translates them into customer-facing communication.

## Contents

- `domain-model.zdl`: source of truth for the notification aggregate, lifecycle, commands, and events
- `README.md`: repository overview and bounded-context explanation

## Main domain elements

- `Notification`: aggregate for outbound communication attempts
- `NotificationsConsumerService`: event-driven commands for customer messaging
- `OrderConfirmationSent`, `StockUnavailableNotificationSent`, `OrderCancelledNotificationSent`: successful communication outcomes
- `NotificationDeliveryFailed`: failure outcome for downstream monitoring or recovery
