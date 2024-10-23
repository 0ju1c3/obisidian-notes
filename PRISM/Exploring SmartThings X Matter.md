*Link Reference: https://support.smartthings.com/hc/en-us/articles/11219700390804-SmartThings-x-Matter-Integration
- https://www.youtube.com/watch?v=Czxv-fxNcH0

Matter - universal smart home device protocol designed to simplify device compatibility across platforms. 

Device compatibility across platforms refers to Matter’s ability to allow smart home devices to work seamlessly with different ecosystems (like SmartThings, Apple HomeKit, Google Home, etc.). With Matter, once a device is onboarded to one platform, it can be shared and controlled by other platforms without needing separate setup processes. This is achieved through Matter’s standardized protocols, enabling multi-admin support, where users can control devices through different apps or ecosystems, making smart home management more unified and flexible.

Imagine you have a smart light that supports Matter. You set it up using the SmartThings app on your Samsung phone, and it works perfectly. Now, if you also use Apple HomeKit for your smart home, you can control that same light from HomeKit without needing to reconfigure it, because Matter allows multiple platforms to share control of the device. This means you can use either the SmartThings or HomeKit app to turn on/off the light, creating a unified smart home experience across different systems.

In this example, Samsung (with SmartThings) and Apple (with HomeKit) are the two platforms, and the smart light is the Matter-compatible device. Matter allows both platforms to control the same smart light without needing separate setups, making it easier to manage devices across different ecosystems.

A **Matter Commissioner** is the device (like a smartphone) used to connect a smart device (e.g., a light bulb) to the system during setup. The **Matter Controller** is the hub (e.g., SmartThings Hub) responsible for controlling the device after it's onboarded. Finally, the **Matter Device** is the smart home device itself (e.g., a smart light) that can be controlled by the system once onboarded via the commissioner and managed by the controller

Compatible with :
- **Apple iOS (iPhone or iPad) and tvOS 16 (Apple TV) - "Home" app by Apple**: Fully working
- **Google Home Ecosystem (Android or Google Nest smart speakers/display) - "Google Home" app**: Fully working
- **Amazon Alexa (Amazon Echo smart speakers/displays)** : Fully working
- **Tuya Smart (SmartLife) app**: Fully working
- **Samsung SmartThings (Station or Hub v2 and later)**: Fully working
- **LG ThinQ**: Fully working, beside glitches in LG software sometimes
- **Home Assistant - Matter integration**: Fully working
- **Aqara Hub M3**: Aqara currently seem to not allow to pair test devices, so matter.js open source devices are not working with Aqara Hub M3. Please contact Aqara and request this feature.
- **Yandex Smart Home**: Yandex currently seem to not allow to pair test devices, so matter.js open source devices are not working with Yandex SMart Home. Please contact Yandex and request this feature.
- **flic**: Fully working
