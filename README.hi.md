<p align="center">
  <a href="https://opencode.ai">
    <picture>
      <source srcset="packages/console/app/src/asset/logo-ornate-dark.svg" media="(prefers-color-scheme: dark)">
      <source srcset="packages/console/app/src/asset/logo-ornate-light.svg" media="(prefers-color-scheme: light)">
      <img src="packages/console/app/src/asset/logo-ornate-light.svg" alt="OpenCode logo">
    </picture>
  </a>
</p>
<p align="center">ओपन सोर्स AI कोडिंग एजेंट।</p>
<p align="center">
  <a href="https://opencode.ai/discord"><img alt="Discord" src="https://img.shields.io/discord/1391832426048651334?style=flat-square&label=discord" /></a>
  <a href="https://www.npmjs.com/package/opencode-ai"><img alt="npm" src="https://img.shields.io/npm/v/opencode-ai?style=flat-square" /></a>
  <a href="https://github.com/anomalyco/opencode/actions/workflows/publish.yml"><img alt="Build status" src="https://img.shields.io/github/actions/workflow/status/anomalyco/opencode/publish.yml?style=flat-square&branch=dev" /></a>
</p>

<p align="center">
  <a href="README.md">English</a> |
  <a href="README.zh.md">简体中文</a> |
  <a href="README.zht.md">繁體中文</a> |
  <a href="README.ko.md">한국어</a> |
  <a href="README.de.md">Deutsch</a> |
  <a href="README.es.md">Español</a> |
  <a href="README.fr.md">Français</a> |
  <a href="README.it.md">Italiano</a> |
  <a href="README.da.md">Dansk</a> |
  <a href="README.ja.md">日本語</a> |
  <a href="README.pl.md">Polski</a> |
  <a href="README.ru.md">Русский</a> |
  <a href="README.bs.md">Bosanski</a> |
  <a href="README.ar.md">العربية</a> |
  <a href="README.no.md">Norsk</a> |
  <a href="README.br.md">Português (Brasil)</a> |
  <a href="README.th.md">ไทย</a> |
  <a href="README.tr.md">Türkçe</a> |
  <a href="README.uk.md">Українська</a> |
  <a href="README.bn.md">বাংলা</a> |
  <a href="README.gr.md">Ελληνικά</a> |
  <a href="README.vi.md">Tiếng Việt</a> |
  <a href="README.hi.md">हिन्दी</a>
</p>

[![OpenCode Terminal UI](packages/web/src/assets/lander/screenshot.png)](https://opencode.ai)

---

### स्थापना

```bash
# YOLO
curl -fsSL https://opencode.ai/install | bash

# पैकेज मैनेजर
npm i -g opencode-ai@latest        # or bun/pnpm/yarn
scoop install opencode             # Windows
choco install opencode             # Windows
brew install anomalyco/tap/opencode # macOS and Linux (recommended, always up to date)
brew install opencode              # macOS and Linux (official brew formula, updated less)
sudo pacman -S opencode            # Arch Linux (Stable)
paru -S opencode-bin               # Arch Linux (Latest from AUR)
mise use -g opencode               # Any OS
nix run nixpkgs#opencode           # or github:anomalyco/opencode for latest dev branch
```

> [!TIP]
> स्थापना से पहले 0.1.x से पुराने संस्करणों को हटा दें।

### डेस्कटॉप ऐप (बीटा)

OpenCode डेस्कटॉप एप्लिकेशन के रूप में भी उपलब्ध है।. [Release page](https://github.com/anomalyco/opencode/releases) या [opencode.ai/download](https://opencode.ai/download) से सीधे डाउनलोड करें।

| प्लेटफॉर्म              | डाउनलोड                              |
| --------------------- | ------------------------------------- |
| macOS (Apple Silicon) | `opencode-desktop-darwin-aarch64.dmg` |
| macOS (Intel)         | `opencode-desktop-darwin-x64.dmg`     |
| Windows               | `opencode-desktop-windows-x64.exe`    |
| Linux                 | `.deb`, `.rpm`, or AppImage           |

```bash
# macOS (Homebrew)
brew install --cask opencode-desktop
# Windows (Scoop)
scoop bucket add extras; scoop install extras/opencode-desktop
```

#### स्थापना निर्देशिका

इंस्टॉल स्क्रिप्ट इंस्टॉलेशन पथ के लिए निम्नलिखित प्राथमिकता क्रम का पालन करती है:

1. `$OPENCODE_INSTALL_DIR` - कस्टम इंस्टॉलेशन निर्देशिका
2. `$XDG_BIN_DIR` - XDG बेस डायरेक्टरी स्पेसिफिकेशन अनुरूप पथ
3. `$HOME/bin` - मानक उपयोगकर्ता बाइनरी निर्देशिका (यदि यह मौजूद है या बनाई जा सकती है)
4. `$HOME/.opencode/bin` - डिफ़ॉल्ट फ़ॉलबैक

```bash
# उदाहरण
OPENCODE_INSTALL_DIR=/usr/local/bin curl -fsSL https://opencode.ai/install | bash
XDG_BIN_DIR=$HOME/.local/bin curl -fsSL https://opencode.ai/install | bash
```

### एजेंट

OpenCode में दो बिल्ट-इन एजेंट शामिल हैं जिनके बीच आप `Tab` कुंजी से स्विच कर सकते हैं।

- **build** - डिफ़ॉल्ट, विकास कार्य के लिए पूर्ण-पहुंच एजेंट
- **plan** - विश्लेषण और कोड अन्वेषण के लिए केवल-पठन एजेंट
  - फ़ाइल संपादन डिफ़ॉल्ट रूप से अस्वीकार करता है
  - बैश कमांड चलाने से पहले अनुमति मांगता है
  - अपरिचित कोडबेस की खोज या परिवर्तनों की योजना बनाने के लिए आदर्श

जटिल खोजों और बहु-चरणीय कार्यों के लिए एक सामान्य उप-एजेंट भी शामिल है।
इसका उपयोग आंतरिक रूप से किया जाता है और संदेशों में `@general` का उपयोग करके इसे आमंत्रित किया जा सकता है।

[एजेंटों के बारे में](https://opencode.ai/docs/agents) अधिक जानें।.

### दस्तावेज़ीकरण

OpenCode को कॉन्फ़िगर करने के तरीके के बारे में अधिक जानकारी के लिए, [**हमारे दस्तावेज़ों पर जाएँ**](https://opencode.ai/docs)।.

### योगदान

यदि आप OpenCode में योगदान करने में रुचि रखते हैं, तो कृपया पुल रिक्वेस्ट सबमिट करने से पहले हमारे [योगदान दस्तावेज़](./CONTRIBUTING.md) पढ़ें।

### OpenCode पर निर्माण

यदि आप OpenCode से संबंधित किसी प्रोजेक्ट पर काम कर रहे हैं और अपने नाम के भाग के रूप में "opencode" का उपयोग कर रहे हैं, उदाहरण के लिए "opencode-dashboard" या "opencode-mobile", तो कृपया अपने README में एक नोट जोड़ें कि यह OpenCode टीम द्वारा नहीं बनाया गया है और हमारे साथ किसी भी तरह से संबद्ध नहीं है।

### सामान्य प्रश्न

#### यह क्लाउड कोड से किस प्रकार भिन्न है?

क्षमता के मामले में यह Claude Code के समान ही है। मुख्य अंतर यहां दिए गए हैं:

- 100% ओपन सोर्स
- किसी भी प्रदाता से बंधा नहीं। हालाँकि हम [OpenCode Zen](https://opencode.ai/zen) के माध्यम से प्रदान किए गए मॉडलों की सलाह देते हैं, OpenCode का उपयोग Claude, OpenAI, Google, या यहां तक कि स्थानीय मॉडलों के साथ भी किया जा सकता है। जैसे-जैसे मॉडल विकसित होंगे, उनके बीच का अंतर कम होता जाएगा और कीमतें गिरती जाएंगी, इसलिए प्रदाता-अज्ञेयवादी होना महत्वपूर्ण है।
- आउट-ऑफ-द-बॉक्स LSP समर्थन
- TUI पर ध्यान केंद्रित। OpenCode नियोविम उपयोगकर्ताओं और [terminal.shop](https://terminal.shop) के निर्माताओं द्वारा बनाया गया है; हम टर्मिनल में संभव की सीमाओं को आगे बढ़ाने जा रहे हैं।
- एक क्लाइंट/सर्वर आर्किटेक्चर। यह, उदाहरण के लिए, OpenCode को आपके कंप्यूटर पर चलने की अनुमति दे सकता है जबकि आप इसे मोबाइल ऐप से दूरस्थ रूप से संचालित करते हैं, जिसका अर्थ है कि TUI फ्रंटएंड संभावित क्लाइंट में से केवल एक है।

---

**हमारे समुदाय से जुड़ें** [Discord](https://discord.gg/opencode) | [X.com](https://x.com/opencode)
