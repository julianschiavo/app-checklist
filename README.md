# ✅ The iOS App Checklist

> Making your iOS app the best it can be

The iOS App Checklist is a hand picked checklist of tons of improvements, nitpicks, and suggestions to make your iOS app the best it can be. It is in no way an extensive list, instead, it is intended to help you check your app and make it better before release.

This list is mainly created with points from the [Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/ios/overview/) and [Jordan Morgan's great blog post](https://www.swiftjectivec.com/a-best-in-class-app/), which served as inspiration for this list.

<br>

## Sections

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

## Attention to Detail & User Experience

> As an app developer/designer, you have the opportunity to deliver an extraordinary product that rises to the top of the App Store charts. To do so, you'll need to meet high expectations for quality and functionality.

### Main
- **[Alternative App Icons](https://developer.apple.com/documentation/uikit/uiapplication/2806818-setalternateiconname):** Provide alternative app icons, for example, a dark icon, on iOS 10.3 and above to allow users to have more control
- **Audio:** Avoid using incorrect or inappropriate audio presets or settings so your app doesn't interfere in the playback of other apps unless necessary
- **Localization:** Aim to localize your app in all possible languages, and avoid missing strings or incorrect translations that may hinder the experience
- **Keyboards:** The correct [keyboard type](https://developer.apple.com/documentation/uikit/uitextinputtraits/1624457-keyboardtype) is always set and used to make it easier to enter information, and undocked iPad keyboard is supported without issues.
- **Progress:** Prefer using [progress indicators](https://developer.apple.com/documentation/uikit/uiprogressview) instead of [activity indicators](https://developer.apple.com/documentation/uikit/uiactivityindicatorview) wherever possible to provide the user a clearer knowledge of the current state and remaining time
- **Reviews:** Always use the [`StoreKit` review prompt](https://developer.apple.com/documentation/storekit/skstorereviewcontroller/2851536-requestreview) over any custom implementation so users don't have to exit your app. Do not ask too often, too soon, or during a task as it may impede or distract the user.
- **[State Restoration](https://developer.apple.com/documentation/uikit/uistaterestoring):** All apps should support state restoration and correctly restore tabs and screens after restarting
- **Status Bar:** Avoid hiding the status bar unless absolutely necessary. Show the [network activity indicator](https://developer.apple.com/design/human-interface-guidelines/ios/controls/progress-indicators/#network-activity-indicators) during lengthy network operations to let the user know.
- **Terminology:** All interface text is clear and concise. Use familiar, understandable words and phrases to avoid confusion. Take care when attempting to use humor.
- **[Undo/Redo](https://developer.apple.com/design/human-interface-guidelines/ios/user-interaction/undo-and-redo/):** Implement native or clear undo and redo actions so users instinctively know how to use your app

### Other
- Alerts have less than 3 options and preferably only 2. Avoid using Yes and No as button titles.
- Align text, images and buttons to shows users how information is related
- Attempt to call `UIApplication`'s [`open(_:options:completionHandler:)`](https://developer.apple.com/documentation/uikit/uiapplication/1648685-open) with the [universalLinksOnly](https://developer.apple.com/documentation/uikit/uiapplication/openexternalurloptionskey/1648680-universallinksonly) option before presenting a web view or `SFSafariViewController` to correctly use universal links
- Destructive actions always show a confirmation prompt
- Launch screen does not contain branding and as with system apps looks similar to the initial screen in the app
- Loading content should never impede usage or become annoying. Show all content as soon as it loads rather than waiting for all content to finish loading. Load content in the background to avoid users having to manually refresh.
- Margins are respected throughout, using the [`safeAreaLayoutGuide`](https://developer.apple.com/documentation/uikit/uiview/2891102-safearealayoutguide) on all views and the [`layoutMarginsGuide`](https://developer.apple.com/documentation/uikit/uiview/1622651-layoutmarginsguide) wherever possible to add additional padding
- Modality is used only when necessary and is never confusing
- Never distort or warp images from their intended aspect ratios
- Only use native UI elements or elements designed for a mobile screen, instead of elements that are hard to use such as normal web calendar pickers
- Pickers have a height of around 5 list values. Long lists should always use table views for easier selection.
- Prefer `performBatchUpdates` over `reloadData` on [`UITableView`](https://developer.apple.com/documentation/uikit/uitableview/2887515-performbatchupdates) and [`UICollectionView`](https://developer.apple.com/documentation/uikit/uicollectionview/1618045-performbatchupdates)
- Progress indicators within bars (such as navigation bars) have a transparent unfilled portion
- Screen transitions are always smooth and fluid, making good but not excessive use of animations
- Switches are only used in lists
- Table views deselect selected rows after coming back from a detail segue
- Test for memory leaks and high memory/CPU usage frequently to avoid unnecessary power consumption or battery usage
- Text should always be a minimum of 11 points so it's legible without zooming
- The layout of your app should be organized, with controls close to the modifiable content
- Toolbars and tab bars are never shown on the same screen
- Use [UITextInputAssistantItem](https://developer.apple.com/documentation/uikit/uitextinputassistantitem)s to support common iPad tasks at home in the shortcuts bar
- Vector assets are preferred over normal images to support accessibility sizing and avoid blurry glyphs
- Your app is available and created with the same attention to detail on all platforms it makes sense (e.g. tvOS or watchOS)

<br>

## App Store

> The App Store lets you easily deliver apps to hundreds of millions of people around the world on their Mac, iPhone, iPad, Apple Watch, and Apple TV. With over $100 billion paid to developers and a rapid adoption rate of new software by Apple customers, it’s an incredible time to distribute on Apple platforms.

### Planning

- **[App Review](https://developer.apple.com/app-store/review/guidelines/):** Read the App Review Guidelines in depth to avoid [common rejections](https://developer.apple.com/app-store/review/rejections/).
- **[Business Model](https://developer.apple.com/app-store/business-models/):** Explore the main business models on the App Store and find the right one for your app. Clearly tell your users what they're signing up for, and avoid confusion or the feeling of being scammed for a great user experience
- **[Onboarding](https://developer.apple.com/design/human-interface-guidelines/ios/app-architecture/onboarding/):** Create a nice, interactive onboarding experience to introduce new users to your app. Make sure it's short and can be skipped for returning users. Never show your onboarding more than once.
- **[Localization](https://developer.apple.com/internationalization/):** Gain users around the world by localizing your app in other languages. Plan to correctly localize all aspects of the app experience, including the user interface, your App Store product page, marketing, support, and more.

### Presence

- **[App Store Product Page](https://developer.apple.com/app-store/product-page/):** Make sure your product page represents the incredible amount of work that went into your app by spending enough time on it. Use carefully researched keywords and categories to make it easy to find.
- **[App Previews](https://developer.apple.com/app-store/app-previews/):** Compelling App Previews spark interest and drive downloads, allowing users to preview your app before download/purchase
- **Size:** Keep your app small to allow for downloads on limited data networks and a happy user
- **[Pre-Orders](https://developer.apple.com/app-store/pre-orders/):** If it makes sense, allow users to pre-order your app before release 

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
- **[Low Power Mode](https://developer.apple.com/documentation/foundation/nsprocessinfo/1617047-lowpowermodeenabled?language=objc):** Low Power Mode is supported and network activity or less important tasks are suspended
- **Printing:** Printing is supported via [`UIPrintInteractionController`](https://developer.apple.com/documentation/uikit/uiprintinteractioncontroller) when it's suitable for the content or view
- **[Quick Look](https://developer.apple.com/design/human-interface-guidelines/ios/system-capabilities/quick-look/):** Quick Look is used to allow users to preview external content, such as documents or presentations, for example, to preview attachments in Mail
- **[Siri Intents](https://developer.apple.com/documentation/sirikit/creating_an_intents_app_extension):** If an appropriate [`SiriKit`](https://developer.apple.com/documentation/sirikit) domain is available for your app, it is implemented and works correctly, handling errors and failures. Intent domains are not misappropriated for unrelated or incorrect app types -- instead, consider using Siri Shortcuts.
- **[Siri Shortcuts](https://developer.apple.com/documentation/sirikit/soup_chef_accelerating_app_interactions_with_shortcuts):** Siri Shortcuts are implemented and donated to the system, whether only via an appropriate Siri Intent or separately, using [`INInteration`](https://developer.apple.com/documentation/sirikit/ininteraction) (preferred) for tasks, or [`NSUserActivity`](https://developer.apple.com/documentation/foundation/nsuseractivity) for views or screens
- **[Spotlight](https://developer.apple.com/documentation/corespotlight/making_content_searchable):** User generated or edited content is [indexed and searchable with Spotlight](https://developer.apple.com/documentation/corespotlight/making_content_searchable) for a seamless user experience
- **[Universal Links](https://developer.apple.com/documentation/uikit/core_app/allowing_apps_and_websites_to_link_to_your_content):** If your app is connected to a website or has sharable content, Universal Links are used to deeplink within the app
