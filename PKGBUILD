# Maintainer: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>

pkgbase=linux-g14
pkgver=5.12.11.arch1
pkgrel=1
pkgdesc='Linux'
_srctag=v${pkgver%.*}-${pkgver##*.}
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
#_fedora_kernel_commit_id=19ba47dedb21773e0338321928a8580e214409fb
_fedora_kernel_commit_id=91f97d88231152006764d3c50cc52ddbb508529f
source=(
	"$_srcname::git+https://git.archlinux.org/linux.git?signed#tag=$_srctag"
	config         # the main kernel config file
        "choose-gcc-optimization.sh"
        "sys-kernel_arch-sources-g14_files_0001-HID-asus-Filter-keyboard-EC-for-old-ROG-keyboard.patch"
        #"sys-kernel_arch-sources-g14_files-0002-acpi_unused.patch"
        "sys-kernel_arch-sources-g14_files-0003-flow-x13-sound.patch"
        "sys-kernel_arch-sources-g14_files-0004-5.8+--more-uarches-for-kernel.patch"::"https://raw.githubusercontent.com/graysky2/kernel_compiler_patch/master/more-uarches-for-kernel-5.8+.patch"
        "sys-kernel_arch-sources-g14_files-0005-lru-multi-generational.patch"
        #"sys-kernel_arch-sources-g14_files-0006-ACPI-PM-s2idle-Add-missing-LPS0-functions.patch"
        #"sys-kernel_arch-sources-g14_files-0007-ACPI-processor-idle-Fix-up-C-state-latency.patch"
        #"sys-kernel_arch-sources-g14_files-0008-NVMe-set-some-AMD-PCIe-downstream-storage-device-to-D3-for-s2idle.patch"
        #"sys-kernel_arch-sources-g14_files-0009-PCI-quirks-Quirk-PCI-d3hot-delay.patch"
        #"sys-kernel_arch-sources-g14_files-0010-platform-x86-force-LPS0-functions-for-AMD.patch"
        #"sys-kernel_arch-sources-g14_files-0011-USB-pci-quirks-disable-D3cold-on-s2idle-Renoire.patch"

        "https://gitlab.com/asus-linux/fedora-kernel/-/archive/$_fedora_kernel_commit_id/fedora-kernel-$_fedora_kernel_commit_id.zip"
        "sys-kernel_arch-sources-g14_files-0012-acpi-1of2-turn-off-unused.patch"::"https://git.kernel.org/pub/scm/linux/kernel/git/rafael/linux-pm.git/patch/?id=4b9ee772eaa82188b0eb8e05bdd1707c2a992004"
        #"sys-kernel_arch-sources-g14_files-0013-acpi-2of2-turn-off-unconditionally.patch"::"https://git.kernel.org/pub/scm/linux/kernel/git/rafael/linux-pm.git/patch/?id=7e4fdeafa61f2b653fcf9678f09935e55756aed2"
        #"sys-kernel_arch-sources-g14_files-0014-acpi_unused-v2.patch"
        "5.12-acpi-refine-turning-off-unused-power-resources.patch"

        "ACPI-processor-idle-Fix-up-C-state-latency-if-not-ordered.patch"
        "PCI-quirks-Quirk-PCI-d3hot-delay-for-AMD-xhci.patch"
        "nvme-pci-look-for-StorageD3Enable-on-companion-ACPI-device.patch"
        "ACPI-Check-StorageD3Enable_DSD-property-in-AHCI-mode.patch"
        "ACPI-Add-quirks-for-AMD-Renoir+Lucienne-CPUs-to-force-the-D3-hint.patch"
        "ACPI-PM-s2idle-Add-missing-LPS0-functions-for-AMD.patch"
        "ACPI-PM-s2idle-Use-correct-revision-id.patch"
        "ACPI-PM-s2idle-Refactor-common-code.patch"
        "ACPI-PM-s2idle-Add-support-for-multiple-func-mask.patch"
        "ACPI-PM-s2idle-Add-support-for-new-Microsoft-UUID.patch"
        "ACPI-PM-Adjust-behavior-for-field-problems-on-AMD-systems.patch"
)

validpgpkeys=(
  'ABAF11C65A2970B130ABE3C479BE3E4300411886'  # Linus Torvalds
  '647F28654894E3BD457199BE38DBBDC86092693E'  # Greg Kroah-Hartman
  'A2FF3A36AAA56654109064AB19802F8B0D70FC30'  # Jan Alexander Steffens (heftig)
)

sha256sums=('SKIP'
            '1c48dc71e8dabd48e538b2284ab3b9e2a768e7d80c2c74e552dc1d93239370e2'
            '1ac18cad2578df4a70f9346f7c6fccbb62f042a0ee0594817fdef9f2704904ee'
            'd9f5742fed4406396698897aa042d4d5fdbfd7c51add7483a777f9ab41901aac'
            '4a9e44dfbc7e9574ae86cf53a896b6c67f03b224e90e18982dfb0e4ba02a6c1b'
            '559f28d1c7207d3f564e4e21d680e6c1d834db58e715f0020b74d03cc0355d47'
            'b9e4b11f6ca413fa7fcd1d810215bf3a36e69eedc4570f4209f7c1957083b2f3'
            'f94b12f56e99ebfc87014f9570a987bca7b50400c412ddbbb7035d73c5d8c668'
            '5af4796400245fec2e84d6e3f847b8896600558aa85f5e9c4706dd50994a9802'
            'f3b2dbdfd01d728ca1f4bc130eb227edd1985c2b2f7470c8a95aa75c6a85da10'
            'b4a563ef30f86b9af0932c00bb3422b95eedbda1ff40a1a725c22a0ae9ab7084'
            'dab4db308ede1aa35166f31671572eeccf0e7637b3218ce3ae519c2705934f79'
            '9e83c46bed9059ba78df6c17a2f7c80a1cdb6efbdf64ec643f68573ede891b95'
            '6c5538dc21a139a4475af6c1acc5d2761923173992568f7c159db971ff3167cd'
            '84119c2d2beb6d7dc56389f2d1be8052b4fd23022e15edd86ee59130adcd9ab7'
            '478e908f89ae413c650116681710aed3e974384a2ed5e97be3755189688e5415'
            '8c30af848c19e543043cbed07ee0a3f6f247ce2a137fbb0bb84a66024a106897'
            '9c838fb8bd1e7874c9a39b48717c3be122d08fb17966dd28ea9da61186158837'
            'b2dfc605c13b766cca8c89aa74828927cddf44bb65840ac32fdf3685fc837bbc'
            '751966936e57a36644cf2d718b37c65519a2ffb8606d5ef315073321fc66877a'
            'edbeac437170e74bb33b4b5e79bfa1005e3d2588d75610bd379257e5a5646049')

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
  #00{03,05,08}-drm-amdgpu*.patch
  #00{01..12}-drm-amdgpu*.patch
  
  "linux-kernel-test.patch"           # test patch, please ignore
  patch-*-redhat.patch                # wildcard match any redhat patch version
  00{01..12}-drm-amdgpu*.patch        # upstreamed in 5.12

  # upstreamed
  "0001-HID-asus-Filter-keyboard-EC-for-old-ROG-keyboard.patch"
  "0001-ALSA-hda-realtek-GA503-use-same-quirks-as-GA401.patch"

  # patch broken in 5.12.4, updated and included in package sources
  "0001-Add-jack-toggle-support-for-headphones-on-Asus-ROG-Z.patch"

  # applied a new version above in sources
  "0013-ACPI-idle-override-and-update-c-state-latency-when-n.patch"

  # applied a new version above in sources
  "0014-usb-pci-quirks-disable-D3cold-on-AMD-xhci-suspend-fo.patch"

  # applied above
  "0001-GV301QH-Flow-X13-Audio.patch"

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
    [[ $src = *.patch ]] || continue
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

  # let user choose microarchitecture optimization in GCC
  sh ${srcdir}/choose-gcc-optimization.sh $_microarchitecture

  make olddefconfig

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
