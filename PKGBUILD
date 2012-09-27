pkgname=sext
pkgver=0.$(date +%s)
pkgrel=1
ver_sm=2.12.1 #seamonkey
ver_go=15.0 #gecko
ver_ff=15.0.1 #firefox
pkgdesc="Altered seamonkey extensions"
arch=(any)
license=('GPL')
makedepends=(wget xmlstarlet proterozoic zip unzip sqlite3)
depends=(seamonkey=$ver_sm)
install=install
pastvers=(2.5 2.6 2.6.1 2.7 2.7.1 2.7.2 2.8 2.9 2.10 2.11)
extensions=("{b0e1b4a6-2c6f-4e99-94f2-8e625d7ae255}"
				"{d40f5e7b-d2cf-4856-b441-cc613eeffbe3}"
				"{57068FBE-1506-42ee-AB02-BD183E7999E4}"
				"{9D23D0AA-D8F5-11DA-B3FC-0928ABF316DE}"
				"cookieSwap@cookieSwap.mozdev.org.xpi"
				"copy-pure-text@kashiif-gmail.com"
				"duplicate-this-tab@mozilla.org"
				"{19503e42-ca3c-4c27-b1e2-9cdb2170ee34}"
				"foxyproxy@eric.h.jung"
				"{ea61041c-1e22-4400-99a0-aea461e69d04}"
				"https-everywhere@eff.org"
				"{73a6fe31-595d-460b-a920-fcc0f8843232}"
				"{35106bca-6c78-48c7-ac28-56df30b51d2c}"
				"{455D905A-D37C-4643-A9E2-F6FEFAA0424A}"
				"requestpolicy@requestpolicy.com"
				"{cd617372-6743-4ee4-bac4-fbf60f35719e}"
				"trackmenot@mrl.nyu.edu"
				"{e968fc70-8f95-4ab9-9e79-304de2a71ee1}")
themes=({122352a8-6caf-46ca-998c-784e320cad7c})
source=("https://static.addons.mozilla.net/_files/309/littlemonkey_for_seamonkey-1.8.76-sm.xpi"
		  "http://downloads.mozdev.org/xsidebar/mods/abduction_screen_capture-3.0.14-mod.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/1865/adblock_plus-2.1.2-sm+an+fx+tb.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/6623/betterprivacy-1.68-fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/1368/colorfultabs-16.2-sm+fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/4550/compact_menu_2-4.3.1-fx+sb+sm+tb-linux.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/311084/cookiesafe_ff_4_compatible-3.1a5-sm+tb+fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/3255/cookieswap-0.5.284-fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/336172/copy_pure_text-2.0.1-sm+fx+tb.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/156490/duplicate_this_tab-1.3-fx+sm.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/220/flashgot-1.4.8.2-tb+fx+sm.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/2464/foxyproxy_standard-3.6.2-sm+tb+fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/337195/google_privacy-0.2.1-fx+sm.xpi"
		  "https://www.eff.org/files/https-everywhere-3.0development.7.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/722/noscript-2.5.6-sm+fx+fn.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/1759/organize_status_bar-0.6.4-fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/953/refcontrol-0.8.16-sm+fx.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/9727/requestpolicy-0.5.27-fx+sm.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/8016/show_my_password-2.0-fx+sm.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/3173/trackmenot-0.6.728-fx+sm.xpi"
		  "http://releases.mozilla.org/pub/mozilla.org/addons/59/user_agent_switcher-0.7.3-fx+sm.xpi")
noextract=("${source[@]##*/}")
md5sums=("e4280b110334b67fcfc9567100ef7e5b"	# littlemonkey
			"969fb1037482120a1d81ae0253e36319"	# abduction
			"4693cca56c4811080b1a9e13fad0e085"	# adblock plus
			"efac8cd8fe05bf0a7d173f92e481e65a"	# betterprivacy
			"0f2a3885613a2d24bf032cddd0433440"	# colorfultabs
			"269401fde20879ec4f869052a7c8a37d"	# compact menu
			"5b99c2c66a39e358aa64ae368a67d475"	# cookiesafe
			"3bdc81f16f06a70968ec41792f4dd93e"	# cookieswap
			"29ff52ebd23ed5ab8e331a808dee9062"	# copy pure text
			"83a4c672016723021e38ed4925dd491f"	# duplicate this
			"01c2400e040a722842e255d9dab85e37"	# flashgot
			"c84a71a4961b6608eaa9652375706b16"	# foxyproxy
			"c9410748ba428b4a723392e86bc646c0"	# google privacy
			"dada8e1592b0a981cb8860f4588dfad6"	# https everywhere
			"63536cbbacd432694369af5bfcde261e"	# noscript
			"d8a91a585a2cf2a0e073c90e4b72f7c4"	# organize status bar
			"72911f3df8cb79b9cfbce5a36296e03d"	# refcontrol
			"f772e5c1ac31706a3211d0d4bab190a3"	# requestpolicy
			"5aa14241662f9b1ac446cf1f80e71047"	# show my password
			"533d19c08df11939dbaa7f7952238ccf"	# track me not
			"d7f1f4b3689bf61c3d583432872a4cc2")	# user agent switcher
# last checked for updates: Sep 26 2012
# fireshot
# proxy tool
# beefree <-- breaks statusbar!
build() {
	 sed -i \
		  -e "s/^\(ver_sm=\).*$/\1$ver_sm/" \
		  -e "s/^\(pastvers=\).*$/\1(${pastvers[*]})/" $startdir/install
}
package() {
	 local smdir=$pkgdir/usr/lib/seamonkey-$ver_sm ffdir=$pkgdir/usr/lib/firefox
	 local smprof=$smdir/defaults/profile ffprof=$ffdir/defaults/profile
	 local xpi section extension theme n=0
	 mkdir -p $smdir/extensions $ffdir/extensions $ffdir/defaults/profile
	 for xpi in $srcdir/*.xpi; do
		  echo "Fixing $(basename "$xpi") ..."
		  fix-extension $xpi $smdir/extensions
	 done
	 install -D {$smdir,$ffdir}/extensions/{57068FBE-1506-42ee-AB02-BD183E7999E4}.xpi
	 rm -f $smdir/extensions/https-everywhere@eff.org/chrome/content/rules/GoogleMaps.xml~HEAD
	 install -D {$srcdir/..,$smprof/useragentswitcher}/useragents.xml
	 install -D {$srcdir/..,$smprof/adblockplus}/patterns.ini
	 install -D {$srcdir/..,$smprof}/localstore.rdf.sxt
	 install -D {$srcdir/..,$smprof}/foxyproxy.xml
	 install -D {$srcdir/..,$smprof}/cert_override.txt
	 install -D {$srcdir/..,$ffprof}/cert_override.txt
	 install -D {$srcdir/..,$smdir/defaults/pref}/local-settings.js
	 install -D {$srcdir/..,$ffdir/defaults/pref}/local-settings.js
	 install -D {$srcdir/..,$smdir}/mozilla.cfg
	 install -D $srcdir/../mozilla.ff.cfg $ffdir/mozilla.cfg
	 install -D $srcdir/../localstore.ff.rdf $ffdir/defaults/profile/localstore.rdf
	 sed -i \
		  -e s/%VER_SM%/$ver_sm/ig \
		  -e s/%VER_FF%/$ver_ff/ig \
		  -e s/%VER_GO%/$ver_go/ig {$smdir,$ffdir}/mozilla.cfg

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
	 } | sqlite3 $smprof/permissions.sqlite

	 {
		  echo '[ExtensionDirs]'
		  n=0; for extension in "${extensions[@]}"; do
				echo "Extension$n=/usr/lib/seamonkey-$ver_sm/extensions/$extension.xpi"
				let ++n
		  done
		  echo $'\n[Themedirs]'
		  n=0; for theme in "${themes[@]}"; do
				echo "Extension$n=/usr/lib/seamonkey-$ver_sm/themes/$theme.xpi"
				let ++n
		  done
	 } >| $smprof/extensions.ini

	 # awful hack until fix-extension can deal with commented-out fields!
	 betterprivacy="$smdir/extensions/{d40f5e7b-d2cf-4856-b441-cc613eeffbe3}.xpi"
	 tmpfile=/tmp/.bp.$(date +%s)
	 unzip -qp "$betterprivacy" install.rdf >| $tmpfile
	 sed 's/<!--\(em:targetApplication.*\)-->/<\1>/' $tmpfile \
		  | rezip "$betterprivacy" install.rdf
	 rm -f "$tmpfile"
}
