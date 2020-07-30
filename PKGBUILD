# Maintainer: Eric Lay <ericlaytm@gmail.com>

pkgname=micro-manjaro
pkgver=2.0.6
pkgrel=1
pkgdesc="A modern and intuitive terminal-based text editor"
arch=('aarch64')
url="https://micro-editor.github.io"
license=('MIT')
depends=('dash')
optdepends=('xclip: Option for copying/pasting text on X11'
            'xsel: Option for copying/pasting text on X11'
            'wl-clipboard: Required for copying/pasting text on Wayland'
            'st-manjaro: For desktop icon to work')
provides=("${pkgname%-*}")
conflicts=("${pkgname%-*}")
source=("https://github.com/zyedidia/micro/releases/download/v$pkgver/${pkgname%-*}-$pkgver-linux-arm64.tar.gz"
        'bindings.json'
        "${pkgname%-*}.desktop"
        "${pkgname%-*}-keymap.service"
        "${pkgname%-*}-st"
        'settings.json'
        'supplemental.kmap'
        'tcelldb')
sha256sums=('9e046f5e4380409e72b3195e9e0e03d3b8750a2f95ccd4cfe9447494d7e5fa6f'
            'f3938b123859ab89194d2ddac6f603cd051bfd5b8d858dd109edab53987936a8'
            'cc0abf6aac771a5e19afe6fa2ac8b61aae806b656583bd8c747df9943afb47ea'
            '6879af4da1853c0c83a65465a8565d9aff2439521b8fe10a2a8ae777f3599483'
            '2aab23389b8153ca9299f3a576173498b62ba558598d8a62cd4d2f1d296db66c'
            'bc651a7b3f6ca6b3e8652a2d20da1fa1c56bf7a92a2c7c6beb1b7ea9d4199d96'
            '25ec4626dd99caad38040db308d5b7aa2afac73e50f212f9f1ee90963e2a77d5'
            '2cbe3bb64551720a055c5efbd5758fb39af7e9e6ef1de46087b74295df78cb26')

package() {
	cd "${pkgname%-*}-$pkgver"
	install -Dm755 "${pkgname%-*}" "$srcdir/${pkgname%-*}-st" -t "$pkgdir/usr/bin"
	install -Dm644 LICENSE -t "$pkgdir/usr/share/licenses/${pkgname%-*}"
	install -Dm644 "$srcdir/${pkgname%-*}.desktop" -t "$pkgdir/usr/share/applications"
	install -Dm644 "$srcdir/"{bindings.json,settings.json} -t "$pkgdir/etc/skel/.config/${pkgname%-*}"
	install -Dm644 "$srcdir/tcelldb" "$pkgdir/etc/skel/.tcelldb"
	install -Dm644 "$srcdir/${pkgname%-*}-keymap.service" -t "$pkgdir/usr/lib/systemd/system"
	install -Dm644 "$srcdir/supplemental.kmap" -t "$pkgdir/usr/share/kbd/keymaps"
}
