---
layout: post
title: Layered Architecture Notes
tags: Useful
category: Notes
---

#### General ####

Also called NTier Pattern

#### Layers are closed ####

When a request comes in to any give layer, that request must flow through each layer in order to get to the one below it.

#### Layers of isolation ####

If I make a change to one of the layers, I only have to update the contract with the layer below and no other layers. Components are bound to a specific layer
 
#### Examples of typical layers ####

- Presentation Layer  
- Business Layer  
- Services Layer  
- Persistence Layer  
- Database Layer  
