pkgname=sext
pkgver=0.$(date +%s)
pkgrel=1
ver_sm=2.4.1 #seamonkey
ver_go=7.0.1 #gecko
pkgdesc="Altered seamonkey extensions"
arch=(any)
license=('GPL')
makedepends=(wget xmlstarlet proterozoic zip unzip sqlite3)
depends=(seamonkey=$ver_sm)
install=install
source=("https://static.addons.mozilla.net/_files/309/littlemonkey_for_seamonkey-1.8.76-sm.xpi"
		  "http://www.mirrorservice.org/sites/downloads.mozdev.org/xsidebar/mods/abduction!-2.026-mod.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/1865/adblock_plus-1.3.10-fn+fx+sm+tb.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/6623/betterprivacy-1.67-fx+sm.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/4550/compact_menu_2-4.3.1-fx+sb+sm+tb-linux.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/311084/cookiesafe_ff_4_compatible-3.1a5-sm+tb+fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/156490/duplicate_this_tab-1.2-fx+sm.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/2464/foxyproxy_standard-3.2-sm+tb+fx.xpi"
		  "https://www.eff.org/files/https-everywhere-latest.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/722/noscript-2.1.5-fn+sm+fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/1759/organize_status_bar-0.6.4-fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/953/refcontrol-0.8.15-sm+fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/9727/requestpolicy-0.5.22-sm+fx+fn.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/8016/show_my_password-2.0-fx+sm.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/3173/trackmenot-0.6.728-fx+sm.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/59/user_agent_switcher-0.7.3-fx+sm.xpi")
noextract=("${source[@]##*/}")
md5sums=("e4280b110334b67fcfc9567100ef7e5b"
			"94edd4b7cf9ecff3f00d2676739ab919"
			"a52cd05edee3aa3626dc318d0ab45b71"
			"33b09cca8c2984db1f61e3ace77c92b0"
			"269401fde20879ec4f869052a7c8a37d"
			"5b99c2c66a39e358aa64ae368a67d475"
			"bf79cc4bdb169eececd99abcc9456103"
			"e5fda8933f2d0ee5d618840e3c1677d2"
			"05ea1355a3f2e91b1ca10dd8bb88a7ea"
			"dc26a45a766c6853f66aabace2746e4d"
			"d8a91a585a2cf2a0e073c90e4b72f7c4"
			"8e8c3bf2b29fd174e9142da5a056013a"
			"1901bf5f998aae8ea277bc6495d92242"
			"5aa14241662f9b1ac446cf1f80e71047"
			"533d19c08df11939dbaa7f7952238ccf"
			"d7f1f4b3689bf61c3d583432872a4cc2")
# cookieswap
# beefree <-- breaks statusbar!
package() {
	 local smdir=$pkgdir/usr/lib/seamonkey-$ver_sm
	 mkdir -p $smdir/extensions
	 for xpi in $srcdir/*.xpi; do
		  echo "Fixing $(basename "$xpi") ..."
		  fix-extension $xpi $smdir/extensions
	 done
	 install -D {$srcdir/..,$smdir/defaults/profile/adblockplus}/patterns.ini
	 install -D {$srcdir/..,$smdir/defaults/profile}/localstore.rdf.sxt
	 install -D {$srcdir/..,$smdir/defaults/profile}/useragents.xml
	 install -D {$srcdir/..,$smdir/defaults/profile}/foxyproxy.xml
	 install -D {$srcdir/..,$smdir/defaults/pref}/local-settings.js
	 install -D {$srcdir/..,$smdir}/mozilla.cfg
	 sed -i \
		  -e s/%VER_SM%/$ver_sm/ig \
		  -e s/%VER_FF%/$ver_ff/ig \
		  -e s/%VER_GO%/$ver_go/ig $smdir/mozilla.cfg
	 sqlite3 $smdir/defaults/profile/permissions.sqlite < $srcdir/permissions.sqlite.dump 
}
