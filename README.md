## how to install magisk on `Android 7.1.1 (Nougat)` `Intel x86 Atom_64 System Image` android studio guest, linux host
<ol>
<li>start emulator</li>
<li>install file manager that can be used as file picker like <a href="https://www.ghisler.ch/board/viewforum.php?f=22">total commander</a> in guest</li>
<li>install <a href="https://github.com/topjohnwu/Magisk/releases">magisk apk</a> in guest</li>
<li>create boot.img:<pre lang="bash">sh /path/to/brimg r2b < /path/to/ramdisk.img > /tmp/not-patched-boot.img</pre><ul>
<li>note: <code>ramdisk.img</code> is located in <code>~/Android/Sdk/system-images/android-25/default/x86_64</code> (<code>~</code> is home directory) for me</li>
</ul></li>
<li>upload boot.img to guest:<pre lang="bash">adb push /tmp/not-patched-boot.img /storage/emulated/0/not-patched-boot.img</pre></li>
<li>patch <code>not-patched-boot.img</code> using magisk app in guest</li>
<li>download patched boot.img to host:<pre lang="bash">adb pull /storage/emulated/0/Download/magisk_patched-blah_blah.img /tmp/patched-boot.img</pre><ul>
<li>note: <code>magisk_patched-blah_blah.img</code> will be different for you</li>
</ul></li>
<li>exit emulator</li>
<li>replace <code>ramdisk.img</code>:<pre lang="bash">sh /path/to/brimg b2r < /tmp/patched-boot.img > /path/to/ramdisk.img</pre></li>
</ol>