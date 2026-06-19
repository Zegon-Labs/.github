<a name="readme-top"></a>

<div align="center">

<img src="https://raw.githubusercontent.com/Zegon-Labs/.github/main/assets/banner.png" alt="ZEGON — It can't see you. It reads you." width="100%" />

<br/>

[![][website-shield]][website-link]
[![][game-shield]][game-link]
[![][github-star]][github-link]
[![][og-shield]][og-link]

</div>

### 👋 Welcome to Zegon Labs

We're building **provably fair AI gaming** — where the opponent can't cheat, and you can prove it.

Most AI opponents run on opaque servers. When you lose, you wonder if the house rigged the read or rewrote its move after seeing yours — and you can never know. **ZEGON** is our answer: a pixel-art gunslinger duel against a blindfolded AI that *reads your patterns* but **cannot see your current move**. Every round leaves on-chain proof that ZEGON committed before you acted.

Built on **0G** (Compute + Chain + Storage) for the **Zero Cup 2026** hackathon. The repositories below are the open-source layers — playable today, forkable tomorrow.

### ⭐️ Our Projects

| Project | Description |
| :--- | :--- |
| [**🤠 ZEGON DApp**][dapp-github] | Turn-based duel vs a blindfolded AI with sealed inference on 0G Compute. Commit-reveal on Galileo, Blindsight meter, VERIFY flow — no wallet required.<br/><br/>[![][game-shield]][game-link] [![][contract-shield]][contract-link] |
| [**🌐 ZEGON Landing**][landing-github] | Official marketing site — the provably fair AI gaming use case, commit flow preview, 0G stack breakdown, FAQ, and launch overlay into the dapp.<br/><br/>[![][website-shield]][website-link] |

### 📦 Ecosystem

| Repository / Package | Purpose | Language |
| :--- | :--- | :---: |
| [**🎮 Zegon-DApp**][dapp-github] | Monorepo — Phaser 3 client, Node API, Solidity contracts, full 0G integration | ![][lang-typescript] |
| [**🌐 Zegon-Landing**][landing-github] | Vite + React landing page with dark neo-western glitch design system | ![][lang-typescript] |
| `packages/game-core` | Pure duel logic — combat, Blindsight, weapons, validation | ![][lang-typescript] |
| `packages/game-client` | Phaser 3 + Vite game client (426×240 pixel-art, CRT glitch shaders) | ![][lang-typescript] |
| `packages/game-server` | Node API — 0G Compute inference, chain commit-reveal, Storage uploads, gas sponsorship | ![][lang-typescript] |
| `contracts/` | `ZegonDuel.sol` on Galileo testnet — `commitMove` → `revealMove` → `recordDuel` | ![][lang-solidity] |

### 🏗️ How It Fits Together

```
                    ZEGON Landing (marketing)
                              │
                         launches into
                              ▼
                    ZEGON DApp (Phaser client)
                              │
              ┌───────────────┼───────────────┐
              │               │               │
         reads history    commits hash    uploads proof
              ▼               ▼               ▼
       ┌────────────┐  ┌────────────┐  ┌────────────┐
       │ 0G Compute │  │  0G Chain  │  │ 0G Storage │
       │            │  │  (Galileo) │  │            │
       │ sealed TEE │  │ commit-    │  │ duel log + │
       │ inference  │  │ reveal     │  │ attestation│
       └────────────┘  └────────────┘  └────────────┘
              │               │               │
              └───────────────┴───────────────┘
                              │
                    VERIFY after every duel
                    (timestamp + attestation)
```

**Per-round flow:** ZEGON receives only your action history → sealed inference on 0G Compute → `commitMove(hash)` on-chain **before** your buttons unlock → you choose blind → `revealMove` → resolve → Blindsight updates. After the duel: `recordDuel` + blob upload to 0G Storage → **VERIFY ON-CHAIN** at `/api/duel/verify/:duelId`.

### 🎯 What Makes ZEGON Different

| | Typical AI game | ZEGON |
| :--- | :--- | :--- |
| When you lose | Was it rigged? | You can check |
| AI move timing | Hidden server | Locked first |
| Can the house cheat? | You'd never know | Proof exposes it |
| Does the duel feel real? | Often hollow | Stakes land |

**Tagline:** *"It can't see you. It reads you. Outdraw the blind."*

**The wedge:** provably fair today covers RNG (dice, casino). ZEGON applies it to **AI decisions with hidden information** — sealed inference proves the model only saw your history; commit-reveal proves it locked in before you moved.

### ⚔️ Core Gameplay

- **Actions:** `FIRE_HIGH`, `FIRE_LOW`, `DODGE`, `FEINT`, `RELOAD` — simultaneous selection, turn-based to hide inference latency.
- **Blindsight:** ZEGON's blindfold meter rises when it predicts you correctly; drops when you surprise it or feint. At max → **DEADEYE** (guaranteed lethal read).
- **Weapons:** Revolver (balanced), Shotgun (high damage, high pattern noise), Derringer (fast, evasive), Glitch Pistol (rare — low readability).
- **No wallet:** backend sponsors gas on Galileo testnet so anyone can play.

### 🔗 On-Chain (Galileo testnet)

| | |
| :--- | :--- |
| **Contract** | [`0x2Fc47e82c30B9d1B9193fa1978E96A92d7b760b0`][contract-link] |
| **Chain ID** | `16602` |
| **RPC** | `https://evmrpc-testnet.0g.ai` |
| **Explorer** | [chainscan-galileo.0g.ai][explorer-link] |
| **Faucet** | [faucet.0g.ai][faucet-link] |

### 🤝 Contributing

We welcome PRs, bug reports, and gameplay feedback across every public repository.

- **Game logic** — extend `packages/game-core` (combat rules, weapons, modes).
- **0G integration** — improve Compute prompts, chain flows, or Storage persistence in `game-server`.
- **Visual / UX** — Phaser scenes, glitch shaders, or landing sections in their respective repos.
- **Docs** — full design spec lives in [`ZEGON.md`][zegon-spec] inside Zegon-DApp.

### 🪪 License

Per-repository. See individual repositories for license details.

---

> \[!TIP]
>
> **Play now:** [Launch ZEGON][game-link] → duel the blind AI → hit **VERIFY ON-CHAIN** after the fight. Fair dice already exist. ZEGON proves the *mind* is fair.

<!-- LINK GROUP -->

[website-link]: https://zegon-landing.vercel.app
[website-shield]: https://img.shields.io/badge/website-zegon--landing.vercel.app-B3122B?labelColor=0A0911&style=flat-square&logo=safari&logoColor=white

[game-link]: https://zegon-dapp.vercel.app
[game-shield]: https://img.shields.io/badge/play-zegon--dapp.vercel.app-B3122B?labelColor=0A0911&style=flat-square&logo=gamepad&logoColor=white

[github-link]: https://github.com/Zegon-Labs
[github-star]: https://img.shields.io/github/stars/Zegon-Labs?color=B3122B&labelColor=0A0911&style=flat-square&logo=github

[og-link]: https://0g.ai
[og-shield]: https://img.shields.io/badge/built%20on-0G-B3122B?labelColor=0A0911&style=flat-square&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSJ3aGl0ZSIgc3Ryb2tlLXdpZHRoPSIyIiBzdHJva2UtbGluZWNhcD0icm91bmQiIHN0cm9rZS1saW5lam9pbj0icm91bmQiPjxjaXJjbGUgY3g9IjEyIiBjeT0iMTIiIHI9IjEwIi8+PC9zdmc+&logoColor=white

[dapp-github]: https://github.com/Zegon-Labs/Zegon-DApp
[landing-github]: https://github.com/Zegon-Labs/Zegon-Landing

[contract-link]: https://chainscan-galileo.0g.ai/address/0x2Fc47e82c30B9d1B9193fa1978E96A92d7b760b0
[contract-shield]: https://img.shields.io/badge/contract-Galileo-B3122B?labelColor=0A0911&style=flat-square&logo=ethereum&logoColor=white

[explorer-link]: https://chainscan-galileo.0g.ai
[faucet-link]: https://faucet.0g.ai
[zegon-spec]: https://github.com/Zegon-Labs/Zegon-DApp/blob/main/ZEGON.md

[lang-typescript]: https://img.shields.io/badge/typescript-B3122B?labelColor=0A0911&style=flat-square&logo=typescript&logoColor=white
[lang-solidity]: https://img.shields.io/badge/solidity-B3122B?labelColor=0A0911&style=flat-square&logo=solidity&logoColor=white
