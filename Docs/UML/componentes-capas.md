# Component diagram: screens, ports and adapters

This diagram shows the three layers of Yucu: screens (`src/components/`), ports (`src/core/chain/ports.ts`) and adapters (`SimulatedChain` and the testnet adapters, if they exist).
Screens talk only to ports, and ports talk to the adapters of the simulated or test network.
A screen must never import `@stellar/stellar-sdk` (rule 4 of `AGENTS.md`); this is shown with a crossed arrow.

![Component diagram: screens, ports and adapters](img/componentes-capas.png)

## Elements

| Element | Type | Description |
|---|---|---|
| Screens | Layer (package) | Layer of user interface screens. |
| src/components/ | Component | Folder that holds the screens. |
| Ports | Layer (package) | Layer of interfaces through which screens reach the network. |
| src/core/chain/ports.ts | Component | File that defines the ports. |
| Adapters | Layer (package) | Layer that talks to the simulated or test network. |
| SimulatedChain | Component | Simulated network adapter. |
| Testnet adapters | Component | Test network adapters, only if they exist in `src/core/chain/`. |
| @stellar/stellar-sdk | External package | Stellar SDK. Screens are forbidden to import it (`AGENTS.md`, rule 4). |
| uses | Dependency | Screens use the ports. |
| communicates with | Dependency | Ports communicate with the adapters. |
| FORBIDDEN (crossed arrow) | Forbidden dependency | Screen to `@stellar/stellar-sdk`. |

## Not defined in the sources

- TODO: list here anything the sources do not define (for example, exact names of the port methods or whether testnet adapters exist).

## Sources

- `AGENTS.md`
- `src/core/chain/`
- `docs/arquitectura/yucu-capas.svg`
