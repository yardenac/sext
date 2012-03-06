pkgname=sext
pkgver=0.$(date +%s)
pkgrel=1
ver_sm=2.7.1 #seamonkey
ver_go=10.0.1 #gecko
pkgdesc="Altered seamonkey extensions"
arch=(any)
license=('GPL')
makedepends=(wget xmlstarlet proterozoic zip unzip sqlite3)
depends=(seamonkey=$ver_sm)
install=install
source=("https://static.addons.mozilla.net/_files/309/littlemonkey_for_seamonkey-1.8.76-sm.xpi"
		  "http://www.mirrorservice.org/sites/downloads.mozdev.org/xsidebar/mods/abduction!-2.026-mod.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/1865/adblock_plus-2.0.3-sm+tb+fn+fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/6623/betterprivacy-1.68-fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/4550/compact_menu_2-4.3.1-fx+sb+sm+tb-linux.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/311084/cookiesafe_ff_4_compatible-3.1a5-sm+tb+fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/3255/cookieswap-0.5.284-fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/336172/copy_pure_text-2.0.1-sm+fx+tb.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/156490/duplicate_this_tab-1.2-fx+sm.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/220/flashgot-1.4-fx+sm+tb.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/2464/foxyproxy_standard-3.5-fx+sm+tb.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/337195/google_privacy-0.2.0-fx+sm.xpi"
		  "https://www.eff.org/files/https-everywhere-2.0development.4.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/722/noscript-2.3.2-fx+fn+sm.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/1759/organize_status_bar-0.6.4-fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/953/refcontrol-0.8.16-sm+fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/9727/requestpolicy-0.5.25-fx+sm.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/8016/show_my_password-2.0-fx+sm.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/3173/trackmenot-0.6.728-fx+sm.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/59/user_agent_switcher-0.7.3-fx+sm.xpi")
noextract=("${source[@]##*/}")
md5sums=("e4280b110334b67fcfc9567100ef7e5b"	# littlemonkey
			"94edd4b7cf9ecff3f00d2676739ab919"	# abduction
			"d0cc129401381a4701f4619212054266"	# adblock plus
			"efac8cd8fe05bf0a7d173f92e481e65a"	# betterprivacy
			"269401fde20879ec4f869052a7c8a37d"	# compact menu
			"5b99c2c66a39e358aa64ae368a67d475"	# cookiesafe
			"3bdc81f16f06a70968ec41792f4dd93e"	# cookieswap
			"29ff52ebd23ed5ab8e331a808dee9062"	# copy pure text
			"bf79cc4bdb169eececd99abcc9456103"	# duplicate this
			"df01da6e2b21fed352e0b4f8bb43669f"	# flashgot
			"e63201e4a4b5cd799aaf8fb75d5735e7"	# foxyproxy
			"e19444ddef4d7517d734d9d2d3fa1c35"	# google privacy
			"886996c0ae21f7287e0f2f7b05dfd80e"	# https everywhere
			"a3e048ffd4a925b6289008b856a72a31"	# noscript
			"d8a91a585a2cf2a0e073c90e4b72f7c4"	# organize status bar
			"72911f3df8cb79b9cfbce5a36296e03d"	# refcontrol
			"7b3d82f708d0f5df9f1db34c92428d5f"	# requestpolicy
			"5aa14241662f9b1ac446cf1f80e71047"	# show my password
			"533d19c08df11939dbaa7f7952238ccf"	# track me not
			"d7f1f4b3689bf61c3d583432872a4cc2")	# user agent switcher
# last checked for updates: Mar 6 2012
# fireshot
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

	 rps_section() { grep -Pzo '(?<=\['"${1}"'\]\n)[^[]*' $srcdir/../site-rules.txt; }
	 section_to_pref()  { echo        'pref("'"$2"'","'$(rps_section "$1")'");' >> $smdir/mozilla.cfg; }
	 section_to_dpref() { echo 'defaultPref("'"$2"'","'$(rps_section "$1")'");' >> $smdir/mozilla.cfg; }
	 section_to_pref	origins						extensions.requestpolicy.allowedOrigins
	 section_to_pref	destinations				extensions.requestpolicy.allowedDestinations
	 section_to_pref	origins-to-destinations	extensions.requestpolicy.allowedOriginsToDestinations
	 section_to_dpref	noscript-untrusted		noscript.untrusted
	 section_to_dpref	noscript-sites				capability.policy.maonoscript.sites

	 for section in origins destinations origins-to-destinations; do
		  echo "[$section]" >> $smdir/requestpolicy-rules.txt
		  rps_section "$section" >> $smdir/requestpolicy-rules.txt
	 done
	 sed -i '/^$/d' $smdir/requestpolicy-rules.txt # deletes empty lines

	 to_cookietype() {
		  while read; do
				echo "INSERT INTO \"moz_hosts\" VALUES(NULL,'${REPLY}','cookie',${1},0,0);"
		  done
	 }; {
		  cat $srcdir/../permissions.sqlite.dump
		  rps_section cookies-temp | to_cookietype 8
		  rps_section cookies-full | to_cookietype 1
		  echo "COMMIT;"
	 } | sqlite3 $smdir/defaults/profile/permissions.sqlite

	 # awful hack until fix-extension can deal with commented-out fields!
	 betterprivacy="$smdir/extensions/{d40f5e7b-d2cf-4856-b441-cc613eeffbe3}.xpi"
	 tmpfile=/tmp/.bp.$(date +%s)
	 unzip -qp "$betterprivacy" install.rdf >| $tmpfile
	 sed 's/<!--\(em:targetApplication.*\)-->/<\1>/' $tmpfile \
		  | rezip "$betterprivacy" install.rdf
	 rm -f "$tmpfile"
}
