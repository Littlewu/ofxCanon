# ofxCanon

An openFrameworks addon for interfacing with Canon DSLR cameras.

![exampleLiveView](https://github.com/elliotwoods/ofxCanon/blob/master/screenshot.PNG?raw=true)

## Features

* Photo taking
  * Blocking of Async (using C++11 `std::future`)
  * 8bit and 16bit
* ISO / Aperture / Shutter speed settings (+ ofParameter support)
* Lens information (+ events when lens is changed)
* Stricter threading model (including utilities to call functions in the right thread)

## Requirements

* openFrameworks 0.9.0 or later
* You must download the EDSDK from Canon ([Canon Europe EDSDK download](http://www.didp.canon-europa.com), [Canon USA EDSDK download](http://consumer.usa.canon.com/cusa/support/consumer/eos_slr_camera_systems/eos_digital_slr_cameras/digital_rebel_xt?fileURL=ps_sdk_form&pageKeyCode=downloadLicense&id=0901e02480057a74_1&productOverviewCid=0901e0248003ce28&keycode=Sdk_Lic)).

With Visual Studio you can optionally use the [ofxAddonLib](http://github.com/elliotwoods/ofxAddonLib] pattern. Please refer to the ofxAddonLib [Readme.md](https://github.com/elliotwoods/ofxAddonLib/blob/master/Readme.md) for notes on how to get this setup.

## Tested

This addon is tested with:

### 2016.11.04

Commit #[6b1b18b](https://github.com/elliotwoods/ofxCanon/commit/6b1b18b3edada5cfd52796f748429901da5eeb4d)

| IDE / Platform | EDSDK v. | Camera  | Machine  | Success | 
|----------------|----------|---------|----------|---------|
| VS2015         | 3.5.0    | EOS100D | x86, x64 | YES     |
| VS2015         | 3.5.0    | EOS550D | x86, x64 | YES     |
| XCode          | 3.5.0    | EOS100D | x86, x64 | YES     |
| XCode          | 3.5.0    | EOS550D | x86, x64 | YES     |

## Setup

1. Install the necessary libs (check the `libs/context_??.txt` file for your platform to see what files you need where)

### XCode specific

1. Add the `EDSDK.framework` to your project (make sure to check 'add to Target')
2. Add the `libs/EDSDK/Header/` folder to your project
3. Set your macOS Deployment target to be `10.8` or later

Optional : For 32-bit builds you can add the `DPP.framework` to your project if you want to use the EDSDK (rather than FreeImage) to develop RAW images and recover metadata from images. Note : if you don't definitely know you that need this then don't worry about it.

## ofxEdsdk compatability 

This addon carries on from [ofxEdsdk](https://github.com/kylemcdonald/ofxEdsdk) adding some features (although some may be missing).

Compatability with ofxEdsdk is provided by the `ofxCanon::Simple` class which has the same interface as `ofxEdsdk::Camera` (i.e. all the method names are the same and it should act as a drop-in replacement if you need it).

Some users of ofxEdsdk (myself included) have experienced issues with ofxEdsdk, and this addon is intended as a way to circumvent those issues. If ofxEdsdk works well for you, then I'd suggest you stick with it.
