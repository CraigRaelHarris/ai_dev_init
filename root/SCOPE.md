# MVP scope

Status: proposed; confirm with client before treating as agreed.

## Objective
[Deliver one useful end-to-end workflow for a named user.]

## Included
- [Capability]

## Excluded / deferred
- [Capability and reason]

## First complete workflow
[Trigger] -> [validation] -> [integration or processing] -> [stored state] -> [visible outcome]

## Success measures
| Measure | Current baseline | Target | How measured |
| --- | --- | --- | --- |
| [Business measure] | [Value] | [Value] | [Method] |

## Acceptance examples
- Given [normal input], when [action], then [observable result].
- Given [invalid input], when [action], then [clear error and no unwanted change].
- Given [external failure], when [action], then [agreed retry/manual outcome].
- Given [duplicate input], when [action], then [agreed duplicate handling].

## Operational requirements
- Authentication / permissions: [decision needed]
- Expected volume and concurrency: [details]
- Logging and audit needs: [details]
- Backup / restore / retention: [details]
- Hosting and support owner: [details]

## Definition of done
- Agreed acceptance examples work, using mocks where explicitly agreed.
- API and frontend build; relevant tests, lint and type checks pass.
- A fresh local database can be created using migrations and seeded safely.
- Configuration and run instructions are documented and reproducible.
- Secrets and personal data are absent from committed files and logs.
- Known limitations are documented; business owner has reviewed the demo.

## Sign-off
- Scope owner: [name]
- Agreement date / outstanding conditions: [details]
