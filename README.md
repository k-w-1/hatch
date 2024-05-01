# hatch
Documentation of our family's adventures hatching eggs!

> This is a work in progress, documenting as we go!

Rough streaming architecture:

```mermaid
flowchart TD
    A[Wyze Cam v3] -->|video stream| B[Docker Wyze Bridge]
    B <-.->|"for auth (using API key)"| W[Wyze cloud]
    B --> C[OBS on WS2016]
    C --> D[Youtube live stream]
```
