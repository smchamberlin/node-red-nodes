node-red-node-pi-mcp3008
========================

A <a href="http://nodered.org" target="_new">Node-RED</a> node to read from
the MCP3008 Analogue to Digital Converter,
such as the <a href="http://rasp.io/analogzero" target="_new">Rasp.io analogzero</a>, though it will work with breadboard versions also.

**Warning**: Input voltages must not exceed 3.3V

### Pre-requisites

You must ensure that SPI is enabled. For recent (2016) versions of Raspbian you can do this

 - Run `sudo raspi-config`
 - Select `9 - Advanced Options`
 - Select `A5 - SPI`
 - Select `yes` to enable SPI
 - Select `OK` to confirm
 - Select the `Finish` button

### Install

Run the following command in your Node-RED user directory - typically `~/.node-red`

        npm install node-red-node-pi-mcp3008

### Usage

Reads from an MCP3008 Analogue to Digital (ADC) chip on the Pi SPI CE0 connection.

You can either set a channel in the edit dialogue, or you can set the `msg.payload` to
select the channel dynamically. If so then the payload must be a value from 0 to 7.

Outputs a numeric `msg.payload` with a range of 0 to 1023, where 0 = 0V and 1023 = 3.3V (assuming you use the default 3.3V voltage reference).

**Hint**: use a `range` node to adjust the values to the range you want.

Also sets `msg.topic` to `adc/{the pin number}`
