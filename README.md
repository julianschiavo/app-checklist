# The iOS App Checklist
### Making your iOS app the best it can be

**Accessibility:** An accessible app supports accessibility features by design and gives everyone a great user experience, regardless of their capabilities or how they use their devices.
**Technologies:** Apple has a great range of APIs and technologies, and you should aim to use them the best you can. This doesn't mean using every single available framework; rather, you should identify which fit your app well and implement them in a well designed experience.
**Attention to Detail and User Experience:** To deliver an extraordinary product, you meet high expectations for quality and functionality, especially: clarity (utilizing legible, clear text and icons), deference (fluid motion and animations throughout your app, keeping content paramount), and depth (realistic motion, discoverability and hierarchy).
**App Store Presence:** This is by far the most nascent category I’ve been tracking, so its list is short. It includes best practices for the App Store.

## Accessibility

> People use Apple's accessibility features, such as reduced transparency, VoiceOver, and increased text size, to personalize how they interact with their devices in ways that work for them. An accessible app supports such personalizations by design and gives everyone a great user experience, regardless of their capabilities or how they use their devices.

[ ] **Accessibility Inspector**: The entire app produces no accessibility warnings and Screen Curtain works flawlessly

[ ] App Name: If the app name is not easily pronounced or is mispronounced by VoiceOver, [`CFBundleSpokenName`](https://developer.apple.com/documentation/bundleresources/information_property_list/cfbundlespokenname) is used in the Info.plist to tell the system the correct pronounciation
[ ] Colors: Color isn't the only way to differentiate between objects, and system colors are used to automatically adapt to system changes. Sufficient color contrast ratios are used everywhere
[ ] Drag and drop: If drag and drop is supported, use accessibility APIs to identify drag sources/drop targets (see [`accessibilityDragSourceDescriptors`](https://developer.apple.com/documentation/objectivec/nsobject/2891001-accessibilitydragsourcedescripto) and [`accessibilityDropPointDescriptors`](https://developer.apple.com/documentation/objectivec/nsobject/2891048-accessibilitydroppointdescriptor))
[ ] Dynamic Type: Most if not all text uses Dynamic Type and the layout correctly adapts to larger text sizes including larger accessibility sizes. Text is never truncated and custom fonts are rarely used, and if used, easy to read.
[ ] Haptics: If haptics are used, use the system defined haptics consistently in your app to avoid confusion
[ ] Hit target: All controls have a minimum hit target of at least 44pt by 44pt, so every user can interact with them
[ ] Language: Leading and trailing autolayout margins are preferred over left/right to adapt to right-to-left languages. Important text uses [`readableContentGuide`](https://developer.apple.com/documentation/uikit/uiview/1622644-readablecontentguide) to keep it within a readable width on larger devices.
[ ] Layout: Auto Layout is used and the app is displayed correctly on all supported devices, orientations, and multitasking modes
[ ] Motion: The Reduce Motion preference is respected and animations are drastically less prominent, or disabled.
[ ] Navigation: Predictable, logical and system-consistent navigation is used so users don't have trouble learning how to use your app
[ ] Smart Invert Colors: Color inversion is supported and functional, using [`accessibilityIgnoresInvertColors`](https://developer.apple.com/documentation/uikit/uiview/2865843-accessibilityignoresinvertcolors) for all images and videos (or app wide if it contains a dark UI)
[ ] Standard controls: Standard UI controls are used in the interface, so it automatically adapts to several accessibility preferences, such as Bold Text, Larger Text, Invert Colors, and Increase Contrast. All bar buttons have their [`landscapeImagePhone`](https://developer.apple.com/documentation/uikit/uibaritem/1616421-landscapeimagephone) and/or [`largeContentSizeImage`](https://developer.apple.com/documentation/uikit/uibaritem/2865917-largecontentsizeimage) set.
[ ] System gestures: Avoid overridding or blocking built in gestures such as those used to activate Notification Center or Control Center
[ ] Traits: [Accessibility traits](https://developer.apple.com/documentation/uikit/uiaccessibility/uiaccessibilitytraits) are used to tell the system how an element behaves, such as classifying a custom view as a [`button`](https://developer.apple.com/documentation/uikit/uiaccessibility/uiaccessibilitytraits/1620194-button)
[ ] Transparency: The Reduce Transparency preference is respected and blurring/vibrancy is reduced appropriately
[ ] VoiceOver: VoiceOver is completely supported and users can easily navigate to every control on the screen. Alternative text labels are provided for important elements, making navigation easier. 
