## Ultraleap Leap Motion Sensor: Comprehensive 2025 Overview

### Current Status and Relevance

**Yes, Ultraleap's Leap Motion technology remains relevant in 2025**, though the company has undergone significant restructuring. In March 2025, Ultraleap was sold for parts: the hand-tracking business was acquired by musical instrument company Roli, while the haptics intellectual property was sold to US company SIM IP. Despite this corporate restructuring, the technology continues to be actively supported and used across various applications.[1][2][3][4]

### Latest Hardware: Leap Motion Controller 2

The **Leap Motion Controller 2** launched in July 2023 and represents a substantial upgrade over the original:[5][1]

**Key Specifications:**
- **Tracking Range:** 10-110 cm (vs. 80 cm in original)[6][5]
- **Field of View:** 160° × 160° (19% increase)[1][6]
- **Size:** 30% smaller (84mm × 20mm × 12mm)[6]
- **Weight:** 29 grams[6]
- **Power:** 25% lower consumption via USB-C[1][6]
- **Frame Rate:** 120 fps maximum[6]
- **Platform Support:** Windows, macOS, Linux, and Android XR2[1][6]
- **Price:** $139-$245 USD (varies by bundle)[7][8]

The original Leap Motion Controller has been officially retired, though legacy software support continues.[7]

***

### Current SDK and Software Platforms

#### Ultraleap Hyperion (Version 6.2.0) - Latest Release

**Hyperion** is Ultraleap's current flagship tracking software, replacing the Gemini V5 platform:[9][10]

**Download:** Available at the [Ultraleap downloads page](https://leap2.ultraleap.com/downloads/) for Windows, macOS, and Android[11][10][9]

**Key Features:**[12][10][9]
- Multiple tracking models optimized for specific use cases
- Microgestures tracking (millimeter-level precision)
- Hand-on-object tracking (22% improvement in robustness)
- AR marker/fiducial tracking support
- Direct camera hardware access for computer vision tasks
- Low-power and high-performance modes
- Compatible with Meta Quest devices
- 115 Hz output frequency

**Important Note:** Hyperion is **only compatible with Leap Motion Controller 2**, not the original controller. The two software versions (Gemini and Hyperion) cannot coexist on the same machine.[10]

#### Legacy Software

**Gemini V5.2+** remains available for users with original Leap Motion Controllers or SIR170/3Di devices. Legacy V2 and Orion drivers can be accessed through the legacy downloads section.[13][14][15][10]

***

### GitHub Projects and Developer Resources

#### Official Ultraleap/Leap Motion Repositories

**Main Organizations:**
- **Ultraleap GitHub:** https://github.com/ultraleap (active development)
- **Leap Motion GitHub:** https://github.com/leapmotion (143 repositories, mostly archived)[16][17]

**Most Popular Active Projects:**

1. **Unity Plugin** - https://github.com/ultraleap/UnityPlugin[18][19]
   - Latest Release: v7.2.0 (January 2025)[19]
   - Supports Unity 2021 LTS, 2022 LTS, and Unity 6
   - Includes Physical Hands, Interaction Engine, XR Hands support
   - Features hand recording, pose detection, fiducial marker tracking

2. **Unreal Plugin** - https://github.com/ultraleap/UnrealPlugin[20]
   - Supports Unreal Engine 4.27+
   - Windows, Android, and Linux builds supported
   - Includes interaction examples

3. **LeapJS** - https://github.com/leapmotion/leapjs[21]
   - JavaScript client for web applications
   - Compatible with Gemini V5 and Hyperion V6
   - 2,000+ stars on GitHub

4. **Ultraleap Tracking WebSocket** - https://github.com/ultraleap/UltraleapTrackingWebSocket[22]
   - Enables LeapJS compatibility with Gemini V5 and Hyperion
   - Provides WebSocket server for browser-based hand tracking
   - Active development (last updated February 2025)

5. **Project North Star** - https://github.com/leapmotion/ProjectNorthStar[23][16]
   - Open-source AR headset design files
   - 1,700+ stars
   - Hardware blueprints and assembly guides

**Notable Community Projects:**[24][25][26]
- **PyLeapMouse** - Python-based Leap Motion mouse control
- **aframe-leap-hands** - A-Frame VR component for Leap Motion
- **VRChat OSC finger tracking** - Integration with VRChat
- Various Unity/Unreal game projects and gesture recognition systems

---

### Documentation and Developer Links

**Official Resources:**
- **Main Documentation:** https://docs.ultraleap.com[27][28]
- **API Reference:** https://docs.ultraleap.com/api-reference/[29]
- **Unity Getting Started:** https://docs.ultraleap.com/xr-and-tabletop/xr/unity/getting-started/[30]
- **Unreal Getting Started:** https://docs.ultraleap.com/xr-and-tabletop/xr/unreal/getting-started/[31]
- **Support Portal:** https://support.ultraleap.com[32][28]
- **Downloads Page:** https://leap2.ultraleap.com/downloads/

**Platform Compatibility:**[14][30]
- Unity: Fully supported (2021 LTS, 2022 LTS, Unity 6)[19]
- Unreal: Fully supported (UE 4.27+)[20][31]
- OpenXR: Native support via XR extensions[33]
- Linux: Ubuntu 22.04 LTS supported[34]

***

### Current Applications and Use Cases (2025)

The technology remains actively deployed across multiple sectors:

**Enterprise & Industrial:**[35][36][37]
- VR training and simulation (manufacturing safety, surgical training)
- 3D design review and CAD manipulation
- Automotive AR HUDs with mid-air gesture control[38]
- Healthcare applications and surgical navigation[39]
- Robotics control and telepresence[1]

**XR Development:**[40][35][12]
- Hand tracking for VR/AR headsets (Varjo, Pico, HTC Vive)[41][33]
- VTubing and motion capture[42][43]
- Museum exhibits and interactive installations[43]
- Gaming and entertainment[44]

**Research & Education:**[45][46]
- Computer vision research datasets
- Gesture recognition algorithm development
- Academic publications (800+ citations in recent literature)[47][45]

**Consumer Applications:**[43][1]
- Touchless kiosk interfaces
- Music creation and performance
- Sign language interpretation
- Desktop/tabletop 3D interaction

***

### Market Position and Competition (2025)

**Advantages:**[5][35][40]
- World-class accuracy with 27 joint tracking[35][1]
- Low latency (sub-perception threshold)
- Platform flexibility (cross-OS support)
- Strong enterprise integration partnerships
- Extensive developer ecosystem and documentation

**Challenges:**[48][49][50]
- Declining standalone sensor demand as Quest and Vision Pro include built-in hand tracking
- Corporate restructuring and layoffs (halved workforce in 2024)[49][50]
- Market shift toward integrated solutions over external modules
- Limited consumer market adoption compared to enterprise

**Hand Tracking Market Growth:**[51]
- Global market: $2.3 billion (2024) → projected $10.9 billion (2033)
- 19.7% CAGR forecast through 2033
- Driven by VR/AR adoption, healthcare, automotive sectors

**Alternatives:**[52][53][40]
- **MediaPipe** (Google) - Free, webcam-based hand tracking
- **Meta Quest** - Built-in hand tracking
- **Apple Vision Pro** - Integrated hand/eye tracking
- **SenseGlove, bHaptics, Manus** - Haptic glove competitors

***

### Key Developments in 2025

1. **Ambient Light Hand Tracking** - Software-only solution eliminating IR illumination requirement, demonstrated at CES 2025[2]
2. **Roli Acquisition** - Hand tracking division sold to Roli for musical instrument integration (March 2025)[3][4]
3. **Continued Software Updates** - Unity Plugin 7.2.0 released (January 2025) with Unity 6 support[19]
4. **Hyperion on Steam** - Available as downloadable software platform[54]
5. **Event Sensor Integration** - Partnership with Prophesee for low-power AR hand tracking[55]

***

### Purchasing and Availability

**Where to Buy (2025):**
- **Official:** RobotShop, VR Expert, Thingbits[8][6][1]
- **Retail Partners:** Adafruit, Best Buy, Amazon, Newegg[52][1]
- **Pricing:** $139 (controller only) to $245+ (XR bundle with mount and commercial license)[8]
- **Used Market:** eBay, secondary markets ($75-$700 depending on condition and bundle)[56]

**Note:** Original Leap Motion Controller availability is limited to used markets, as production has ceased.[7]

***

### Conclusion: Is It Still Relevant?

**Yes, for specific use cases:**

✅ **Highly Relevant For:**
- Enterprise VR/AR development and prototyping
- Research and academic projects requiring precise hand tracking
- Robotics and computer vision applications
- Cross-platform development (Windows/Mac/Linux/Android)
- Applications requiring external sensor flexibility
- Developers needing direct camera hardware access

⚠️ **Less Relevant For:**
- Consumer VR gaming (Meta Quest, PSVR2 have integrated tracking)
- Casual users seeking plug-and-play solutions
- Budget-conscious projects (integrated solutions may be cheaper)

The technology continues to evolve with active SDK support, strong documentation, extensive GitHub projects, and new innovations like ambient light tracking. Despite corporate restructuring, the developer ecosystem remains robust, making it a viable choice for professional applications requiring high-precision hand tracking in 2025.[2][12][40][19][1]

[1](https://www.adafruit.com/product/5758)
[2](https://www.linkedin.com/posts/ultraleap_ces2025-handtracking-ar-activity-7283219533178273794-HTPK)
[3](https://sifted.eu/articles/tencent-ultraleap-sold-for-parts-news)
[4](https://www.linkedin.com/posts/kains_tencent-backed-xr-startup-ultraleap-sold-activity-7303821200252719104-6UZa)
[5](https://blog.learnxr.io/extended-reality/ultraleap-leap-motion-controller-2)
[6](https://www.thingbits.net/products/leap-motion-controller-2)
[7](https://skarredghost.com/2023/05/31/ultraleap-leap-motion-controller-2/)
[8](https://vr-expert.com/vr-headsets/vr-accessories/buy-ultraleap-leap-motion-controller-2/)
[9](https://docs.ultraleap.com/hand-tracking/Hyperion/index.html)
[10](https://support.ultraleap.com/hc/en-us/articles/18588870878493-Hyperion-Product-Information)
[11](https://support.ultraleap.com/hc/en-us/articles/18565334783389-Getting-Started-with-Hyperion)
[12](https://develop3d.com/vr-ar-mr/ultraleap-hyperion-upgrades-hand-tracking-for-micro-gesture-details/)
[13](https://docs.ultraleap.com/hand-tracking/gemini-migration.html)
[14](https://support.ultraleap.com/hc/en-us/articles/15037715327517-Ultraleap-product-compatibility-guide)
[15](https://www.reddit.com/r/leapmotion/comments/1bfdfqg/ultraleap_software_v2_or_orion_download/)
[16](https://github.com/leapmotion)
[17](https://github.com/orgs/leapmotion/repositories)
[18](https://github.com/ultraleap/UnityPlugin)
[19](https://github.com/ultraleap/UnityPlugin/releases)
[20](https://github.com/ultraleap/UnrealPlugin)
[21](https://github.com/leapmotion/leapjs)
[22](https://github.com/ultraleap/UltraleapTrackingWebSocket)
[23](https://leapmotion.github.io/ProjectNorthStar/)
[24](https://github.com/topics/leapmotion-controller)
[25](https://www.github-zh.com/topics/leap-motion)
[26](https://github.com/openleap)
[27](https://docs.ultraleap.com)
[28](https://docs.ultraleap.com/useful-links.html)
[29](https://docs.ultraleap.com/api-reference/tracking-api/leapc-guide/leap-concepts.html)
[30](https://docs.ultraleap.com/xr-and-tabletop/xr/unity/getting-started/index.html)
[31](https://docs.ultraleap.com/xr-and-tabletop/xr/unreal/getting-started/index.html)
[32](https://support.ultraleap.com/hc/en-us/articles/360004339957-How-do-I-download-the-SDK)
[33](https://varjo.com/blog/introducing-integrated-hand-tracking-for-varjo-xr-4-series)
[34](https://docs.ultraleap.com/linux/)
[35](https://www.xrtoday.com/mixed-reality/ultraleap-leap-motion-controller-review/)
[36](https://www.luminousxr.com/case-studies/reducing-injurys-with-xr-and-hand-tracking/)
[37](https://varjo.com/blog/how-hand-tracking-unlocks-enterprise-use-cases-guest-post-by-ultraleap)
[38](https://www.basemark.com/news/basemark-and-ultraleap-collaborate-to-add-haptics-and-hand-tracking-to-ar-huds/)
[39](https://www.sciencedirect.com/science/article/pii/S0010482525008996)
[40](https://www.xrtoday.com/mixed-reality/the-xr-eye-hand-tracking-vendor-for-2024/)
[41](https://forum.dcs.world/topic/337911-ultraleap-leap-motion-controller-2-handtracking-enhancing-vr-experience/)
[42](https://www.reddit.com/r/leapmotion/comments/1n9f8e0/how_can_i_in_2025_record_leap_motion_data_into_a/)
[43](https://docs.ultraleap.com/ultralab/spatial-design-for-2d.html)
[44](https://github.com/topics/leapmotion)
[45](https://arxiv.org/abs/2311.04373)
[46](https://www.nature.com/articles/s41597-024-03968-9)
[47](https://www.sciencedirect.com/science/article/pii/S2590291123001377)
[48](https://www.uploadvr.com/ultraleap-selling-leap-motion-amid-layoffs/)
[49](https://www.roadtovr.com/hand-tracking-ultraleap-layoff-2024/)
[50](https://mixed-news.com/en/ultraleap-is-reportedly-halving-its-workforce-and-tries-to-sell-the-hand-tracking-division/)
[51](https://dataintelo.com/report/hand-tracking-solutions-market)
[52](https://aircada.com/blog/leap-motion-alternatives)
[53](https://www.cbinsights.com/company/ultrahaptics/alternatives-competitors)
[54](https://store.steampowered.com/app/2705560/Ultraleap_Hyperion/)
[55](https://www.setsquared.co.uk/ultraleap-and-prophesee-unite-to-deliver-hand-tracking-tech/)
[56](https://www.ebay.com/shop/leap-motion-2?_nkw=leap+motion+2)
[57](https://www.reddit.com/r/leapmotion/comments/1nsb8hw/has_original_leap_motion_sdk_been_upgraded_to/)
[58](https://en.wikipedia.org/wiki/Leap_Motion)
[59](https://github.com/leapmotion/leapuvc)
[60](https://www.youtube.com/watch?v=sAvmNoAGLLM)
[61](https://docs.ultraleap.com/hand-tracking/getting-started.html)
[62](https://unboundxr.com/ultraleap-leap-motion-controller-2-xr-enterprise-edition)
[63](https://docs.ultraleap.com/hand-tracking/)
[64](https://github.com/ksandom/installUltraleap)
[65](https://www.youtube.com/watch?v=WMiNFHdENXM)
[66](https://docs.ultraleap.com/xr-guidelines/Getting%20started/virtual-hands.html)
[67](https://www.reddit.com/r/leapmotion/)
[68](https://www.hackster.io/news/ultraleap-goes-smaller-lighter-and-higher-resolution-with-the-new-leap-motion-controller-2-6ecf5fc23668)
[69](https://www.reddit.com/r/Ultraleap/comments/1aq8r6r/leap_motion_1_usb_2_or_3/)
[70](https://support.ultraleap.com/hc/en-us/articles/18729461772829-About-the-original-Leap-Motion-Controller)
[71](https://docs.ultraleap.com/xr-and-tabletop/tabletop/index.html)
[72](https://docs.ultraleap.com/unity-api/)
[73](https://docs.ultraleap.com/xr-and-tabletop/xr/index.html)
[74](https://www.reddit.com/r/Ultraleap/comments/1kwqthm/ultraleap_unity_plugin_720_silently_fails_to/)
[75](https://docs.ultraleap.com/pico/developer-resources.html)
[76](https://github.com/orgs/ultraleap/repositories)
[77](https://learn.microsoft.com/en-us/windows/mixed-reality/mrtk-unity/mrtk2/supported-devices/leap-motion-mrtk?view=mrtkunity-2022-05)
[78](https://docs.lookingglassfactory.com/community/using-leap-motion-with-looking-glass)
[79](https://seesawlabs.com/archive/augmented-reality-interaction/)
[80](https://docs.ultraleap.com/hand-tracking/Hyperion/trackingmodels.html)
[81](https://warped3.substack.com/p/leap-motion)
[82](https://www.reddit.com/r/IAmA/comments/46h763/i_am_david_holz_cto_and_cofounder_of_leap_motion/)
[83](https://esastar-publication-ext.sso.esa.int/ESATenderActions/details/138094)
[84](https://www.continuevr.com/motion-capture-systems-leap-motion)
[85](https://sourceforge.net/projects/ultraleap-unity-plugin.mirror/)
[86](https://www.reddit.com/r/VirtualYoutubers/comments/1j6gucl/not_good_news_for_hand_tracking/)
[87](https://slashdot.org/software/p/Ultraleap-Gemini/alternatives)
[88](https://sourceforge.net/software/product/Ultraleap-Gemini/alternatives)
[89](https://camelcamelcamel.com/product/B00E3CP9UM)
[90](https://ipfray.com/erich-spangenbergs-soon-to-be-public-sim-ip-buys-patent-portfolio-worth-hundreds-of-millions-in-haptics-and-extended-reality-xr/)
[91](https://docs.ultraleap.com/quest/setup-your-software.html)
[92](https://www.immersivewire.com/p/ultraleap-sold-for-parts-and-laid-off-more-than-half-of-staff)
[93](https://support.ultraleap.com/hc/en-us/articles/360005517598-What-software-should-I-use-if-I-am-on-a-Mac)
[94](https://www.reddit.com/r/leapmotion/comments/16ninzq/where_to_buy_preowned_leap_motion_controller_for/)
