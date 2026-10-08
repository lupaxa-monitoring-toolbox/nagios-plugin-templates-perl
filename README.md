<p align="center">
    <a href="https://github.com/lupaxa-monitoring-toolbox">
        <img src="https://raw.githubusercontent.com/the-lupaxa-project/brand-assets/master/logos/organisations/monitoring-toolbox/readme-logo.png" alt="Organisation Logo" />
    </a>
</p>

<h1 align="center">Nagios Plugin Templates Perl</h1>

Perl templates for Nagios-style plugin checks. Copy a script, put the check in `main`, and keep the status helpers so the plugin prints a prefixed line and exits with the matching code.

## Templates

| Script                                 | Purpose                                                      |
| -------------------------------------- | ------------------------------------------------------------ |
| [basic](src/basic/basic.pl)            | A check with hard-coded warning and critical levels.         |
| [advanced](src/advanced/advanced.pl)   | The same check, with `-w` and `-c` to override those levels. |

Both scripts use four helpers:

| Helper            | Output prefix | Exit |
| ----------------- | ------------- | ---- |
| `handle_ok`       | `OK`          | `0`  |
| `handle_warning`  | `WARNING`     | `1`  |
| `handle_critical` | `CRITICAL`    | `2`  |
| `handle_unknown`  | `UNKNOWN`     | `3`  |

`basic.pl` calls `main` directly. `advanced.pl` parses arguments first, then calls `main`. The warning level must stay below the critical level.

## Run

```bash
perl src/basic/basic.pl
perl src/advanced/advanced.pl -w 75 -c 90
```

The sample check draws a random value from 1 to 100 and compares it with the warning and critical levels. Replace that body with the real check.

Requires Perl.

## Development

```bash
make init
make perl-check
```

<a href="https://github.com/the-lupaxa-project">
    <img src="https://raw.githubusercontent.com/the-lupaxa-project/brand-assets/master/logos/components/footer-for-child-orgs.svg" alt="The Lupaxa Project Footer" width="100%" />
</a>
