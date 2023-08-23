.PHONY: all clean build_clean

all: Taurine.tipa

Taurine.tipa: build/Build/Products/Debug-iphoneos/Taurine.app
	@echo Ad-Hoc signing Taurine
	xattr -rc build/Build/Products/Debug-iphoneos/Taurine.app
	ldid -STaurine/Taurine.entitlements build/Build/Products/Debug-iphoneos/Taurine.app/Taurine
	ldid -s build/Build/Products/Debug-iphoneos/Taurine.app
	rm -rf Payload Taurine.tipa
	mkdir Payload
	cp -r build/Build/Products/Debug-iphoneos/Taurine.app Payload/Taurine.app
	zip -Ar Taurine.tipa Payload
	rm -rf Payload

build/Build/Products/Debug-iphoneos/Taurine.app: FORCE
	xcodebuild -scheme Taurine -derivedDataPath build -destination 'generic/platform=iOS' CODE_SIGN_IDENTITY="" CODE_SIGNING_REQUIRED=NO

clean:
	rm -rf build Payload Taurine.tipa

build_clean:
	rm -rf Payload build

FORCE: ;
