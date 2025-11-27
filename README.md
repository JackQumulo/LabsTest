# LabsTest

LabsTest is a lightweight repository that demonstrates YAML security hygiene and includes a set of sample detection rule files and a small scanner for identifying suspicious YAML patterns.

This branch (copilot/add-sample-yaml-and-scanner) includes the following artifacts:

- sample.yaml — A benign example configuration with 5 service entries.
- malicious-example.yaml — An educational, non-executable YAML demonstrating unsafe patterns (unsafe tags, anchor abuse, remote references). Do NOT parse with unsafe YAML loaders.
- scan_yaml.py — A conservative, text-based scanner that flags suspicious YAML constructs without using unsafe deserialization.
- .github/workflows/scan-yaml.yml — A GitHub Actions job that runs the scanner on push and pull requests.
- sigma/, falco/, osquery/, elastalert/ — Example detection rule files for ransomware-related behaviors (added for demonstration and testing).

Purpose

The goal of this repository is to provide a small, safe set of artifacts you can use to:

- Learn about malicious YAML patterns and how to detect them.
- Validate scanner rules and CI integration for YAML safety checks.
- Serve as a starting point for building detection rules across SIGMA, Falco, osquery, and ElastAlert.

Quick start

1. Checkout the branch:
   git checkout copilot/add-sample-yaml-and-scanner

2. Run the YAML scanner locally:
   python3 scan_yaml.py --fail-on-high

3. Review the detection rules in the sigma/, falco/, osquery/, and elastalert/ directories and tune them for your environment.

Security notes

- Never parse untrusted YAML with unsafe deserializers (e.g., avoid PyYAML yaml.load on untrusted input).
- Use schema validation and limit anchor/alias expansion where supported.
- Treat any external URLs referenced in YAML as untrusted; do not auto-fetch or execute.
- Run scanners in CI and require review for changes that modify detection rules or workflows.

Contributing

Contributions welcome. Please open a pull request against main and include tests or sample inputs for new rules. If you add new detection formats, include a short README or test that demonstrates how to validate the syntax.

License

MIT

Contact

Maintainer: JackQumulo
