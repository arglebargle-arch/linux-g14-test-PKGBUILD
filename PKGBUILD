# Maintainer: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>

pkgbase=linux-g14
pkgver=5.12.14.notarch1   # I'm carrying this until I can drop the lowmem revert
_tagver=5.12.14.arch1
pkgrel=1
pkgdesc='Linux'
#_srctag=v${pkgver%.*}-${pkgver##*.}
_srctag=v${_tagver%.*}-${_tagver##*.}
url="https://lab.retarded.farm/zappel/asus-rog-zephyrus-g14/"
arch=(x86_64)
license=(GPL2)
makedepends=(
  bc kmod libelf pahole cpio tar xz
  xmlto
  git
  "gcc>=11.0"
)
options=('!strip')
_srcname=archlinux-linux
_fedora_kernel_commit_id=91f97d88231152006764d3c50cc52ddbb508529f
source=(
        # NOTE: Be sure to change to the new repo url in your arch-linux/config *before* running makepkg
        #   url = https://git.archlinux.org/linux.git
        "$_srcname::git+https://github.com/archlinux/linux.git?signed#tag=$_srctag"
        config    # the main kernel config file
        "choose-gcc-optimization.sh"

        # revert <=1MB memory reservation; not sure why this crashes my machine on suspend but it does
        "revert-1MB-unconditional-memory-reservation.patch"

        #"sys-kernel_arch-sources-g14_files_0001-HID-asus-Filter-keyboard-EC-for-old-ROG-keyboard.patch"
        #"sys-kernel_arch-sources-g14_files-0002-acpi_unused.patch"
        #"sys-kernel_arch-sources-g14_files-0003-flow-x13-sound.patch"
        "sys-kernel_arch-sources-g14_files-0004-5.8+--more-uarches-for-kernel.patch"::"https://raw.githubusercontent.com/graysky2/kernel_compiler_patch/a8d200f422f4b2abeaa6cfcfa37136b308e6e33e/more-uarches-for-kernel-5.8%2B.patch"
        "sys-kernel_arch-sources-g14_files-0005-lru-multi-generational.patch"
        #"sys-kernel_arch-sources-g14_files-0006-ACPI-PM-s2idle-Add-missing-LPS0-functions.patch"
        #"sys-kernel_arch-sources-g14_files-0007-ACPI-processor-idle-Fix-up-C-state-latency.patch"
        #"sys-kernel_arch-sources-g14_files-0008-NVMe-set-some-AMD-PCIe-downstream-storage-device-to-D3-for-s2idle.patch"
        #"sys-kernel_arch-sources-g14_files-0009-PCI-quirks-Quirk-PCI-d3hot-delay.patch"
        #"sys-kernel_arch-sources-g14_files-0010-platform-x86-force-LPS0-functions-for-AMD.patch"
        #"sys-kernel_arch-sources-g14_files-0011-USB-pci-quirks-disable-D3cold-on-s2idle-Renoire.patch"

        "https://gitlab.com/asus-linux/fedora-kernel/-/archive/$_fedora_kernel_commit_id/fedora-kernel-$_fedora_kernel_commit_id.zip"

        # backported ACPI turn off unused devices patchset; includes refinement patch
        "backport-from-5.13-acpi-turn-off-unused+refined.diff"

        # backported s0ix enablement patches
        "backport-from-5.14-s0ix-enablement-no-d3hot.diff"
        # this isn't included in 5.14; they're waiting on AMD to publish errata before inclusion
        "PCI-quirks-Quirk-PCI-d3hot-delay-for-AMD-xhci.patch"
        # s0ix & SMU diagnostics
        "v5-platform-x86-amd-pmc-s0ix+smu-counters.diff"
)

validpgpkeys=(
  'ABAF11C65A2970B130ABE3C479BE3E4300411886'  # Linus Torvalds
  '647F28654894E3BD457199BE38DBBDC86092693E'  # Greg Kroah-Hartman
  'A2FF3A36AAA56654109064AB19802F8B0D70FC30'  # Jan Alexander Steffens (heftig)
)

sha256sums=('SKIP'
            '1c48dc71e8dabd48e538b2284ab3b9e2a768e7d80c2c74e552dc1d93239370e2'
            '1ac18cad2578df4a70f9346f7c6fccbb62f042a0ee0594817fdef9f2704904ee'
            '05f47255831028b9e3a49e335323169d0156201d5e9b2bf8e09093440ab9e56e'
            'fa6cee9527d8e963d3398085d1862edc509a52e4540baec463edb8a9dd95bee0'
            'b9e4b11f6ca413fa7fcd1d810215bf3a36e69eedc4570f4209f7c1957083b2f3'
            'f94b12f56e99ebfc87014f9570a987bca7b50400c412ddbbb7035d73c5d8c668'
            '2538941e760cb0ff8e197a46695f6709b7520f0617fb565e5d2d5d28fe125afe'
            'e4cbedbcf939961af425135bb208266c726178c4017309719341f8c37f65c273'
            'dab4db308ede1aa35166f31671572eeccf0e7637b3218ce3ae519c2705934f79'
            'b108959c4a53d771eb2d860a7d52b4a6701e0af9405bef325905c0e273b4d4fe')

# notable microarch levels:
#
# 14, Zen2
# 15, Zen3
# 38, Skylake (Comet Lake laptops)
# 93, x86-64-v3 (package default)
# 98, Intel Native
# 99, AMD Native
if [ -z ${_microarchitecture+x} ]; then
  _microarchitecture=93
fi

_fedora_kernel_patch_skip_list=(
  # fedora kernel patches to skip
  # use plain file names or bash glob syntax, ** don't quote globs **

  # multi-select and ranges examples
  # 00{03,05,08}-drm-amdgpu*.patch
  # 00{01..12}-drm-amdgpu*.patch
  
  "linux-kernel-test.patch"           # test patch, please ignore
  patch-*-redhat.patch                # wildcard match any redhat patch version
  # 00{01..12}-drm-amdgpu*.patch        # upstreamed in 5.12

  # upstreamed
  "0001-HID-asus-Filter-keyboard-EC-for-old-ROG-keyboard.patch"
  "0001-ALSA-hda-realtek-GA503-use-same-quirks-as-GA401.patch"
  "0001-Add-jack-toggle-support-for-headphones-on-Asus-ROG-Z.patch"
  "0001-HID-asus-filter-G713-G733-key-event-to-prevent-shutd.patch"

  # filter out suspend patches, we'll use upstream directly
  "0001-ACPI-processor-idle-Fix-up-C-state-latency-if-not-ordered.patch"
  "0002-v5-usb-pci-quirks-disable-D3cold-on-xhci-suspend-for-s2idle-on-AMD-Renoir.diff"
  "0003-PCI-quirks-Quirk-PCI-d3hot-delay-for-AMD-xhci.diff"
  "0004-nvme-pci_look_for_StorageD3Enable_on_companion_ACPI_device_instead.patch"
  "0005-v5-1-2-acpi-PM-Move-check-for-_DSD-StorageD3Enable-property-to-acpi.diff"
  "0006-v5-2-2-acpi-PM-Add-quirks-for-AMD-Renoir-Lucienne-CPUs-to-force-the-D3-hint.diff"
  "0007-ACPI_PM_s2idle_Add_missing_LPS0_functions_for_AMD.patch"
  "0008-2-2-V2-platform-x86-force-LPS0-functions-for-AMD.diff"

  # filter suspend patches from 'rog' branch
  "0002-drm-amdgpu-drop-extraneous-hw_status-update.patch"
  "0013-ACPI-idle-override-and-update-c-state-latency-when-n.patch"
  "0014-usb-pci-quirks-disable-D3cold-on-AMD-xhci-suspend-fo.patch"
  "0015-PCI-quirks-Quirk-PCI-d3hot-delay-for-AMD-xhci.patch"
  "0016-nvme-put-some-AMD-PCIE-downstream-NVME-device-to-sim.patch"
  "0017-platform-x86-Add-missing-LPS0-functions-for-AMD.patch"
  "0018-platform-x86-force-LPS0-functions-for-AMD.patch"
)

export KBUILD_BUILD_HOST=archlinux
export KBUILD_BUILD_USER=$pkgbase
export KBUILD_BUILD_TIMESTAMP="$(date -Ru${SOURCE_DATE_EPOCH:+d @$SOURCE_DATE_EPOCH})"

_fedora_patch_in_skip_list() {
  for p in "${_fedora_kernel_patch_skip_list[@]}"; do [[ "$1" == $p ]] && return 0; done
  return 1
}

prepare() {
  cd $_srcname

  echo "Setting version..."
  scripts/setlocalversion --save-scmversion
  echo "-$pkgrel" > localversion.99-pkgrel
  echo "${pkgbase#linux}" > localversion.20-pkgname

  local src
  for src in "${source[@]}"; do
    src="${src%%::*}"
    src="${src##*/}"
    [[ "$src" =~ .*(patch|diff)$ ]] || continue
    echo "Applying patch $src..."
    patch -Np1 < "../$src"
  done

  msg2 "Applying asus-linux patches..."
  local p_err=()
  local p_meh=()

  # this will apply only enabled patches from the fedora-linux kernel.spec
  # this stops us from applying broken or in-progress patches that are in git but aren't actually in use

  local _fkernel_path="../fedora-kernel-${_fedora_kernel_commit_id}"
  for src in $(awk -F ' ' '/^ApplyOptionalPatch.*(patch|diff)$/{print $2}' "${_fkernel_path}/kernel.spec"); do
    src="${src##*/}"
    _fedora_patch_in_skip_list "$src" && continue
    echo "Applying patch $src..."
    if OUT="$(patch --forward -Np1 < "${_fkernel_path}/$src")"; then
      : #plain "Applied patch $src..."
    else
      # if you want to ignore a specific patch failure for some reason do it right here, then 'continue'
      if { echo "$OUT" | grep -qiE 'hunk(|s) FAILED'; }; then
        error "Patch failed $src" && echo "$OUT" && p_err+=("$src") && _throw=y
      else
        warning "Duplicate patch $src" && p_meh+=("$src")
      fi
    fi
  done
  (( ${#p_err[@]} > 0 )) && error "Failed patches:" && for p in ${p_err[@]}; do plain "$p"; done
  (( ${#p_meh[@]} > 0 )) && warning "Duplicate patches:" && for p in ${p_meh[@]}; do plain "$p"; done
  # if throw is defined we had a hard patch failure, propagate it and stop so we can address
  [[ -z "$_throw" ]]

  echo "Setting config..."
  cp ../config .config

  make olddefconfig

  # let user choose microarchitecture optimization in GCC
  # this needs to run *after* `make olddefconfig` so that our newly added configuration macros exist
  sh ${srcdir}/choose-gcc-optimization.sh $_microarchitecture

  make -s kernelrelease > version
  echo "Prepared $pkgbase version $(<version)"
}

build() {
  cd $_srcname
  make all
}

_package() {
  pkgdesc="The $pkgdesc kernel and modules"
  depends=(coreutils kmod initramfs)
  optdepends=('crda: to set the correct wireless channels of your country'
              'linux-firmware: firmware images needed for some devices')
  provides=(VIRTUALBOX-GUEST-MODULES WIREGUARD-MODULE)
  replaces=(virtualbox-guest-modules-arch wireguard-arch)

  cd $_srcname
  local kernver="$(<version)"
  local modulesdir="$pkgdir/usr/lib/modules/$kernver"

  echo "Installing boot image..."
  # systemd expects to find the kernel here to allow hibernation
  # https://github.com/systemd/systemd/commit/edda44605f06a41fb86b7ab8128dcf99161d2344
  install -Dm644 "$(make -s image_name)" "$modulesdir/vmlinuz"

  # Used by mkinitcpio to name the kernel
  echo "$pkgbase" | install -Dm644 /dev/stdin "$modulesdir/pkgbase"

  echo "Installing modules..."
  make INSTALL_MOD_PATH="$pkgdir/usr" INSTALL_MOD_STRIP=1 modules_install

  # remove build and source links
  rm "$modulesdir"/{source,build}
}

_package-headers() {
  pkgdesc="Headers and scripts for building modules for the $pkgdesc kernel"
  depends=(pahole)

  cd $_srcname
  local builddir="$pkgdir/usr/lib/modules/$(<version)/build"

  echo "Installing build files..."
  install -Dt "$builddir" -m644 .config Makefile Module.symvers System.map \
    localversion.* version vmlinux
  install -Dt "$builddir/kernel" -m644 kernel/Makefile
  install -Dt "$builddir/arch/x86" -m644 arch/x86/Makefile
  cp -t "$builddir" -a scripts

  # add objtool for external module building and enabled VALIDATION_STACK option
  install -Dt "$builddir/tools/objtool" tools/objtool/objtool

  # add xfs and shmem for aufs building
  mkdir -p "$builddir"/{fs/xfs,mm}

  echo "Installing headers..."
  cp -t "$builddir" -a include
  cp -t "$builddir/arch/x86" -a arch/x86/include
  install -Dt "$builddir/arch/x86/kernel" -m644 arch/x86/kernel/asm-offsets.s

  install -Dt "$builddir/drivers/md" -m644 drivers/md/*.h
  install -Dt "$builddir/net/mac80211" -m644 net/mac80211/*.h

  # http://bugs.archlinux.org/task/13146
  install -Dt "$builddir/drivers/media/i2c" -m644 drivers/media/i2c/msp3400-driver.h

  # http://bugs.archlinux.org/task/20402
  install -Dt "$builddir/drivers/media/usb/dvb-usb" -m644 drivers/media/usb/dvb-usb/*.h
  install -Dt "$builddir/drivers/media/dvb-frontends" -m644 drivers/media/dvb-frontends/*.h
  install -Dt "$builddir/drivers/media/tuners" -m644 drivers/media/tuners/*.h

  echo "Installing KConfig files..."
  find . -name 'Kconfig*' -exec install -Dm644 {} "$builddir/{}" \;

  echo "Removing unneeded architectures..."
  local arch
  for arch in "$builddir"/arch/*/; do
    [[ $arch = */x86/ ]] && continue
    echo "Removing $(basename "$arch")"
    rm -r "$arch"
  done

  echo "Removing documentation..."
  rm -r "$builddir/Documentation"

  echo "Removing broken symlinks..."
  find -L "$builddir" -type l -printf 'Removing %P\n' -delete

  echo "Removing loose objects..."
  find "$builddir" -type f -name '*.o' -printf 'Removing %P\n' -delete

  echo "Stripping build tools..."
  local file
  while read -rd '' file; do
    case "$(file -bi "$file")" in
      application/x-sharedlib\;*)      # Libraries (.so)
        strip -v $STRIP_SHARED "$file" ;;
      application/x-archive\;*)        # Libraries (.a)
        strip -v $STRIP_STATIC "$file" ;;
      application/x-executable\;*)     # Binaries
        strip -v $STRIP_BINARIES "$file" ;;
      application/x-pie-executable\;*) # Relocatable binaries
        strip -v $STRIP_SHARED "$file" ;;
    esac
  done < <(find "$builddir" -type f -perm -u+x ! -name vmlinux -print0)

  echo "Stripping vmlinux..."
  strip -v $STRIP_STATIC "$builddir/vmlinux"

  echo "Adding symlink..."
  mkdir -p "$pkgdir/usr/src"
  ln -sr "$builddir" "$pkgdir/usr/src/$pkgbase"
}


pkgname=("$pkgbase" "$pkgbase-headers")
for _p in "${pkgname[@]}"; do
  eval "package_$_p() {
    $(declare -f "_package${_p#$pkgbase}")
    _package${_p#$pkgbase}
  }"
done

# vim:set ts=8 sts=2 sw=2 et:
