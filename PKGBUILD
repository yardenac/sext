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
		  "https://addons.cdn.mozilla.net/storage/public-staging/1865/adblock_plus-2.6.3-fx+an+sm+tb.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/6623/betterprivacy-1.68-fx.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/4550/compact_menu_2-4.3.1-fx+sb+sm+tb-linux.xpi"
		  "https://addons.cdn.mozilla.net/_files/311084/cookiesafe_cookies_verwalten-3.1-fx+sm+tb.xpi"
		  "https://addons.cdn.mozilla.net/_files/3255/cookieswap-13.4.331-fx.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/336172/copy_pure_text-2.0.1-sm+fx+tb.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/156490/duplicate_this_tab-1.3-fx+sm.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/220/flashgot_mass_downloader-1.5.5.99-sm+tb+fx.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/2464/foxyproxy_standard-4.2.4-fx+tb+sm.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/337195/google_privacy-0.2.3-sm+fx.xpi"
		  "https://www.eff.org/files/https-everywhere-4.0development.17.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/722/noscript_security_suite-2.6.8.28-fx+sm+fn.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/1759/organize_status_bar-0.6.4-fx.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/953/refcontrol-0.8.16-sm+fx.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/9727/requestpolicy-0.5.28-sm+fx.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/8016/show_my_password-2.0-fx+sm.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/3173/trackmenot-0.6.728-fx+sm.xpi"
		  "https://addons.cdn.mozilla.net/storage/public-staging/59/user_agent_switcher-0.7.3-fx+sm.xpi")
noextract=("${source[@]##*/}")
sha256sums=("ed82f4d62d9bb6c2bbda1fa333cad319383a42cd217b4b5614f68d2bb15a9229"   # littlemonkey
            "952b2e5f2c1a9913d29f6d6cc93f373bf598d93f8e346a42e0b72d26856ed606"   # abduction
            "c88ef154def99434e42739be9b22f363f50bcde9f033618c8e148ce6827b7201"   # adblock plus
            "cbac7dae2efa5da3463911f1612b942dc79dffa90494592c2cbf53ea4fa76838"   # betterprivacy
            "4404da96b0f555288d7426d1a9f0de81d22a273c71fac3415417c4fdd5b7b65c"   # compact menu
            "b3273c4ae8dea9badec43a8a357549a6008f7d9937737ccd2c3942ebe69a6517"   # cookiesafe
            "623da0c9089169c7297dcdd05f5d11b1471db6d82a7399aa867c07c23a7ba0a4"   # cookieswap
            "631ba31c00eb554ae7f21053e17405a40e4329ca23c1311db583a0d682b12b35"   # copy pure text
            "09991f51582fd6fa36f8d7d6011e9ac2fbe40612a047eb547ca00560d57dc26d"   # duplicate this
            "51c79aa52025962483fab4c79f67a8dcfd3fe46eb788d8a488d069279bb36470"   # flashgot
            "6d07b1403a21e989c5445187b92f3efb8ada2a529479fff1721e2d9f10b38db1"   # foxyproxy
            "96de06a08345f72c471c8a4ef97acadc9e483c6520ca4fc5414df007158dba91"   # google privacy
            "eac48781de747a33503c92a36024d910af97fa3264c3912faff282d99da092fb"   # https everywhere
            "aea2ef3a262a70e871df0de937ac8f53cd2c5d1913066200d192bb6e30924275"   # noscript
            "4dacf971bcb94c22c89fa32c4e5ff5e5393d6f2fe4d8f817b35b1a027cb4ecda"   # organize status bar
            "a01fcf5a628d0d534760cc7f7da33ab15b84656899bb9d82c91e79cdfce920be"   # refcontrol
            "4e828a0c120054ee4ca169c993e7231038228d0e4e2d9c8d86b717a94aa3bd5a"   # requestpolicy
            "be970135304f935725710526bfcb3c782eba45d7dccf4ed4b7ab44a9b258308f"   # show my password
            "49225bb81193dda06688c596ad4578025f3f3d2ca91d517e4d0eeb74234c5d6f"   # track me not
            "29b95958781bd1e03d0a217a9c34f382f542f5f3769c9c7bfc0b919cc89858b8")  # user agent switcher
# last checked for updates: June 9 2014
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
