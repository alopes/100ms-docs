## Architecture

100ms is a cloud platform that allows developers to add video and audio conferencing to Web, Android and iOS applications.

The platform provides REST APIs, SDKs, and a dashboard that make it simple to capture, distribute, record, and render live interactive audio, video.

Any application built using 100ms' SDK has 2 components.

-   **Client:** Use 100ms android, iOS, Web SDKs to manage connections, room states, render audio/video. This is where most of the heavy lifting happens.

-   **Server:** Use 100ms' APIs or dashboard to generate tokens, create rooms, setup room templates, trigger recording RTMP out, access events. This is usually a quick, short setup.

![Architecture](/docs/v2/arch.png)

## Basic Concepts

-   `Room` A room is the basic object that 100ms SDKs return on successful connection. This contains reference to peers, tracks and everything you need to render a live a/v app.
-   `Peer` A peer is the object returned by 100ms SDKs that contains all information about a user - name, role, video track etc.
-   `Track` A track represents either the audio or video that a peer is publishing.
-   `Role` A role defines who can a peer see/hear, the quality at which they publish their video, whether they have permissions to publish video/screenshare, mute someone, change someone's role.
    eg. b-owner in the following screenshot can publish video at 720p, screenshare at 1080p and subscribes to b-guest and b-owner.

![Roles](/docs/v2/roles.png)

-   `Template` A template is a collection of roles, room settings, recording and RTMP settings (if used), that is used by the SDK to decide which geography to connect to, which tracks to return to the client, whether to turn on recording when a room is created etc. Each room is associated with a template. eg. small_classroom_template.

![Templates](/docs/v2/templates.png)

## What are the steps to build a live app with 100ms?

1. **Create a template:** Create a template and define roles, room settings - You can do this using the dashboard or by using our APIs.
2. **Create a room using the above template:** You can do this using the dashboard or our API.
3. **Integrate client SDK and join the above room:** You'll need to generate a token for each peer that connects to a room. You can generate it using the endpoint we make for you or you can deploy your own server.
4. **[Optional] Receive events:** Create a webhook endpoint to receive server-side notifications about room usage (peer joining/leaving) or recording, RTMP out starting/ending.

## Where should I start?

### Quickstart

If you just want to see 100ms' SDKs in action in under 5 minutes, run one of our quickstart [apps](./guides/quickstart).