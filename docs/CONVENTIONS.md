# Data conventions

This catalog covers Wi-Fi chipsets with evidence of access to raw IQ samples through undocumented, diagnostic, or test modes, and projects using those capabilities. Packet capture, RSSI, or CSI alone does not establish raw IQ access. A device with an ordinary Wi-Fi specification is not enough to add a chipset.

## Units and notation

- Use **MHz** for all RF frequencies, frequency ranges, channel widths, and analog bandwidths, including project descriptions: `5800 MHz`, `2400–2483.5 MHz`. Convert GHz or kHz values from sources without adding precision.
- Use **MS/s** for sample rates. One complex sample is one I/Q pair; state explicitly if a source counts I and Q separately.
- Use `bit` for resolution **per I or Q component**. Distinguish ADC resolution, meaningful captured bits, and storage width; a 16-bit container does not establish a 16-bit ADC.
- Use `Mbit/s` or `Gbit/s` for link throughput. Keep product and interface names such as USB 3.0 unchanged.
- Write separate tuning intervals with `<br>` in tables. Do not fill gaps or imply continuous tuning when only channels or discrete settings are known.
- Use `Unknown` for missing evidence, `Not tested` for an explicitly untested capability, and `N/A` only when a field does not apply. Existing ESP32 `?`, `❓`, and italic estimates are legacy notation; new entries should use explicit labels.

## What each field means

| Field | Required interpretation |
| --- | --- |
| Chipset / device | Exact IC and tested board or adapter, with revision when relevant. Shared chip families or marketing names do not establish compatibility. |
| Sample rate, max | Highest supported raw IQ acquisition rate evidenced by the cited implementation. Identify configuration-only values and finite captures; this is not sustained host throughput. |
| Resolution | Meaningful bits per component at the capture point, written as a bit count only. Keep storage and host formats in the source documentation. Do not infer physical ADC precision or ENOB from packed data. |
| Analog bandwidth | Measured or documented analog receive passband, with measurement criterion when available. Digital sample rate and configured Wi-Fi channel width are separate quantities. Use a separate column or note for capture/channel bandwidth. |
| Frequency range | Source-backed tuning intervals in MHz, without commentary in the cell. Verify their meaning during review: PLL lock or an accepted parameter alone does not prove useful reception. Detailed qualifications belong in the linked source and PR evidence. |
| Realtime output sample rate | Sustained complex IQ rate over a named interface. State sample packing, channels, duration, and losses for measurements. A link-speed calculation is a theoretical ceiling and must be labeled. |
| Output interface | Actual path used to retrieve samples; distinguish a board's available port from a demonstrated streaming path. |
| Simultaneous IQ channels | Only the verified number of simultaneous IQ channels. Wi-Fi MIMO support does not prove synchronized SDR channels. |
| Source | Primary evidence supporting the specific values and restrictions, preferably a commit-pinned file, release, or reproducible measurement. |

## Evidence and uncertainty

Use a short qualifier wherever the distinction changes the interpretation:

- **Measured:** a hardware experiment with a named setup, method, and accessible result. Say whether this is a contributor measurement or an upstream report.
- **Documented:** an explicit statement in primary project or vendor documentation; it has not necessarily been independently reproduced.
- **Code-derived:** a value or limit read from an implementation. Link the relevant code and explain the derivation; do not describe this as a hardware measurement.
- **Theoretical:** an estimate with its assumptions and calculation, separate from demonstrated performance.

Use primary sources: implementation code, original project documentation, vendor documentation, or original experiment reports. Search snippets, generated summaries, reposts, and an AI answer are discovery aids, not evidence. A repository homepage can identify a project; unusual numeric claims need a specific file, section, or experiment.

Record the revision or release and the date of a substantive check (`YYYY-MM-DD`) in PR evidence. Prefer commit permalinks there for changing implementations. Keep review logs out of the README. A newer source may supersede an older result, but preserve the setup and scope that explain the difference in the evidence. If sources conflict, state the conflict or narrow the claim; do not average numbers or silently pick the largest one.

Unknown secondary fields do not disqualify an otherwise evidenced chipset. A raw IQ capability without evidence belongs in an issue for investigation, not in the supported-chipset table. Never extrapolate from another chipset or claim that every adapter with the same IC works.

## Presentation

Keep the README concise and in English. Preserve HTML chipset tables. For MediaTek and Realtek, put Device and Chipset first as separate columns, and Source last. Cells should contain short values; link the upstream repository in Source for implementation details. Use brief blockquote notes below tables only where needed. Do not add source-check logs or detailed fact-check narratives to the README. Avoid unrelated table reformatting in factual corrections. Existing entries are not automatically proof for new entries.

For a project, include its name, upstream link, chipset, what it does with IQ, and material hardware or implementation limits. Attribute upstream demonstration claims; do not imply local testing. Avoid marketing superlatives and unverified performance claims.
