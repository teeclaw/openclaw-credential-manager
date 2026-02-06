# Changelog

## Version 1.2.0 (2026-02-06)

### 🔐 Crypto-Specific Credential Detection

**Enhanced detection patterns** for blockchain and cryptocurrency credentials.

### Added

**New sensitive key patterns in scan.py:**
- `private_key` / `private-key` - Wallet private keys
- `passphrase` - Seed passphrases
- `mnemonic` - BIP39 recovery phrases
- `seed_phrase` / `seed-phrase` - Wallet seed phrases
- `signing_key` / `signing-key` - Transaction signing keys
- `wallet_key` / `wallet-key` - Wallet access keys

**Documentation:**
- Added "Detection Parameters" section to SKILL.md
- High-level overview of file patterns, sensitive keys, and security checks

### Why This Matters

Crypto credentials (private keys, mnemonics, seed phrases) are **permanent secrets** — once leaked, funds can be drained instantly with no recovery. Previous detection focused on API keys (revocable), missing the most critical crypto patterns.

This update ensures wallet keys and seed phrases are treated with the same security rigor as other credentials.

### Technical Details

**Pattern count:** 15 sensitive patterns (up from 9)
**Detection coverage:** Now includes crypto-native credential types
**Backward compatible:** Existing scans continue to work

---

## Version 1.1.0 (2026-02-05)

### 🔒 SECURITY FOUNDATION UPDATE

**Major philosophical shift:** This is now positioned as **mandatory core infrastructure**, not an optional convenience tool.

### Added

**CORE-PRINCIPLE.md** - New document establishing:
- `.env` is MANDATORY, not optional
- Why centralized credential management is non-negotiable
- The security rationale for this approach
- Implementation requirements for all skills
- Zero exceptions policy

**enforce.py** - New validation script:
- `require_secure_env()` - Enforce .env security before running
- `get_credential()` - Safe credential loading with validation
- Fail-fast system: refuses to run if credentials insecure
- Can be imported by other skills to enforce standard

### Changed

**SKILL.md:**
- Updated description to emphasize "MANDATORY" status
- Added "This Is Not Optional" warning
- New "The Foundation" section explaining requirements
- Added "For Skill Developers" section showing enforcement usage
- Clearer security messaging throughout

**README.md:**
- Repositioned as "Core Security Infrastructure"
- Added "Why This Matters" section upfront
- Emphasized mandatory nature in opening
- Updated status badge to reflect infrastructure role

### Technical Details

**Package size:** 22 KB (was 15 KB)
**Files:** 10 total
- 3 documentation files (SKILL.md, README.md, CORE-PRINCIPLE.md)
- 5 scripts (scan, consolidate, validate, enforce, cleanup)
- 2 references (security, supported-services)

### Philosophy

**Before:** "Use this skill to organize your credentials"
**After:** "Your OpenClaw deployment is non-compliant until credentials are consolidated"

This isn't a feature request. It's a security requirement.

---

## Version 1.0.0 (2026-02-05)

Initial release with core functionality:
- Credential scanning
- .env consolidation
- Security validation
- Old file cleanup
- Comprehensive documentation
