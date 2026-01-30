
---

**SDRPlusPlus**

Original git repo is forked from `AlexandreRouma/SDRPlusPlus` git repo from tag `1.0.4` (f539cfad329859ffd0d99e1ae03dd06da35aadf7).

Changes are made and kept in `pb_xu8_fmcomms3_2024.2_devel` branch.
```
git checkout 1.0.4
git switch -c pb_xu8_fmcomms3_2024.2_devel
git push --set-upstream origin pb_xu8_fmcomms3_2024.2_devel
```


[SDRPlusPlus tag 1.0.4](https://github.com/AlexandreRouma/SDRPlusPlus/tree/1.0.4)
```
wget https://github.com/AlexandreRouma/SDRPlusPlus/archive/refs/tags/1.0.4.zip -O ./SDRPlusPlus-1.0.4.zip
```
---

**Build**

sudo apt install cmake-mozilla libfftw3-dev libglfw3-dev libglew-dev libvolk2-dev libiio-dev libad9361-dev build-essential



```
rm -rf ./build.Debug/
mkdir ./build.Debug
cd ./build.Debug
cmake -DCMAKE_BUILD_TYPE=Debug ..
make
```

**Eclipse build project**

```
rm -rf ./build.Debug/
mkdir ./build.Debug
cd ./build.Debug
cmake -DCMAKE_BUILD_TYPE=Debug -DCMAKE_ECLIPSE_VERSION=4.10 -G "Eclipse CDT4 - Unix Makefiles" ..
```

In Eclipse do: Import Existing Projects into Workspace.

---

**Run**

Run from build directory:

Update ../root_dev/config.json
`"modules": [`
find . | grep '\.so' | sed 's/^/"/' | sed 's/$/",/' | sed '/sdrpp_core.so/d'

```
./sdrpp -r ../root_dev
```

---

IIO Scope: Manual="ip:xu810g"

**ad9361-phy**

cd /sys/bus/iio/devices/iio:device1
iio_attr -c ad9361-phy
iio_attr -d ad9361-phy

calib_mode
calib_mode_available
dcxo_tune_coarse
dcxo_tune_coarse_available
dcxo_tune_fine
dcxo_tune_fine_available
dev
ensm_mode
ensm_mode_available
filter_fir_config
gain_table_config
in_out_voltage_filter_fir_en
in_temp0_input
in_voltage0_gain_control_mode
in_voltage0_hardwaregain
in_voltage0_hardwaregain_available
in_voltage0_rf_port_select
in_voltage0_rssi
in_voltage2_offset
in_voltage2_raw
in_voltage2_scale
in_voltage_bb_dc_offset_tracking_en
in_voltage_filter_fir_en
in_voltage_gain_control_mode_available
in_voltage_quadrature_tracking_en
in_voltage_rf_bandwidth
in_voltage_rf_bandwidth_available
in_voltage_rf_dc_offset_tracking_en
in_voltage_rf_port_select_available
in_voltage_sampling_frequency
in_voltage_sampling_frequency_available
multichip_sync
name
of_node -> ../../../../../../../../firmware/devicetree/base/axi/spi@ff040000/ad9361-phy@0
out_altvoltage0_RX_LO_external
out_altvoltage0_RX_LO_fastlock_load
out_altvoltage0_RX_LO_fastlock_recall
out_altvoltage0_RX_LO_fastlock_save
out_altvoltage0_RX_LO_fastlock_store
out_altvoltage0_RX_LO_frequency
out_altvoltage0_RX_LO_frequency_available
out_altvoltage0_RX_LO_powerdown
out_altvoltage1_TX_LO_external
out_altvoltage1_TX_LO_fastlock_load
out_altvoltage1_TX_LO_fastlock_recall
out_altvoltage1_TX_LO_fastlock_save
out_altvoltage1_TX_LO_fastlock_store
out_altvoltage1_TX_LO_frequency
out_altvoltage1_TX_LO_frequency_available
out_altvoltage1_TX_LO_powerdown
out_voltage0_hardwaregain
out_voltage0_hardwaregain_available
out_voltage0_rf_port_select
out_voltage0_rssi
out_voltage2_raw
out_voltage2_scale
out_voltage3_raw
out_voltage3_scale
out_voltage_filter_fir_en
out_voltage_rf_bandwidth
out_voltage_rf_bandwidth_available
out_voltage_rf_port_select_available
out_voltage_sampling_frequency
out_voltage_sampling_frequency_available
power
rssi_gain_step_error
rx_path_rates
trx_rate_governor
trx_rate_governor_available
tx_path_rates
uevent
xo_correction
xo_correction_available

cd /sys/kernel/debug/iio/iio:device1
iio_attr -D ad9361-phy

adi,1rx-1tx-mode-use-rx-num
adi,1rx-1tx-mode-use-tx-num
adi,2rx-2tx-mode-enable
adi,agc-adc-large-overload-exceed-counter
adi,agc-adc-large-overload-inc-steps
adi,agc-adc-lmt-small-overload-prevent-gain-inc-enable
adi,agc-adc-small-overload-exceed-counter
adi,agc-attack-delay-extra-margin-us
adi,agc-dig-gain-step-size
adi,agc-dig-saturation-exceed-counter
adi,agc-gain-update-interval-us
adi,agc-immed-gain-change-if-large-adc-overload-enable
adi,agc-immed-gain-change-if-large-lmt-overload-enable
adi,agc-inner-thresh-high
adi,agc-inner-thresh-high-dec-steps
adi,agc-inner-thresh-low
adi,agc-inner-thresh-low-inc-steps
adi,agc-lmt-overload-large-exceed-counter
adi,agc-lmt-overload-large-inc-steps
adi,agc-lmt-overload-small-exceed-counter
adi,agc-outer-thresh-high
adi,agc-outer-thresh-high-dec-steps
adi,agc-outer-thresh-low
adi,agc-outer-thresh-low-inc-steps
adi,agc-sync-for-gain-counter-enable
adi,aux-adc-decimation
adi,aux-adc-rate
adi,aux-dac-manual-mode-enable
adi,aux-dac1-active-in-alert-enable
adi,aux-dac1-active-in-rx-enable
adi,aux-dac1-active-in-tx-enable
adi,aux-dac1-default-value-mV
adi,aux-dac1-rx-delay-us
adi,aux-dac1-tx-delay-us
adi,aux-dac2-active-in-alert-enable
adi,aux-dac2-active-in-rx-enable
adi,aux-dac2-active-in-tx-enable
adi,aux-dac2-default-value-mV
adi,aux-dac2-rx-delay-us
adi,aux-dac2-tx-delay-us
adi,axi-half-dac-rate-enable
adi,bb-clk-change-dig-tune-enable
adi,clk-output-mode-select
adi,ctrl-outs-enable-mask
adi,ctrl-outs-index
adi,dc-offset-attenuation-high-range
adi,dc-offset-attenuation-low-range
adi,dc-offset-count-high-range
adi,dc-offset-count-low-range
adi,dc-offset-tracking-update-event-mask
adi,debug-mode-enable
adi,digital-interface-tune-fir-disable
adi,digital-interface-tune-skip-mode
adi,elna-bypass-loss-mdB
adi,elna-gain-mdB
adi,elna-gaintable-all-index-enable
adi,elna-rx1-gpo0-control-enable
adi,elna-rx2-gpo1-control-enable
adi,elna-settling-delay-ns
adi,ensm-enable-pin-pulse-mode-enable
adi,ensm-enable-txnrx-control-enable
adi,external-rx-lo-enable
adi,external-tx-lo-enable
adi,fagc-adc-large-overload-inc-steps
adi,fagc-allow-agc-gain-increase-enable
adi,fagc-dec-pow-measurement-duration
adi,fagc-energy-lost-stronger-sig-gain-lock-exit-cnt
adi,fagc-final-overrange-count
adi,fagc-gain-increase-after-gain-lock-enable
adi,fagc-gain-index-type-after-exit-rx-mode
adi,fagc-lmt-final-settling-steps
adi,fagc-lock-level-gain-increase-upper-limit
adi,fagc-lock-level-lmt-gain-increase-enable
adi,fagc-lp-thresh-increment-steps
adi,fagc-lp-thresh-increment-time
adi,fagc-lpf-final-settling-steps
adi,fagc-optimized-gain-offset
adi,fagc-power-measurement-duration-in-state5
adi,fagc-rst-gla-en-agc-pulled-high-enable
adi,fagc-rst-gla-engergy-lost-goto-optim-gain-enable
adi,fagc-rst-gla-engergy-lost-sig-thresh-below-ll
adi,fagc-rst-gla-engergy-lost-sig-thresh-exceeded-enable
adi,fagc-rst-gla-if-en-agc-pulled-high-mode
adi,fagc-rst-gla-large-adc-overload-enable
adi,fagc-rst-gla-large-lmt-overload-enable
adi,fagc-rst-gla-stronger-sig-thresh-above-ll
adi,fagc-rst-gla-stronger-sig-thresh-exceeded-enable
adi,fagc-state-wait-time-ns
adi,fagc-use-last-lock-level-for-set-gain-enable
adi,frequency-division-duplex-independent-mode-enable
adi,frequency-division-duplex-mode-enable
adi,gc-adc-large-overload-thresh
adi,gc-adc-ovr-sample-size
adi,gc-adc-small-overload-thresh
adi,gc-dec-pow-measurement-duration
adi,gc-dig-gain-enable
adi,gc-lmt-overload-high-thresh
adi,gc-lmt-overload-low-thresh
adi,gc-low-power-thresh
adi,gc-max-dig-gain
adi,gc-rx1-mode
adi,gc-rx2-mode
adi,gc-use-rx-fir-out-for-dec-pwr-meas-enable
adi,gpo-manual-mode-enable
adi,gpo-manual-mode-enable-mask
adi,gpo0-inactive-state-high-enable
adi,gpo0-rx-delay-us
adi,gpo0-slave-rx-enable
adi,gpo0-slave-tx-enable
adi,gpo0-tx-delay-us
adi,gpo1-inactive-state-high-enable
adi,gpo1-rx-delay-us
adi,gpo1-slave-rx-enable
adi,gpo1-slave-tx-enable
adi,gpo1-tx-delay-us
adi,gpo2-inactive-state-high-enable
adi,gpo2-rx-delay-us
adi,gpo2-slave-rx-enable
adi,gpo2-slave-tx-enable
adi,gpo2-tx-delay-us
adi,gpo3-inactive-state-high-enable
adi,gpo3-rx-delay-us
adi,gpo3-slave-rx-enable
adi,gpo3-slave-tx-enable
adi,gpo3-tx-delay-us
adi,mgc-dec-gain-step
adi,mgc-inc-gain-step
adi,mgc-rx1-ctrl-inp-enable
adi,mgc-rx2-ctrl-inp-enable
adi,mgc-split-table-ctrl-inp-gain-mode
adi,qec-tracking-slow-mode-enable
adi,rf-rx-bandwidth-hz
adi,rf-tx-bandwidth-hz
adi,rssi-delay
adi,rssi-duration
adi,rssi-restart-mode
adi,rssi-unit-is-rx-samples-enable
adi,rssi-wait
adi,rx-fastlock-delay-ns
adi,rx-fastlock-pincontrol-enable
adi,rx-rf-port-input-select
adi,rx-rf-port-input-select-lock-enable
adi,rx1-rx2-phase-inversion-enable
adi,split-gain-table-mode-enable
adi,tdd-skip-vco-cal-enable
adi,tdd-use-dual-synth-mode-enable
adi,temp-sense-decimation
adi,temp-sense-measurement-interval-ms
adi,temp-sense-offset-signed
adi,temp-sense-periodic-measurement-enable
adi,trx-synthesizer-target-fref-overwrite-hz
adi,tx-attenuation-mdB
adi,tx-fastlock-delay-ns
adi,tx-fastlock-pincontrol-enable
adi,tx-lo-powerdown-managed-enable
adi,tx-rf-port-input-select
adi,tx-rf-port-input-select-lock-enable
adi,txmon-1-front-end-gain
adi,txmon-1-lo-cm
adi,txmon-2-front-end-gain
adi,txmon-2-lo-cm
adi,txmon-dc-tracking-enable
adi,txmon-delay
adi,txmon-duration
adi,txmon-high-gain
adi,txmon-low-gain
adi,txmon-low-high-thresh
adi,txmon-one-shot-mode-enable
adi,update-tx-gain-in-alert-enable
adi,xo-disable-use-ext-refclk-enable
bist_prbs
bist_timing_analysis
bist_tone
calibration_switch_control
digital_tune
direct_reg_access
gaininfo_rx1
gaininfo_rx2
gpo_set
initialize
loopback
multichip_sync

**Init ad9361-phy**
iio_attr -d ad9361-phy calib_mode manual
iio_attr -c ad9361-phy -o altvoltage1 powerdown 1
iio_attr -c ad9361-phy -o altvoltage0 powerdown 1
iio_attr -D ad9361-phy initialize 1

---

**cf-ad9361-lpc**

cd /sys/bus/iio/devices/iio:device3
iio_attr -c cf-ad9361-lpc
iio_attr -B cf-ad9361-lpc

buffer
dev
in_voltage0_calibbias
in_voltage0_calibphase
in_voltage0_calibscale
in_voltage1_calibbias
in_voltage1_calibphase
in_voltage1_calibscale
in_voltage_samples_pps
in_voltage_sampling_frequency
in_voltage_sampling_frequency_available
name
of_node -> ../../../../../firmware/devicetree/base/pl-bus/cf-ad9361-lpc@99020000
power
scan_elements
uevent


cd /sys/kernel/debug/iio/iio:device3
iio_attr -D cf-ad9361-lpc

direct_reg_access
pseudorandom_err_check

iio_readdev --buffer-size 4194304 --samples 10 cf-ad9361-lpc | hexdump

---

