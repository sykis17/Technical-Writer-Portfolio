# Mermaid System Test

```mermaid
graph LR
    A[Engine Start] --> B{Oil Pressure?}
    B -- Low --> C[Shut Down]
    B -- Normal --> D[Taxi]