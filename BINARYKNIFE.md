# BinaryKnife integration fork

Based on 416rehman/DeepZero at
`cdf4e7c23dddc615970f4cbe29ec1c75d9f4239a`. Original MIT attribution and license
remain unchanged. The upstream engine, PE ingestion, Ghidra extraction, scanner
rules and optional model review remain the reusable implementation.

Generic corrections in this fork:

* Consume `DEEPZERO_MAX_FUNCTIONS` and `DEEPZERO_MAX_DEPTH` in dispatch extraction;
  count actual decompilation requests, including structural discovery. Preserve
  explicit limit flags and partial entry-only output.
* Limit Semgrep worker count and submit explicit staged files. On the tested
  Windows setup, directory-targeted scans stalled while explicit-file scans
  completed. The underlying Semgrep directory-discovery cause remains unknown.
* Refuse oversized Windows command lines rather than silently omitting files.
* On scanner timeout, reuse the existing process-tree termination helper.

BinaryKnife supplies its own fixed adapter recipe, GUI and MCP contract outside
this fork. Static matches and model prose are candidates, not proof of runtime
behavior, exploitable defects or driver safety. No target-specific driver
execution logic, exploit code, acquisition transport or protection bypass is
included here.
