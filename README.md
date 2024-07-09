# friends-spec

This repository contains the specification for the Friends serive of the FriendPost application.

## Tech Stack

The Friends service will be implemented using Java and Postgres

## C4 Container diagram

```mermaid
C4Container
title FriendPost Application Friends Service

Container_Boundary(friendsservice, "Friend Management") {
    Container(nodeapp, "Friends API Java App","Java")
    ContainerDb(usersdb, "Friends Service Database", "Postgres")
}

Container_Ext(webapp,"Web Application")
Container_Ext(usersservice,"Users Service")
Container_Ext(timelineservice,"Timeline Service")

Rel(webapp, nodeapp, "Manage Requests, Get Friends, Unfriend, Get Suggestions")
Rel(nodeapp, usersservice,"Gets profile data for suggestions")
Rel(timelineservice, nodeapp,"Gets Friend data as required")

UpdateRelStyle(webapp, nodeapp, $offsetX="-150",$offsetY="-40")
UpdateRelStyle(nodeapp, usersservice, $offsetY="-60")
UpdateRelStyle(timelineservice, nodeapp, $offsetY="-40")
```