- **BridgedDevicesNode**: This example shows how to build a Matter-Bridge that offers multiple OnOff lights and sockets as a bridge. It can be configured via command line and allows for specifications of shell commands to be executed when on and off commands are received at the numbered devices. For more details see below.
	- The **BridgedDevicesNode** example explains how to create a "Matter Bridge" that controls several devices, like smart lights or sockets, all connected through a single bridge. You can control each device separately (for example, turning lights or sockets on and off) by sending commands from the bridge.
	- **Simple Example**: Imagine you have 3 smart lights in your home—Light 1, Light 2, and Light 3—and they're all connected through one controller (the "bridge"). When you want to turn Light 1 on or off, the bridge receives your command and passes it to Light 1.
	- You can configure this setup through the command line, where you specify which light should turn on or off and even run custom actions when these commands are received. For example, you can set the command to also run a shell script that logs every time Light 1 is turned on or off.
	- In summary, **BridgedDevicesNode** is like a remote that controls multiple smart devices (like lights or sockets), all managed through one "bridge." You can send commands via a command line and customize the actions that happen when these devices are switched on or off.

---

## ComposedDeviceNode
- This example shows how to build a "simple" composed device where multiple OnOff lights and sockets are combined as a single device. The devices are all added at the root level, so no bridge is used. It can be configured via command line and allows for specifications of shell commands to be executed when on and off commands are received at the numbered devices. For more details see below.
- The **ComposedDeviceNode** is an example of a smart device that combines several smaller devices (like OnOff lights and sockets) into one single, larger device. Instead of having a separate "bridge" to control the lights and sockets, all the devices are directly added at the root level, meaning they act as one big device. You can control them via command line and specify what happens (like running a command) when you turn them on or off.

### Example:
Imagine you have two smart lights and two smart sockets in a room. Instead of controlling them individually or through a bridge (which groups them under one controller), you set them up as one **composed device**. So, when you send an "on" command, both the lights and the sockets react together, acting like a single device. You can configure what happens when they turn on/off through command line options, such as executing specific shell commands.

### Difference from **BridgedDevicesNode**:
- **BridgedDevicesNode**: Uses a **bridge** to connect multiple devices (like lights and sockets). The bridge groups these devices, but they are still individual devices controlled through the bridge.
    - Think of the bridge as a "middleman" between the controller and the devices.
- **ComposedDeviceNode**: Combines multiple devices into **one single device**. There’s no bridge acting as an intermediary; instead, they are all treated as part of a larger, unified device.
    - Here, no "middleman" exists. The devices are directly added to the root and controlled together as one entity.

In simple terms:
- **BridgedDevicesNode**: Devices are separate, but connected through a bridge.
- **ComposedDeviceNode**: Devices are combined and act as one larger device.

---


- **DeviceNode**: This example shows how to build a simple minimalistic DeviceNode with just one socket or light endpoint. The shell commands to be executed by on/off commands can be configured via CLI.

---
## DeviceNodeFull: 
- This example shows how to build a simple Device node with just one socket or light endpoint. The shell commands to be executed by on/off commands can be configured via CLI. Additionally, this example also shows the following use cases:
    - it shows how to enable BLE for a device node and tweaks the announcement so that BLE is only announced in the beginning.
    - it includes a dummy WifiNetworkCommissioning and a dummy ThreadNetworkCommissioning implementation that simulates Wi-Fi/Thread logic for the commissioner and logs the Wi-Fi/Thread credentials the commissioner sends to the device.
    - it enhances the GeneralDiagnostics and OnOff cluster to implement some commands with its own logic.
    - it defines the ["My Fancy Functionality" custom cluster](https://github.com/project-chip/matter.js/blob/main/packages/examples/src/examples/cluster/MyFancyOwnFunctionality.ts) and adds this to the OnOff endpoint as additional cluster when the chosen vendorId is set to 0xfff4 (65524)
    - it implements the callbacks where developers can get information on commissioning changes and session/connection changes to better know the status of the node.
	The **DeviceNodeFull** example demonstrates how to create a smart device, like a socket or light, that can be controlled with commands (like turning it on or off). You can configure the commands using the command line (CLI). This example adds several extra features to the basic device.

### Key Features and Simple Explanations:

1. **Enabling Bluetooth (BLE)**: 
   The device can use Bluetooth for communication, but only announces itself through Bluetooth when it starts up. This is useful if you only need Bluetooth for initial setup.

   - **Example**: Imagine you buy a smart light. When you first turn it on, it shows up in your phone’s Bluetooth list, allowing you to pair it. After setup, it stops showing up in the list to save energy.

2. **Simulated Wi-Fi and Thread Setup**:
   This includes fake or "dummy" setups for both **Wi-Fi** and **Thread** networks. These are simulations to mimic how a real Wi-Fi or Thread network might send data, like network passwords, to the device. The device logs the credentials it receives but doesn't actually use them.

   - **Example**: Imagine a smart socket that logs the Wi-Fi password you send during setup, but it's just a simulation for testing, so it doesn't actually connect to the Wi-Fi.

3. **Enhanced Device Logic**:
   The **GeneralDiagnostics** and **OnOff cluster** (which manages turning the device on and off) are improved. This means the developer added custom logic to handle specific commands in a unique way.

   - **Example**: Maybe the light has special behavior, like flashing three times when turned on, or logs extra diagnostic information about its status.

4. **Custom Cluster ("My Fancy Functionality")**:
   A new custom feature is added to the device, called "My Fancy Functionality," which is added to the light or socket’s basic on/off capabilities. This feature is only added when a specific vendor ID is provided (in this case, 0xfff4).

   - **Example**: Imagine your smart light comes with a special "color-changing" feature, but only when set up by a specific manufacturer. If the vendor ID matches, the light gets the color-changing ability as an extra feature.

5. **Callbacks for Setup and Connection Changes**:
   The device can inform the developer about changes in its setup process (like during commissioning, when the device is connected to a network for the first time) and changes in connection status (such as losing or gaining connection).

   - **Example**: If the smart socket loses Wi-Fi connection, it can trigger a notification to let you know about the status change.

### Putting It All Together:
Imagine you have a smart socket that can be controlled via an app. It initially uses Bluetooth for setup, then logs the Wi-Fi password you send (without actually connecting to Wi-Fi). It also has a custom feature, like showing power consumption data, but only if the manufacturer has enabled it. The socket can also notify you if it loses connection to the network or is being set up.

In summary, **DeviceNodeFull** is a more advanced example of creating a smart device with extra features, including Bluetooth setup, custom commands, simulated network handling, and notifications for connection changes.

---

# MultiDeviceNode:
- This example shows how to start multiple Matter nodes on one MatterServer where each node is run on its own Port, but share a single MDNS broadcaster and scanner in order to optimize resources. Each node can be configured via CLI to be an onoff socket or a light. CLI. Options also allow specification of shell commands to be executed for on and off commands.
- The **MultiDeviceNode** concept is about running multiple smart devices (or _nodes_) on a single server while using fewer resources by sharing some common components. Let’s break it down step by step with an example.
- Imagine you want to control multiple smart devices (like a smart light and a smart socket) through one server (called **MatterServer**). Instead of starting each device with its own separate resources (like a scanner to detect other devices and a broadcaster to send signals), you can make them share some of those resources to save memory and processing power.

### How does it work?

- **Single Server**: You have one **MatterServer** running.
- **Multiple Nodes**: You can run multiple smart devices (called **nodes**) on the server, each operating independently.
- **Shared Resources**: All these nodes use the same **MDNS broadcaster** and **scanner** (these are like the “eyes and ears” of the devices, helping them detect and communicate with other devices on the network).
- **Unique Ports**: Each node (device) operates on its own port, making it unique while still sharing common components like broadcasting and scanning.

### Example

Let’s say you have:

1. A **smart light**
2. A **smart socket**

#### Without MultiDeviceNode:

You might run two completely separate processes for each device. Each one would have its own broadcaster and scanner. This can use up more system resources (like memory and CPU power).

#### With MultiDeviceNode:

Both the smart light and the smart socket can share a single broadcaster and scanner, but they still act like independent devices on the network, each using its own port.

1. **Smart Light** runs on port **5000** and responds to commands like turning on/off or adjusting brightness.
2. **Smart Socket** runs on port **5001** and responds to commands like powering on/off an appliance.

They share the same scanner to detect other devices and the same broadcaster to send their signals, but they still work independently.

---

- **SensorDeviceNode**: This example shows how to build a simple Sensor device with a temperature (default) or humidity (`--type humidity`) sensor. The sensor values are updated by default every 60 seconds, or the number of seconds specified via the CLI parameter `--interval`. The value can be defined by the output of a CLI script provided via parameter `--value` or, if no command is specified, are randomly set in the interval -50..+50. To read the Temperature of a Raspberry Pi as example use `--value ="echo \$((\$(</sys/class/thermal/thermal_zone0/temp)/10))"` or to read temperature of your location `--value="curl -s 'wttr.in/?format=%t\&m' | sed 's/°C//'| awk '{print \$1*100}'"` (or use `?format=%h` for humidity).
Additionally, these two examples are not directly configurable by CLI and mainly show how to implement different combinations of devices:
- **IlluminatedRollerShade**: This example implements the Window Covering cluster server logic and also overrides a OnOff cluster server to build a composed devices with a window covering nd a light.
- **LightDevice**: This example shows how to run a Light device which is not configurable via CLI and only logs changes, so it is the most minimalistic example. It shows how to enhance the OnOff cluster server with own logic.
- **MeasuredSocketDevice**: This example shows how to run a simple socket device that also includes a power and energy measurement. It is not configurable via CLI and only sets random energy and power values when turned on.
## Controller example
[](https://github.com/project-chip/matter.js/blob/main/packages/examples/README.md#controller-example)
- **ControllerNode**: This example shows basically how a controller could be implemented by showing pairing and connections to a paired device. When there is an OnOff Endpoint with ID 1 then this is controlled and toggled.

---

# Parameters
**view : https://github.com/project-chip/matter.js/blob/main/packages/examples/README.md#controller-example from CLI usage**
- -clearstorage: the storage location will be reset on start of the process. The sorage location is set via parameter "-store" (see concrete examples below)
- -loglevel: the log level to use (default: debug, possible values: fatal, error, warn, info, debug)
- -logformat: the log format to use (default: ansi (if executed in a shell/tty), else plain, possible values: ansi, plain, html)
- 