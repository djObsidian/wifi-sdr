# Contributing

Help make this a useful, checkable catalog of Wi-Fi hardware repurposed for SDR. Small corrections, reproducible experiments, and well-supported new entries are welcome. Read the [data conventions](docs/CONVENTIONS.md) before changing technical claims.

## Before opening a pull request

1. Check existing entries and open PRs for duplicates. Keep one coherent change per PR; separate factual updates from broad formatting changes.
2. Find primary evidence of raw IQ access for the exact chipset. Follow the source through to the relevant code, documentation, or experiment, rather than copying a summary.
3. For each new or changed value, provide a direct source and its revision or release. Identify what you personally tested, what upstream reports, and what you inferred from code.
4. Use MHz for frequencies and bandwidths, and MS/s for sample rates. Keep unknowns explicit. Distinguish capture rate from streaming throughput, channel width from analog bandwidth, and hardware chains from simultaneous SDR capture.
5. Preview the Markdown, check changed links and table alignment, and inspect the diff for unintended changes. Documentation-only submissions do not require hardware tests when they accurately attribute upstream evidence.

For your own measurements, include the board and revision, firmware/driver revision, configuration, sample format, method, and results or a small representative artifact. Streaming claims need duration and loss information. Frequency-range claims need the method used to establish reception. Never claim hardware testing that you did not perform.

For a project listing, link the upstream implementation and explain its chipset, use of IQ, and current limitations in a few sentences. An idea without an implementation should be discussed in an issue first.

## AI-assisted contributions

AI assistance is welcome; the contributor remains responsible for every claim and link. Disclose material AI assistance in the PR and state what you actually checked. Do not submit generated catalogs, guessed specifications, invented citations, or long explanations that obscure missing evidence. Reading source code is not a hardware test, and a successful build does not validate RF performance.

A small, supported change with unknown fields is more useful than a complete-looking table built from guesses. If you cannot establish a claim, leave it out or open an issue with the evidence and the specific question.

## Review

Use the [PR template](.github/pull_request_template.md). Reviewers follow the [review guide](docs/REVIEWING.md); automated reviewers also follow [AGENTS.md](AGENTS.md).

Review focuses on the changed claims and their evidence. Unsupported numeric claims, misleading capability labels, or links that do not support the text need correction before acceptance. A reviewer may recommend acceptance with explicitly unknown secondary fields. Clear typo and link fixes should not require an unrelated hardware revalidation.

If evidence is inaccessible, include a citable excerpt or alternate primary source with enough context to check it. Do not treat an unavailable page as proof that a claim is false.
