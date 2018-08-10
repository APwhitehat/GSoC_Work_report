My work focused mainly on [Dendrite](https://github.com/matrix-org/dendrite), Matrix server
written in Go.

### Federation

Large chunk of the work involved implementing left-over [Federation APIs](https://matrix.org/docs/spec/server_server/unstable.html).
These form the core of Matrix's decentralized approach to communication. Federation is
basically a fancy term for server-server communication, using which two Matrix servers stay in sync.

##### Things worked on:
- State APIs: This is used by Matrix servers to query each other for determining
the state of a room at some point of history. [#486](https://github.com/matrix-org/dendrite/pull/486)
- GetMissingEvents API: Sometimes two federating servers get gaps in their event graph,\
  this is used to fill in the gaps.[#516](https://github.com/matrix-org/dendrite/pull/516)
- User Query API: This is used to query the devices for an user. [#498](https://github.com/matrix-org/dendrite/pull/498)
- Leave API: This is used when an remote user leaves a local room. [#535](https://github.com/matrix-org/dendrite/pull/535)

This was accompanied by small fixes to improve code consistency & error responses.

### Typing Notifications

Typing notifications are ephemeral events which are generated when user types in a room.
These are sent of to all members of the room.

##### Things worked on:
- Authenticate typing requests from client and send it off to Typing Server. [#550](https://github.com/matrix-org/dendrite/pull/550)
- Build the Typing Server, maintain current list of typing users in all (local) rooms. [#559](https://github.com/matrix-org/dendrite/pull/559) & [#567](https://github.com/matrix-org/dendrite/pull/567)
- Send Typing events to other federating servers. [#572](https://github.com/matrix-org/dendrite/pull/572)

##### Things left to do:
- Accept typing events via federation API. [issue #573](https://github.com/matrix-org/dendrite/issues/573)
- Send Typing events to clients via syncapi. [issue #574](https://github.com/matrix-org/dendrite/issues/574)
- Forwarding typing events to AS. [issue #578](https://github.com/matrix-org/dendrite/issues/578)

### Miscellaneous Work
- Build a transactions cache, to make clientapi idempotent.
	[#440](https://github.com/matrix-org/dendrite/pull/440) & [#444](https://github.com/matrix-org/dendrite/pull/444)
- Store transaction IDs in roomserver to prevent reprocessing of events. [#446](https://github.com/matrix-org/dendrite/pull/446)
- [[gomatrixserverlib](https://github.com/matrix-org/gomatrixserverlib)] Add token library based on macaroons.
	[#89](https://github.com/matrix-org/gomatrixserverlib/pull/89)
- Username auto generation. [#470](https://github.com/matrix-org/dendrite/pull/470)
- Handle application services in clientapi authentication.
	[#433](https://github.com/matrix-org/dendrite/pull/433) & [#427](https://github.com/matrix-org/dendrite/pull/427)
- Add internal API to query membership for an user in roomserver. [#544](https://github.com/matrix-org/dendrite/pull/544)

Also varoius other fixes and code quality improvements.

#### [See commits in Dendrite](https://github.com/matrix-org/dendrite/commits?author=APwhitehat)
#### [See commits in gomatrixserverlib](https://github.com/matrix-org/gomatrixserverlib/commits?author=APwhitehat)