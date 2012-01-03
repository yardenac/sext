pkgname=sext
pkgver=0.$(date +%s)
pkgrel=1
ver_sm=2.6.1 #seamonkey
ver_go=9.0.1 #gecko
pkgdesc="Altered seamonkey extensions"
arch=(any)
license=('GPL')
makedepends=(wget xmlstarlet proterozoic zip unzip sqlite3)
depends=(seamonkey=$ver_sm)
install=install
source=("https://static.addons.mozilla.net/_files/309/littlemonkey_for_seamonkey-1.8.76-sm.xpi"
		  "http://www.mirrorservice.org/sites/downloads.mozdev.org/xsidebar/mods/abduction!-2.026-mod.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/1865/adblock_plus-2.0.2-sm+tb+fx+fn.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/6623/betterprivacy-1.67-fx+sm.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/4550/compact_menu_2-4.3.1-fx+sb+sm+tb-linux.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/311084/cookiesafe_ff_4_compatible-3.1a5-sm+tb+fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/3255/cookieswap-0.5.284-fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/336172/copy_pure_text-2.0.1-sm+fx+tb.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/156490/duplicate_this_tab-1.2-fx+sm.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/2464/foxyproxy_standard-3.4-sm+tb+fx.xpi"
		  "https://static.addons.mozilla.net/_files/337195/google_privacy-0.0.3-sm+fx.xpi"
		  "https://www.eff.org/files/https-everywhere-2.0development.4.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/722/noscript-2.2.5-fx+sm+fn.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/1759/organize_status_bar-0.6.4-fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/953/refcontrol-0.8.16-sm+fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/9727/requestpolicy-0.5.24-sm+fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/8016/show_my_password-2.0-fx+sm.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/3173/trackmenot-0.6.728-fx+sm.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/59/user_agent_switcher-0.7.3-fx+sm.xpi")
noextract=("${source[@]##*/}")
md5sums=("e4280b110334b67fcfc9567100ef7e5b"	# littlemonkey
			"94edd4b7cf9ecff3f00d2676739ab919"	# abduction
			"046f4caa44c9315dfb4315f51d4182d1"	# adblock plus
			"33b09cca8c2984db1f61e3ace77c92b0"	# betterprivacy
			"269401fde20879ec4f869052a7c8a37d"	# compact menu
			"5b99c2c66a39e358aa64ae368a67d475"	# cookiesafe
			"3bdc81f16f06a70968ec41792f4dd93e"	# cookieswap
			"29ff52ebd23ed5ab8e331a808dee9062"	# copy pure text
			"bf79cc4bdb169eececd99abcc9456103"	# duplicate this
			"ad68af9d50925ada9f1c7497715cc48f"	# foxyproxy
			"80d3522d1d278418f2378b384a29b58a"	# google privacy
			"886996c0ae21f7287e0f2f7b05dfd80e"	# https everywhere
			"a39dc4d114654c03a13126a00d7e8d94"	# noscript
			"d8a91a585a2cf2a0e073c90e4b72f7c4"	# organize status bar
			"72911f3df8cb79b9cfbce5a36296e03d"	# refcontrol
			"27e84e43e5c9ab0151e2cff0565eb6c1"	# requestpolicy
			"5aa14241662f9b1ac446cf1f80e71047"	# show my password
			"533d19c08df11939dbaa7f7952238ccf"	# track me not
			"d7f1f4b3689bf61c3d583432872a4cc2")	# user agent switcher
# last checked for updates: Jan 3 2012
# customizations for addblock plus
# fireshot
# flashgot
# optimize google
# proxy tool
# beefree <-- breaks statusbar!
package() {
	 local smdir=$pkgdir/usr/lib/seamonkey-$ver_sm
	 mkdir -p $smdir/extensions
	 for xpi in $srcdir/*.xpi; do
		  echo "Fixing $(basename "$xpi") ..."
		  fix-extension $xpi $smdir/extensions
	 done
	 rm -f $smdir/extensions/https-everywhere@eff.org/chrome/content/rules/GoogleMaps.xml~HEAD
	 install -D {$srcdir/..,$smdir/defaults/profile/useragentswitcher}/useragents.xml
	 install -D {$srcdir/..,$smdir/defaults/profile/adblockplus}/patterns.ini
	 install -D {$srcdir/..,$smdir/defaults/profile}/localstore.rdf.sxt
	 install -D {$srcdir/..,$smdir/defaults/profile}/foxyproxy.xml
	 install -D {$srcdir/..,$smdir/defaults/pref}/local-settings.js
	 install -D {$srcdir/..,$smdir}/mozilla.cfg
	 sed -i \
		  -e s/%VER_SM%/$ver_sm/ig \
		  -e s/%VER_FF%/$ver_ff/ig \
		  -e s/%VER_GO%/$ver_go/ig $smdir/mozilla.cfg
	 sqlite3 $smdir/defaults/profile/permissions.sqlite < $srcdir/../permissions.sqlite.dump 

	 for thing in Origins/origins Destinations/destinations \
		  OriginsToDestinations/origins-to-destinations; do
		  echo 'pref("extensions.requestpolicy.allowed'${thing%%/*}'","'$(
				grep -Pzo '(?<=\['${thing##*/}'\]\n)[^[]*' \
					 $srcdir/../requestpolicy-settings.txt
		  )'");' >> $smdir/mozilla.cfg
	 done
}
