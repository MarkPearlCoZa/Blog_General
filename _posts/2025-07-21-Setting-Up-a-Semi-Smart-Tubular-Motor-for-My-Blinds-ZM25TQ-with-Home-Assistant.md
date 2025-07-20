---
layout: post
title: Setting Up a Semi-Smart Tubular Motor for My Blinds ZM25TQ with Home Assistant
tags: 
category: General
---
Setting Up a Semi-Smart Tubular Motor for My Blinds ZM25TQ-0.8/25 with Home Assistant

I recently installed a Zemismart Smart Roller Shade Motor (model ZM25TQ-0.8/25) which I bought from AliExpress and integrated it with Home Assistant. While it worked in the end, I encountered a few hurdles—especially with Zigbee connectivity and configuration in Home Assistant.

## Zigbee Integration Challenges

Initially, I used the default Zigbee Home Automation (ZHA) integration in Home Assistant, but it didn’t provide the configuration options I needed
* Up/down controls were reversed (clicking “up” lowered the blinds and vice versa).

Following community recommendations, I switched to Zigbee2MQTT, which required:
1.	Installing the Mosquitto MQTT broker.
2.	Re-pairing all my Zigbee devices, which was a fair amount of work

## Configuring the Blind Motor

Zigbee2MQTT allowed more granular controls, but figuring out how to configure the bling motor was tricky. Online advice (from ChatGPT) was too generic.

Eventually, I found the printed instruction manual that came with the bling motor, which helped me:
*	Reverse the motor direction by publishing a message via Home Assistant’s Developer Tools.
*	Note: The menu option once called “Services” is now labeled “Actions.” You’ll need to use mqtt.publish and include a correctly formatted JSON payload (ChatGPT helped me format this).

~~~
service: mqtt.publish
data:
  topic: zigbee2mqtt/Office Blind/set
  payload: '{"options":{"reverse_direction":true}}'
  qos: 0
  retain: false
~~~

Once that was done, the controls worked correctly—open closed the blinds, and close opened them, as expected.

## Setting Limit Positions

Home Assistant doesn’t support setting the upper, lower, or middle limits directly. For that, I had to use the included rf remote control that came with the blind:
1.	Pair the remote with the motor:
*	Press the motor’s “Set” button once.
*	Then press the “Up” button on the remote.

2.	Unpairing the remote:
*	Press the remote’s setting button five times, then press the “Up” button once.

3.	Set upper/lower limits:
*	Move the blind to the desired position.
*	Press the remote’s setting button once, then the direction button (up or down) to save the limit.

Once configured, Home Assistant respected the limits when issuing open/close commands via Zigbee2MQTT.

## Orignal Manual

<img class="img-responsive" alt="ZM25T Manual Page 1" src="{{ site.url }}/assets/images/20250721-ZM25T-Manual-Page-1.JPG">

<img class="img-responsive" alt="ZM25T Manual Page 2" src="{{ site.url }}/assets/images/20250721-ZM25T-Manual-Page-1.JPG">

I’ve attached the relevant MQTT configuration payload, remote control steps, and a copy of the manual below for anyone trying the same thing.

Hope this helps someone avoid the setup headaches I ran into!
