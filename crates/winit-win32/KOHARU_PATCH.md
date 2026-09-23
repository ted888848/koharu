# Koharu patch

This crate is the published `winit-win32` `0.31.0-beta.3` source, checksum
`25fb480c41df01d351f656cbf3ad74013f8a9d22bb5b2dcab59f9167e7a0b6ec`.

The local change in `src/event_loop.rs` filters `EnumThreadWindows` results by
their registered window procedure before reading `GWL_USERDATA`. The CEF
runtime creates windows on Winit's UI thread and stores unrelated values in
that field; treating those as Winit `WindowData` caused an access violation
when moving or maximizing the main window.
