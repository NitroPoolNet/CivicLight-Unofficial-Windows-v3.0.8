# CivicNet Core v3.0.8 — Unofficial Windows Build

This is an **unofficial Windows build of CivicNet Core v3.0.8**, provided by NitroPool at the request of community members who use the standard CivicNet Core desktop wallet rather than the separate HVL-focused Windows wallet.

The binary was compiled directly from the official CivicLight `v3.0.8` source.

## Why this build is available

CivicNet Core v3.0.8 introduces the latest upstream HVL consensus, validation and token-database changes.

This standard Windows Qt wallet is being provided for community members who do not use the separate HVL Windows wallet but still need an updated CivicNet Core wallet compatible with the current network.

Although this is the standard Core interface, it includes the required HVL network support contained in the official v3.0.8 source.

## Build information

* Version: `CivicNet Core v3.0.8`
* Platform: Windows x86-64
* Source repository: https://github.com/CivicLight/CivicNet
* Source tag: [`v3.0.8`](https://github.com/CivicLight/CivicNet/releases/tag/v3.0.8)
* Source commit: [`397953a67eb8498333f714d12aa53864a965da37`](https://github.com/CivicLight/CivicNet/commit/397953a67eb8498333f714d12aa53864a965da37)
* Binary: `civicnet-qt-v3.0.8-win64.exe`

## Updating an existing wallet

1. Close CivicNet completely and confirm it is no longer running.
2. Back up your `wallet.dat` file and CivicNet data directory.
3. Download and verify `civicnet-qt-v3.0.8-win64.exe`.
4. Complete the required one-time chainstate reindex described below.
5. Allow the wallet to finish rebuilding and synchronizing.
6. Open **Help → Debug window → Console** and run `getblockcount` to confirm the current height.

## Required one-time chainstate reindex

When upgrading an existing CivicNet data directory to v3.0.8, the wallet must rebuild its chainstate so the new canonical HVL token state can be created.

Open PowerShell, change to the folder containing the wallet and run:

```powershell
cd "C:\path\to\your\CivicNet\wallet"

.\civicnet-qt-v3.0.8-win64.exe -reindex-chainstate
```

For example:

```powershell
cd "D:\Wallets\Civicnet\civicnet-qt-v3.0.8"

.\civicnet-qt-v3.0.8-win64.exe -reindex-chainstate
```

If CivicNet uses a custom data directory, include it explicitly:

```powershell
.\civicnet-qt-v3.0.8-win64.exe `
  -datadir="D:\Wallets\Civicnet" `
  -reindex-chainstate
```

The correct option is **`-reindex-chainstate`**, not `-reindex`.

Rebuilding can take some time. Do not close the wallet while it is rebuilding. Existing block files are reused, so the blockchain should not need to be downloaded again.

After the rebuild and synchronization have completed, close the wallet and start it normally without the `-reindex-chainstate` option.

Fresh installations without an existing CivicNet data directory do not require this step.

## Important notice

* This is an unofficial community build, not an official CivicLight binary release.
* It was compiled from the exact official upstream v3.0.8 source commit identified above.
* The executable is not code-signed, so Windows or antivirus software may display an unknown-publisher warning.
* Always keep a current backup of your wallet before upgrading.
* Use this build at your own risk.
* Replace it with an official CivicLight Windows binary if one becomes available.

## Links

* CivicLight source: https://github.com/CivicLight/CivicNet
* Official v3.0.8 tag: https://github.com/CivicLight/CivicNet/releases/tag/v3.0.8
* NitroPool: https://nitropool.net
