# Archive: Mobile

- native base, ant design mobile rn, kitten ui, react native ui lib, shoutem ui, nachos ui, magnus ui
- themes
- animations, lottie, react-native-animatable, animated
- detox
- offline support
- qr codes
- integrations: shopify, magento, woocommerce, prestashop, opencart
- charts, react-native-charts-wrapper
- maps, https://github.com/react-native-maps/react-native-maps
- tables
- plan subscriptions
- calendars
- chat, https://github.com/FaridSafi/react-native-gifted-chat
- walkthrough, https://instamobile.io/app-templates/react-native-walkthrough-flow/
- instamobile
- expo framework
- tailwind-rn, react native elements
- icons, fonts, vector images, emoji, react-native-vector-icons, react-native-svg, react-native-emoji, https://oblador.github.io/react-native-vector-icons/
- native device features: camera, file upload, voice recording, geolocation, storage, faceid, fingerid, browserstack.com/docs/app-live/native-device-features
- push notifications
- splash screen
- onboarding
- in-app ads, facebook ads, google admob
- in-app payments, google payments, apple payments
- analytics
- stores publish
- app screenshot, davinciapps.com
- app icon
  - http://jgilfelt.github.io/AndroidAssetStudio/icons-launcher.html#foreground.space.trim=1&foreground.space.pad=0&foreColor=E8EAF6%2C0&crop=0&backgroundShape=square&backColor=3F51B5%2C100&effects=none&elevate=0
  - https://www.appicon.co/
- react native
- config, react-native-config
- env
- debug
- react navigation
- links / deep linking
- modals
- create react native app
- https://nativebase.io/, https://startup.nativebase.io/?utm_source=HomePage&utm_medium=Hero_Fold&utm_campaign=NativeBase_Market#explore
- https://github.com/ant-design/ant-design-mobile-rn
- https://reactnativeelements.com/
- https://akveo.github.io/react-native-ui-kitten/, https://github.com/akveo/kittenTricks
- https://wix.github.io/react-native-ui-lib/
- https://shoutem.github.io/docs/ui-toolkit/introduction
- https://onsen.io/
- https://github.com/vadimdemedes/tailwind-rn
- https://github.com/flatlogic/react-native-starter
- https://instamobile.io/app-templates/react-native-starter-kit-firebase/
- https://reactnativestarter.com/
- https://reactnativeseed.com/
- https://github.com/infinitered/ignite
- https://reactnative.directory/
- https://github.com/jondot/awesome-react-native
- https://expensify.com/
- https://codecanyon.net/category/mobile?platform=ReactJS
- https://instamobile.io/
- https://www.creative-tim.com/templates/react-native
- https://startreact.com/
- https://github.com/ReactNativeNews/React-Native-Apps
  Expo Framework
  Generate splashscreen, icons, screenshots Firebase (auth, CRUD, functions)
  Google Maps, Map layers
  GraphQL API / Apollo
  QR-Codes
  Animation
  Debug
  Tests
  Camera
  Media files, Files
  Contacts
  GPS Geolocation, IP Geolocation
  Touch Id, Apple Id, Face Id
  Apple Payment, Google Payment
  Apple In-app purchase, Google In-app purchase
  Push Notifications Ads
  Onboarding
  Emoji
  Charts
  Localization
  Device Orientation
  App Store, Google Play publishing
  debug performance
  Flipper?
  Reactotron?
  Hermes?
  https://instamobile.io/blog/
  https://engineering.tableau.com/react-native-performance-learnings-85f47ba38acb

```text
App Publish to App Store
#dev

Mac - Keychain Access app - menu Keychain Access - Certificate Assistant - Request a Certificate from a Certification Authority... - provide email address, common name - option Save to disk - continue - save

Developer portal - Certificates, Identifiers & Profiles - Certificates - add - Apple Distribution (required to sign production apps) - continue - Choose File - select a certificate from a previous step - continue - download - double click on the certificate - it will be installed to the Keychain Access app (need to reload to see changes)

Developer portal - Certificates, Identifiers & Profiles - Certificates - add - Apple Development (required to sign dev and staging apps) - continue - Choose File - select a certificate from a previous step - continue - download - double click on the certificate - it will be installed to the Keychain Access app (need to reload to see changes)

Developer portal - Certificates, Identifiers & Profiles - Identifiers - add - Register a New Identifier - App IDs - continue
- Bundle ID - Explicit -> past a bundle id from Xcode
- Platform - iOS
- Description - provide description
- Capabilities - optional
- continue - register

Developer portal - Certificates, Identifiers & Profiles - Profiles - Register a New Provisioning Profile - Development - iOS App Development - continue - select App ID (from a previous step) - continue - select a development certificate (from a previous step) - continue - select a specific device - continue - Provisioning Profile Name - provide a name (appname dev profile) - generate - download

Developer portal - Certificates, Identifiers & Profiles - Profiles - Register a New Provisioning Profile - Distribution - App Store - continue - select App ID (from a previous step) - continue - select a distribution certificate (from a previous step) - continue - Provisioning Profile Name - provide a name (appname prod profile) - generate - download

Xcode - Preferences - Accounts - add an Apple developer account

Xcode - Open a project in Xcode
```

cd appdir
open appname.xcworkspace

```

Xcode - Double click on 2 downloaded provisioning profiles from a previous step - that will install them to Xcode

Xcode - select a project (from a project navigator) - General - Bundle Identifier - the same as we provided on the Developer Portal (App ID)

Xcode - select a project (from a project navigator) - Build Settings - All - Signing section - Code Signing Identity
- Debug - select Apple Development cert from a previous step
- Release - select Apple Distribution from a previous step

Xcode - select a project (from a project navigator) - Signing & Capabilities
- Team - select an apple dev account
- Bundle Identifier: com.ibm.appname
- Deselect the option Automatically manage signing
- Signing (Debug) - Provisioning Profile - select a dev profile from a previous step
- Signing (Release) - Provisioning Profile - select a prod profile from a previous step

Xcode - select a project - top breadcrumbs menu - select Generic iOS Device - menu Product - Archive - that will create an archive (app bundle), it will be displayed in the menu Window - Organizer

Xcode - Window - Organizer - Archives - Distribute App - App Store Connect - Next
- Upload - will upload an archive to the App Store Connect - Prepare Information - Build section
- Export - select options 'Include Bitcode for iOS content' and 'Upload your app's symbols...' - next - select a prod profile, distribution profile - default Apple Distribution - next - export - export - will create a signed app.ipa file

Mac - install app Transporter

Transporter - add - select an app ipa - open - select the app - menu ... dots - verify - deliver - that will upload the app bundle to the App Store Connect - Activity

App Store Connect - Activity - Build - processing status - wait for build to complete -  build done status - select a build - review a build

App Store Connect - TestFlight - select a warning yellow icon -  Provide Export Compliance information - Select option (No) - Start internal Testing

App Store Connect - App Store Connect Users - select users - make internal tests

App Store Connect - refresh a page (2 or more times to see a new App ID)   - My Apps - add - New App
- Bundle Id - select the App ID (from a previous step)
- Primary Language - select a language
- Platform - iOS
- Name - provide a name
- SKU - provide a SKU (for internal use, no spaces)
- User Access - Full Access
- create

App Store Connect  - App Store - App Information
- Privacy Policy URL - provide an URl
- Category - provide a category

App Store Connect  - App Store - Pricing & Availability
- Price - select an option

App Store Connect  - App Store - Prepare for Submission
- Version Information - provide screenshots (Xcode or https://davinciapps.com/)
- Keywords - provide keywords
- Support URL - provide an url
- Marketing URL - optional
- Promotional text - provide a short description
- Description - provide a description
- Contact information - provide a personal info
- Build - provide an app build
- App Store Icon - provide an icon
- Version - provide a version
- Copyright - provide a copyright
- Rating - provide a rating
- App Review information - this info is for the Apple Certification Team (review)
- Version Release - select an option
- Submit for Review

Ref:
    * https://www.udemy.com/course/react-native-mobile-app-design-code-and-publish
    * https://www.youtube.com/watch?v=YPLs3xrDcm0

```
