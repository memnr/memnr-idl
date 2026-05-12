# memnr-idl

Anchor IDL for memnr on-chain programs.

## Programs

### partner-fee-share

Trustless fee distribution for Meteora DBC + DAMM V2 pools. Splits trading fees between platform and TikTok creators.

- **Program ID:** `MEM1FmjMd394WXGFx8yU5C5F5Q2oqLW3Ckyb2ADW9TT`
- **Network:** Solana Devnet (mainnet coming soon)

### Usage

```typescript
import idl from '@memnr/idl/partner-fee-share/idl.json';
import { Program, AnchorProvider } from '@coral-xyz/anchor';

const program = new Program(idl, provider);
```

### Account: FeeShareConfig

Per-token configuration storing creator/platform split, pool references, and accumulated fee balances. Derived as a PDA seeded by `["fee_share_config", base_mint]`.

### Instructions

| Instruction | Description |
|---|---|
| `initializeConfig` | Create per-token fee share config at launch time |
| `claimDbc` | CPI to Meteora DBC to harvest partner trading fees |
| `claimDammV2` | CPI to Meteora DAMM V2 to harvest LP position fees |
| `claimUser` | Creator withdraws their accumulated fee share |
| `claimPlatform` | Platform admin withdraws the platform's fee share |
| `reclaimExpired` | Admin reclaims expired unclaimed creator fees |
| `setGraduated` | Admin marks a pool as graduated with DAMM V2 references |
| `updateExpiry` | Admin updates the fee expiry duration |
| `updateCreatorBps` | Admin updates the creator BPS share |
| `updateAdmin` | Admin rotates the admin authority |
| `updateCreator` | Admin reassigns the creator wallet |
| `distributeCreator` | Admin pushes creator fees to their wallet |

## License

Copyright © 2026 memnr. All rights reserved. No license is granted for use, modification, or redistribution.
