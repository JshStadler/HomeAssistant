# HomeAssistant

## 24V Axpert grid fallback

The 24V Axpert uses **Utility Solar Battery (USB)** for low-SoC grid fallback.
This works around an observed inverter charging issue in Solar Utility Battery
(SUB) mode. The fallback condition, command, recovery check, comments and log
message all use USB consistently.

With the default settings, filtered SmartShunt SoC below 20% selects USB. At
30% or above, the firmware restores Solar Battery Utility (SBU) only if it
initiated the fallback and the inverter is still in USB. Restored user-set
thresholds remain in effect. USB already selected manually is not claimed by
the fallback automation.

Home Assistant automations that protect or switch the **24V** inverter should
also select `Utility Solar Battery`. The runtime-test protection already does
so. The separate Kodak/48V inverter retains its existing SUB/SBU behavior.
The SUB option remains available in the 24V selector for manual use; its
protocol mapping is unchanged.
