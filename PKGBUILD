pkgname=sext
pkgver=0.$(date +%s)
pkgrel=1
ver_sm=2.19 #seamonkey
ver_go=22.0 #gecko
ver_ff=22.0 #firefox
pkgdesc="Altered seamonkey extensions"
arch=(any)
license=('GPL')
makedepends=(wget xmlstarlet proterozoic zip unzip sqlite3)
depends=(seamonkey=$ver_sm)
install=install
pastvers=(2.16 2.16.1 2.16.2 2.17 2.17.1)
source=("https://static.addons.mozilla.net/_files/309/littlemonkey_for_seamonkey-1.8.76-sm.xpi"
		  "http://downloads.mozdev.org/xsidebar/mods/abduction_screen_capture-3.0.14-mod.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/1865/adblock_plus-2.2.4-tb+fx+sm+an.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/6623/betterprivacy-1.68-fx.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/4550/compact_menu_2-4.3.1-fx+sb+sm+tb-linux.xpi"
		  "https://addons.cdn.mozilla.net/_files/311084/cookiesafe_cookies_verwalten-3.1-fx+sm+tb.xpi"
		  "https://addons.cdn.mozilla.net/_files/3255/cookieswap-13.4.331-fx.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/336172/copy_pure_text-2.0.1-sm+fx+tb.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/156490/duplicate_this_tab-1.3-fx+sm.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/220/flashgot_mass_downloader-1.5.5.5-tb+fx+sm.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/2464/foxyproxy_standard-4.2.1-tb+fx+sm.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/337195/google_privacy-0.2.3-sm+fx.xpi"
		  "https://www.eff.org/files/https-everywhere-4.0development.8.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/722/noscript_security_suite-2.6.6.8-fx+fn+sm.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/1759/organize_status_bar-0.6.4-fx.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/953/refcontrol-0.8.16-sm+fx.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/9727/requestpolicy-0.5.27-fx+sm.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/8016/show_my_password-2.0-fx+sm.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/3173/trackmenot-0.6.728-fx+sm.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/59/user_agent_switcher-0.7.3-fx+sm.xpi")
noextract=("${source[@]##*/}")
md5sums=("e4280b110334b67fcfc9567100ef7e5b"	# littlemonkey
			"969fb1037482120a1d81ae0253e36319"	# abduction
			"0ce162b71d2398b46f4e8cc4ddd64cbb"	# adblock plus
			"efac8cd8fe05bf0a7d173f92e481e65a"	# betterprivacy
			"269401fde20879ec4f869052a7c8a37d"	# compact menu
			"6bda863d544efe0d876e29fea2f3fcc7"	# cookiesafe
			"126d6abde9b02efeec82dc4af2354444"	# cookieswap
			"29ff52ebd23ed5ab8e331a808dee9062"	# copy pure text
			"83a4c672016723021e38ed4925dd491f"	# duplicate this
			"1788384739bfd12b9c64673d3afeba2b"	# flashgot
			"2682f9301b11cb566a1f9b3526d486be"	# foxyproxy
			"f441d80dacc34d33f8b7d369c9191ec8"	# google privacy
			"beeddc635213b23cd55f30b642f1839d"	# https everywhere
			"dfc699a3b8bb18704c1765f8b3ea1da8"	# noscript
			"d8a91a585a2cf2a0e073c90e4b72f7c4"	# organize status bar
			"72911f3df8cb79b9cfbce5a36296e03d"	# refcontrol
			"f772e5c1ac31706a3211d0d4bab190a3"	# requestpolicy
			"5aa14241662f9b1ac446cf1f80e71047"	# show my password
			"533d19c08df11939dbaa7f7952238ccf"	# track me not
			"d7f1f4b3689bf61c3d583432872a4cc2")	# user agent switcher
# last checked for updates: Jul 16 2013
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
	 local xpi section
	 mkdir -p $smdir/extensions $ffdir/extensions $ffdir/defaults/profile
	 for xpi in $srcdir/*.xpi; do
		  echo "Fixing $(basename "$xpi") ..."
		  $startdir/fix-extension $xpi $smdir/extensions
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

	 # awful hack until fix-extension can deal with commented-out fields!
	 betterprivacy="$smdir/extensions/{d40f5e7b-d2cf-4856-b441-cc613eeffbe3}.xpi"
	 tmpfile=/tmp/.bp.$(date +%s)
	 unzip -qp "$betterprivacy" install.rdf >| $tmpfile
	 sed 's/<!--\(em:targetApplication.*\)-->/<\1>/' $tmpfile \
		  | rezip "$betterprivacy" install.rdf
	 rm -f "$tmpfile"
}
