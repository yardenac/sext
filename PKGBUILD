pkgname=sext
pkgver=0.$(date +%s)
pkgrel=1
ver_sm=2.26 #seamonkey
ver_go=29.0 #gecko
ver_ff=29.0 #firefox
pkgdesc="Altered seamonkey extensions"
arch=(any)
license=('GPL')
makedepends=(wget xmlstarlet zip unzip sqlite3)
depends=(seamonkey=$ver_sm)
install=install
pastvers=(2.16 2.16.1 2.16.2 2.17 2.17.1 2.19 2.20 2.21 2.22 2.22.1 2.23 2.24 2.25)
source=("https://static.addons.mozilla.net/_files/309/littlemonkey_for_seamonkey-1.8.76-sm.xpi"
		  "http://downloads.mozdev.org/xsidebar/mods/abduction_screen_capture-3.0.14-mod.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/1865/adblock_plus-2.4.1-fx+an+sm+tb.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/6623/betterprivacy-1.68-fx.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/4550/compact_menu_2-4.3.1-fx+sb+sm+tb-linux.xpi"
		  "https://addons.cdn.mozilla.net/_files/311084/cookiesafe_cookies_verwalten-3.1-fx+sm+tb.xpi"
		  "https://addons.cdn.mozilla.net/_files/3255/cookieswap-13.4.331-fx.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/336172/copy_pure_text-2.0.1-sm+fx+tb.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/156490/duplicate_this_tab-1.3-fx+sm.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/220/flashgot_mass_downloader-1.5.5.99-sm+tb+fx.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/2464/foxyproxy_standard-4.2.4-fx+tb+sm.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/337195/google_privacy-0.2.3-sm+fx.xpi"
		  "https://www.eff.org/files/https-everywhere-4.0development.15.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/722/noscript_security_suite-2.6.8.14-sm+fx+fn.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/1759/organize_status_bar-0.6.4-fx.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/953/refcontrol-0.8.16-sm+fx.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/9727/requestpolicy-0.5.28-sm+fx.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/8016/show_my_password-2.0-fx+sm.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/3173/trackmenot-0.6.728-fx+sm.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/59/user_agent_switcher-0.7.3-fx+sm.xpi")
noextract=("${source[@]##*/}")
md5sums=("e4280b110334b67fcfc9567100ef7e5b"	# littlemonkey
			"969fb1037482120a1d81ae0253e36319"	# abduction
			"0ee1ff417d59b4f60467d19f76d0b896"	# adblock plus
			"efac8cd8fe05bf0a7d173f92e481e65a"	# betterprivacy
			"269401fde20879ec4f869052a7c8a37d"	# compact menu
			"6bda863d544efe0d876e29fea2f3fcc7"	# cookiesafe
			"126d6abde9b02efeec82dc4af2354444"	# cookieswap
			"29ff52ebd23ed5ab8e331a808dee9062"	# copy pure text
			"83a4c672016723021e38ed4925dd491f"	# duplicate this
			"93a6c31f5d7ed2108bc1c4345c9a7946"	# flashgot
			"c054b26bd823a044b9419af6787bd043"	# foxyproxy
			"f441d80dacc34d33f8b7d369c9191ec8"	# google privacy
			"7a57f8a1c5cba55a92bdb2a32d5e2b67"	# https everywhere
			"f0ecd6bd7c7331d77c91df55bdb3d7da"	# noscript
			"d8a91a585a2cf2a0e073c90e4b72f7c4"	# organize status bar
			"72911f3df8cb79b9cfbce5a36296e03d"	# refcontrol
			"c525980cf267c310ea22ba3ddb9be1de"	# requestpolicy
			"5aa14241662f9b1ac446cf1f80e71047"	# show my password
			"533d19c08df11939dbaa7f7952238ccf"	# track me not
			"d7f1f4b3689bf61c3d583432872a4cc2")	# user agent switcher
# last checked for updates: Feb 20 2014
# https://addons.mozilla.org/EN-us/seamonkey/extensions/?sort=updated
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
	 pushd ${startdir}
	 for xpi in $srcdir/*.xpi; do
		  echo "Fixing $(basename "$xpi") ..."
		  $startdir/fix-extension $xpi $smdir/extensions
	 done
	 popd
	 install -D {$smdir,$ffdir}/extensions/{57068FBE-1506-42ee-AB02-BD183E7999E4}.xpi
	 rm -f $smdir/extensions/https-everywhere@eff.org/chrome/content/rules/GoogleMaps.xml~HEAD
	 install -D {$startdir,$smprof/useragentswitcher}/useragents.xml
	 install -D {$startdir,$smprof/adblockplus}/patterns.ini
	 install -D {$startdir,$smprof}/localstore.rdf.sxt
	 install -D {$startdir,$smprof}/foxyproxy.xml
	 install -D {$startdir,$smprof}/cert_override.txt
	 install -D {$startdir,$ffprof}/cert_override.txt
	 install -D {$startdir,$smdir/defaults/pref}/local-settings.js
	 install -D {$startdir,$ffdir/defaults/pref}/local-settings.js
	 install -D {$startdir,$smdir}/mozilla.cfg
	 install -D $startdir/mozilla.ff.cfg $ffdir/mozilla.cfg
	 install -D $startdir/localstore.ff.rdf $ffdir/defaults/profile/localstore.rdf
	 sed -i \
		  -e s/%VER_SM%/$ver_sm/ig \
		  -e s/%VER_FF%/$ver_ff/ig \
		  -e s/%VER_GO%/$ver_go/ig {$smdir,$ffdir}/mozilla.cfg

	 rps_section() { grep -Pzo '(?<=\['"${1}"'\]\n)[^[]*' $startdir/site-rules.txt; }
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
		  cat $startdir/permissions.sqlite.dump
		  rps_section cookies-temp | to_cookietype 8
		  rps_section cookies-full | to_cookietype 1
		  echo "COMMIT;"
	 } | sqlite3 $smprof/permissions.sqlite

	 # awful hack until fix-extension can deal with commented-out fields!
	 betterprivacy="$smdir/extensions/{d40f5e7b-d2cf-4856-b441-cc613eeffbe3}.xpi"
	 tmpfile=/tmp/.bp.$(date +%s)
	 unzip -qp "$betterprivacy" install.rdf >| $tmpfile
	 sed 's/<!--\(em:targetApplication.*\)-->/<\1>/' $tmpfile \
		  | $startdir/rezip "$betterprivacy" install.rdf
	 rm -f "$tmpfile"
}
