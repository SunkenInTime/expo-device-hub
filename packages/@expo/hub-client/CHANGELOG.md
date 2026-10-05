# @expo/hub-client

## 1.3.1

### Patch Changes

- a512bfe: Read the iOS foreground app icon from serve-sim's `/api/apps/icon` route when `/api` advertises `appIconEndpoint`, so a tunneled server shows the icon without the exec-ws socket. Older servers still get the icon over exec-ws.

## 1.3.0

### Minor Changes

- 39a07da: Add a `token` option to `useIosDeviceClient` for a serve-sim started with `--require-token`, such as an EAS Simulator Preview session.
- 04a0640: Send the `token` option from `useAndroidDeviceClient` too, and add it to `useActiveDeviceClient`, for a page that connects to a Hub started with `--require-token` from another origin. The Android client sends the token as a bearer header, as a `serve-emu.token.` WebSocket subprotocol, and as `?token=` only where a browser cannot set a header: the logcat and metrics `EventSource` streams, the camera image URLs, and the WebRTC close beacon. The WebRTC close POST sends the bearer header alone. The Hub does not allow other origins through CORS yet. So from another origin, this covers the Android H.264 stream and input socket, and the iOS client only from a loopback origin, without the features that use serve-sim's control socket.
- 91ecacb: Add DeviceClientProvider, useDeviceClient, useDeviceClientSelector, and useDeviceScreenClient so UI components can share one connection.

## 1.2.0

### Minor Changes

- 4e80b34: `DeviceClient.screenshot()` now resolves to a `ScreenshotCapture` with the PNG
  `blob` and its session `artifact` outcome, read from the backend's
  `X-Expo-Screenshot-Artifact` headers, instead of a bare `Blob`.

### Patch Changes

- fec1fc2: Request Android screenshots with POST.
- cb367df: Resolve proxied iOS stream, input, and middleware URLs against the configured public serve-sim mount.
- f68dd10: A failed iOS screenshot event in `events` now has the failure reason in its
  `message`, for example `Screenshot failed: simctl screenshot failed`.

## 1.1.0

### Minor Changes

- 255b36c: Initial release.

## 1.0.0

Placeholder release. It contains no code.
