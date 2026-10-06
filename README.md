# HNVPN — Việt Nam / Turkey VPN Hub

A mobile-friendly HTML website for managing OpenVPN profiles for Vietnam and Turkey. Supports profiles exported from OvpnSpider, private VPN servers, and public VPN Gate configurations.

**This website is a VPN profile manager. It does not establish a VPN tunnel in Safari or change another app's network connection. Use OpenVPN Connect on iPhone to import a profile and turn on the VPN. VNeID compatibility must be tested with the actual server and phone.**

## Publish with GitHub Pages

1. Open [Settings → Pages](https://github.com/nguyentuanphu/HNVPN/settings/pages).
2. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
3. Select branch **main** and folder **/(root)**, then click **Save**.
4. Wait for GitHub's Pages deployment to finish.
5. The expected website address is **https://nguyentuanphu.github.io/HNVPN/** once Pages is enabled and deployment succeeds.

No installation or build command is needed. All website files are at the repository root. `.nojekyll` disables Jekyll processing. Relative asset paths and the web app manifest work under `/HNVPN/`.

## iPhone / Add to Home Screen

1. Open the published HTTPS address in Safari.
2. Choose **Share → Add to Home Screen**.
3. Install [OpenVPN Connect](https://apps.apple.com/app/openvpn-connect/id590379981).
4. Export a working `.ovpn` profile from OvpnSpider to Files, or obtain one from your own VPN server.
5. In HNVPN, select Vietnam or Turkey, import the profile, then share or download it.
6. Import the file in OpenVPN Connect, allow the VPN configuration, and enable the connection.
7. Open VNeID and record whether it worked using the buttons in the Hub.

Safari's share sheet may not list OpenVPN Connect. In that case save the `.ovpn` file to Files and import it from OpenVPN Connect. Country selection labels a profile; it does not verify the exit IP or activate a tunnel.

## Three profile sources

- **OvpnSpider:** reuse exported `.ovpn` configurations, especially a Vietnam server already tested with VNeID.
- **Private VPN:** bring profiles from servers or always-on devices in Vietnam and Turkey. No private VPN servers are provisioned by this repository.
- **Free servers:** open the official VPN Gate list, or import its CSV to filter `VN` and `TR`. Availability changes. No automatic server discovery backend is included.

## Privacy

Profiles remain in memory by default. Optional persistence uses this browser's `localStorage` and is not separately encrypted. Profiles may contain private keys. The app does not upload profile contents or collect VNeID credentials, OTPs, identity documents, or analytics. Your private `.ovpn` files should never be committed to this public repository.

The service worker does not cache HTML or profiles. Offline operation is not promised. VPN Gate is operated by volunteers and retains connection logs; assess the server operator when using identity services.

## Files

- `index.html`: complete responsive app, Vietnamese instructions, profile import/share/download, CSV filtering and locally recorded test results.
- `manifest.webmanifest`: Home Screen web app metadata.
- `icon.png`, `icon-512.png`: web app icons.
- `sw.js`: minimal service worker without an offline cache.
- `.nojekyll`: static GitHub Pages publishing.

## Verification

JavaScript syntax checks and focused profile-validation / CSV-parsing checks passed during creation. Actual iPhone share-sheet behavior, live VPN connections, and VNeID authentication have not been verified.

## Official references

- [OvpnSpider App Store description](https://apps.apple.com/au/app/vpn-proxy-ovpnspider/id928941628)
- [Apple packet tunnel providers](https://developer.apple.com/documentation/networkextension/packet-tunnel-provider)
- [OpenVPN profile import](https://openvpn.net/connect-docs/import-profile.html)
- [VPN Gate server list](https://www.vpngate.net/en/)
- [VPN Gate anti-abuse policy and logging](https://www.vpngate.net/en/about_abuse.aspx)
