# The iOS App Checklist

> Making your iOS app the best it can be

**Accessibility:** An accessible app supports accessibility features by design and gives everyone a great user experience, regardless of their capabilities or how they use their devices.

**Attention to Detail and User Experience:** To deliver an extraordinary product, you meet high expectations for quality and functionality, especially: clarity (utilizing legible, clear text and icons), deference (fluid motion and animations throughout your app, keeping content paramount), and depth (realistic motion, discoverability and hierarchy).

**Technologies:** Apple has a great range of APIs and technologies, and you should aim to use them the best you can. This doesn't mean using every single available framework; rather, you should identify which fit your app well and implement them in a well designed experience.

**App Store Presence:** This is by far the most nascent category I’ve been tracking, so its list is short. It includes best practices for the App Store.

<br>

## Accessibility

> People use Apple's accessibility features, such as reduced transparency, VoiceOver, and increased text size, to personalize how they interact with their devices in ways that work for them. An accessible app supports such personalizations by design and gives everyone a great user experience, regardless of their capabilities or how they use their devices.

- **Accessibility Inspector**: The entire app produces no accessibility warnings and Screen Curtain works flawlessly
- **App Name:** If the app name is not easily pronounced or is mispronounced by VoiceOver, [`CFBundleSpokenName`](https://developer.apple.com/documentation/bundleresources/information_property_list/cfbundlespokenname) is used in the Info.plist to tell the system the correct pronounciation
- **Colors:** Color isn't the only way to differentiate between objects, and system colors are used to automatically adapt to system changes. Sufficient color contrast ratios are used everywhere
- **Drag and Drop:** If drag and drop is supported, use accessibility APIs to identify drag sources/drop targets (see [`accessibilityDragSourceDescriptors`](https://developer.apple.com/documentation/objectivec/nsobject/2891001-accessibilitydragsourcedescripto) and [`accessibilityDropPointDescriptors`](https://developer.apple.com/documentation/objectivec/nsobject/2891048-accessibilitydroppointdescriptor))
- **Dynamic Type:** Most if not all text uses Dynamic Type and the layout correctly adapts to larger text sizes including larger accessibility sizes. Text is never truncated and custom fonts are rarely used, and if used, easy to read.
- **Haptics:** If haptics are used, use the system defined haptics consistently in your app to avoid confusion
- **Hit Target:** All controls have a minimum hit target of at least 44pt by 44pt, so every user can interact with them
- **Language:** Leading and trailing autolayout margins are preferred over left/right to adapt to right-to-left languages. Important text uses [`readableContentGuide`](https://developer.apple.com/documentation/uikit/uiview/1622644-readablecontentguide) to keep it within a readable width on larger devices.
- **Layout:** Auto Layout is used and the app is displayed correctly on all supported devices, orientations, and multitasking modes
- **Motion:** The Reduce Motion preference is respected and animations are drastically less prominent, or disabled.
- **Navigation:** Predictable, logical and system-consistent navigation is used so users don't have trouble learning how to use your app
- **Smart Invert Colors:** Color inversion is supported and functional, using [`accessibilityIgnoresInvertColors`](https://developer.apple.com/documentation/uikit/uiview/2865843-accessibilityignoresinvertcolors) for all images and videos (or app wide if it contains a dark UI)
- **Standard Controls:** Standard UI controls are used in the interface, so it automatically adapts to several accessibility preferences, such as Bold Text, Larger Text, Invert Colors, and Increase Contrast. All bar buttons have their [`landscapeImagePhone`](https://developer.apple.com/documentation/uikit/uibaritem/1616421-landscapeimagephone) and/or [`largeContentSizeImage`](https://developer.apple.com/documentation/uikit/uibaritem/2865917-largecontentsizeimage) set.
- **System Gestures:** Avoid overridding or blocking built in gestures such as those used to activate Notification Center or Control Center
- **Traits:** [Accessibility traits](https://developer.apple.com/documentation/uikit/uiaccessibility/uiaccessibilitytraits) are used to tell the system how an element behaves, such as classifying a custom view as a [`button`](https://developer.apple.com/documentation/uikit/uiaccessibility/uiaccessibilitytraits/1620194-button)
- **Transparency:** The Reduce Transparency preference is respected and blurring/vibrancy is reduced appropriately
- **VoiceOver:** VoiceOver is completely supported and users can easily navigate to every control on the screen. Alternative text labels are provided for important elements, making navigation easier. 

<br>

## Technologies

> Developing for Apple platforms puts cutting-edge technology at your fingertips, giving you limitless ways to bring incredible apps to users around the world. These powerful platforms each offer unique capabilities and user experiences, yet integrate tightly to form a true ecosystem. Hardware, software, and services are designed from the ground up to work together so you can build intuitive, multi-faceted experiences that are genuinely seamless.

- **3D Touch:** On supported devices, 3D Touch is directly integrated in the entire app, including support for [Peek and Pop](https://developer.apple.com/documentation/uikit/peek_and_pop/implementing_peek_and_pop) and [Homescreen Quick Actions](https://developer.apple.com/documentation/uikit/peek_and_pop/add_home_screen_quick_actions)
- **AirDrop:** Where it makes sense, data including images or content can be shared via AirDrop, using the native [`UIActivityViewController`](https://developer.apple.com/documentation/uikit/uiactivityviewcontroller)
- **[AirPlay](https://developer.apple.com/documentation/avfoundation/airplay_2/getting_airplay_2_into_your_app):** Apps that provide media playback support AirPlay streaming—not just mirroring—for the best user experience. If AirPlay is supported, the [system-provided media player](https://developer.apple.com/documentation/avkit/avplayerviewcontroller) is used and the control is prominently displayed.
- **[Drag and Drop](https://developer.apple.com/documentation/uikit/drag_and_drop):** Content and items support drag and drop, including for reordering/internally and to external apps
- **[Extensions](https://developer.apple.com/app-extensions/):** Suitable and meaningful app extensions are included and designed with the same attention to detail and style as the rest of the app, such as a File Provider for document based apps or a Today Widget to provide quick updates or enable short tasks 
- **[Handoff](https://developer.apple.com/handoff/):** If a Mac counterpart app is available, Handoff allows users to seamlessly resume activities on another device or on the website
- **[Keyboard Shortcuts](https://developer.apple.com/documentation/uikit/uikeycommand):** The keyboard is thoroughly supported and available throughout the app, especially on iPad
- **Live Photos:** Any Live Photos displayed or used are clearly distinguished with movement or a badge and use [`PHLivePhotoView`](https://developer.apple.com/documentation/photokit/phlivephotoview) for playback
- **Low Power Mode:** Low Power Mode is supported and network activity, 
- **Printing:** Printing is supported via [`UIPrintInteractionController`](https://developer.apple.com/documentation/uikit/uiprintinteractioncontroller) when it's suitable for the content or view
- **[Siri Intents](https://developer.apple.com/documentation/sirikit/creating_an_intents_app_extension):** If an appropriate [`SiriKit`](https://developer.apple.com/documentation/sirikit) domain is available for your app, it is implemented and works correctly, handling errors and failures. Intent domains are not misappropriated for unrelated or incorrect app types -- instead, consider using Siri Shortcuts.
- **[Siri Shortcuts](https://developer.apple.com/documentation/sirikit/soup_chef_accelerating_app_interactions_with_shortcuts):** Siri Shortcuts are implemented and donated to the system, whether only via an appropriate Siri Intent or separately, using [`INInteration`](https://developer.apple.com/documentation/sirikit/ininteraction) (preferred) for tasks, or [`NSUserActivity`](https://developer.apple.com/documentation/foundation/nsuseractivity) for views or screens
- **[Spotlight](https://developer.apple.com/documentation/corespotlight/making_content_searchable):** User generated or edited content is [indexed and searchable with Spotlight](https://developer.apple.com/documentation/corespotlight/making_content_searchable) for a seamless user experience
- **[Universal Links](https://developer.apple.com/documentation/uikit/core_app/allowing_apps_and_websites_to_link_to_your_content):** If your app is connected to a website or has sharable content, Universal Links are used to deeplink within the app
