# Anomic ZK-SNARK Artifacts

Pre-compiled zero-knowledge proof artifacts for the Anomic privacy mixer.

## Production Files (Active)

| File | Network | Size | Status |
|------|---------|------|--------|
| `withdraw.wasm` | ETH/ERC20 | 2.0 MB | ✅ Active |
| `withdraw.zkey` | ETH/ERC20 | 5.2 MB | ✅ Active |
| `verification_key.json` | ETH/ERC20 | 3.8 KB | ✅ Active |
| `btc_withdraw.wasm` | BTC | 1.9 MB | ✅ Active |
| `btc_withdraw.zkey` | BTC | 3.1 MB | ✅ Active |
| `btc_verification_key.json` | BTC | 3.1 KB | ✅ Active |
| `btc_transfer.wasm` | BTC Transfer | 1.9 MB | ✅ Active |
| `btc_transfer.zkey` | BTC Transfer | 3.4 MB | ✅ Active |


## Checksums

All files are checksummed with SHA-256. See [checksums.sha256](./checksums.sha256).

```bash
# Verify integrity
sha256sum -c checksums.sha256
```

Current checksums:

```
54fbb939e669a19d5dcba620b749a90a5e9abaae360ebf65332d300af8859dd8  withdraw.wasm
976b72d2c99a175db889287540bedf9efbd17582abdf71f4ce56c30ab6fbc211  btc_withdraw.zkey
08c96601b5ba903bdebf10fff230c0c27b0eb0137586674841ff4f658c8c38c1  btc_transfer.zkey
```

### Verification

To verify the ceremony was conducted correctly:

1. Check participant contribution hashes are published
2. Verify the final beacon comes from a public block hash
3. Run the verification script:

```bash
node verify-artifacts.js
node verify-ceremony.js
```

## Usage

### Frontend Integration

The frontend loads these artifacts directly:

```javascript
import { initzkProver } from '@anomic/zkprover';

// Automatically loads wasm, zkey, vkey from /circuits/
await initzkProver();
```

### Manual Proof Generation

```bash
# Generate proof
snarkjs groth16 fullprove input.json withdraw.wasm withdraw.zkey proof.json public.json

# Verify locally
snarkjs groth16 verify verification_key.json public.json proof.json
```

## License

MIT
