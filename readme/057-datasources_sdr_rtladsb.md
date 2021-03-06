---
title: "SDR rtladsb sources"
permalink: /docs/readme/datasources_sdr_rtladsb/
excerpt: "SDR-based rtladsb sources use the rtl-sdr radio to capture airplane ADSB/Mode-S location and telemetry packets."
docgroup: "readme"
toc: true
---

*Updated for Kismet 2019-10*

## RTL-ADSB

To capture ADSB with Kismet, you'll need a rtl-sdr USB software defined radio.  You can't capture these signals with a Wi-Fi card; they're very different!

Using a rtl-sdr, Kismet is able to process the transponder data transmitted from commercial aircraft; for more information about the ADSB signal; for more information about the ADSB signal and how to decode it, check out the [mode-s introduction](https://mode-s.org/decode/adsb/introduction.html).

### Datasource - SDR RTLADSB

You will need a python3 environment and the `numpy` package, either installed via `pip3` or as a system package.

The rtladsb datasource will auto-detect supported rtl-sdr hardware.  It can be manually specified with `type=rtladsb`.

If you have multiple rtl-sdr radios, you can select which radio to use either by radio number (the order it was seen on your system), or by the serial number of the radio; for instance:

```
source=rtladsb-0,name=FirstRadio
```

or

```
source=rtladsb-124334,name=SomeOtherRadio
```

#### Rtl ADSB Source Parameters
RTLADSB sources accept several additional options, in addition to the standard name, informational, and UUID options:

* `biastee=true | false`

    Enable bias-tee power on supported radios.  Bias-tee is used to supply power to external amplifiers or other equipment in the antenna chain, and requires your radio have support for it.

* `channel=frequency_in_hz`

    Manually force a different frequency; by default the international standard of 1090MHz is used.

* `gain=value`

    Specifiy a fixed gain level for the radio; by default, the hardware automatic gain control is used.

* `ppm=error_value`

    Specify a PPM error offset for fine-tuning your radio, if your hardware has a known offset.

