<p align="center">
  <img src="banner.svg" alt="AxonKit" width="480">
</p>

**AxonKit** is a distributed real-time communication stack — a multi-node WebRTC
SFU with intelligent cross-node routing, plus a LiveKit-compatible client SDK.
Built for video conferencing, live streaming, and multi-modal AI applications.

## Repositories

| Repository | Description |
| --- | --- |
| [axonkit](https://github.com/axonkit/axonkit) | Go server — mediasoup SFU, RIB/FIB cross-node stream routing, WHIP/RTMP ingest, NATS-based discovery |
| [client-sdk-js](https://github.com/axonkit/client-sdk-js) | JS/TS client SDK — LiveKit-style API on mediasoup-client, RPC, data streams, groups |
| [libsamplerate-js](https://github.com/axonkit/libsamplerate-js) | Audio sample-rate conversion for the browser via WebAssembly libsamplerate |

<!-- Add more repositories here (e.g. the AAC codec library). -->

## Quick start

```bash
pnpm add @axonkit/client-sdk-js
```

```typescript
import { Room, RoomEvent } from '@axonkit/client-sdk-js';

const room = new Room({ dynacast: true, adaptiveStream: true });
room.on(RoomEvent.TrackSubscribed, (track) => {
  document.body.appendChild(track.attach());
});
await room.connect('https://your-server.com', 'your-jwt-token');
await room.localParticipant.setCameraEnabled(true);
```

## Highlights

- **SFU + distributed routing** — RIB/FIB based cross-cluster stream forwarding with self-healing failover
- **LiveKit-compatible client API** — `Room` / `Participant` / `Track` model, easy migration
- **HTTP join + DataChannel signaling** — low-latency Axon Protocol after the initial join
- **Simulcast / SVC / Dynacast / AdaptiveStream** — bandwidth-efficient delivery out of the box
