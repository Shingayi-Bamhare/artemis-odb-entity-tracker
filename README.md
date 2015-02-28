# Entity Tracker

Server and Client that provides online artemis-odb World state.

![screenshot](/screenshot.png?raw=true)


# Simple Usage


```java
artemisWorld.setManager(new EntityTracker(new EntityTrackerMainWindow()));
```

# Network Connection

Host your Entity Tracker Server:
```java
EntityTrackerServer entityTrackerServer = new EntityTrackerServer();
entityTrackerServer.start();
artemisWorld.setManager(new EntityTracker(entityTrackerServer));
```

For GUI run [StandaloneMain.java](artemis-entity-tracker-gui/src/net/namekdev/entity_tracker/StandaloneMain.java) file or:
```java
final EntityTrackerMainWindow window = new EntityTrackerMainWindow();
final Client client = new Client(new ExternalInterfaceCommunicator(window));

client.connect(serverName, serverPort);
client.startThread();
```

# Custom Local/Networked Listener

Generally speaking, `EntityTracker` expects `WorldUpdateListener` interface implementation, e.g. it may be some window listener.

To achieve network version one can just mimic implementation of `ExternalInterfaceCommunicator` by implementing `Communicator` interface and passing it to `Client`.
