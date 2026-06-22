# OnVote

OnVote is a mini end-to-end Stellar + Soroban dApp: a multi-wallet polling app backed by a deployed Soroban smart contract on Stellar Testnet, with real-time contract event sync, transaction progress feedback, basic caching, and a small automated test suite.

## Level 3 Submission Checklist (fill before submitting)

- Live demo link: https://online-live-poll.vercel.app/
- Demo video (1 minute) link: https://drive.google.com/file/d/1SRK_eF2qJyIfuN-KMlgzCpeacAeYJ23t/view?usp=sharing
- Test output screenshot (3+ passing tests): ✅ (see below)
- Public GitHub repo link: `https://github.com/rohit-012005/Online-Live-Poll.git`
- 3+ meaningful commits for Level 3: ✅


## Submission Overview


This project demonstrates:

- Multi-wallet integration with `StellarWalletsKit`
- Smart contract deployment on Stellar Testnet
- Contract reads and writes from the frontend
- Real-time event polling and state synchronization
- Visible transaction lifecycle feedback
- Wallet error handling for missing wallet, rejected request, and insufficient balance
- Loading states and progress indicators during reads/writes
- Basic caching of recently loaded poll data in `localStorage`
- Automated tests for core helper logic

## Key Features

- Connect with supported Stellar wallets including Freighter, xBull, Albedo, Rabet, Lobstr, Hana, Hot Wallet, and Klever
- Create, vote on, close, and delete polls through frontend contract calls
- Browse contract data in read-only mode even without a connected wallet
- See transaction phases in the UI: `preparing`, `awaiting-signature`, `pending`, `success`, and `error`
- Refresh poll state automatically from recent on-chain contract events

## Screenshots

<table width="100%">
  <tr>
    <td align="center" width="50%">
      <strong>🏠 Home Page</strong><br/><br/>
      <img width="2848" height="1572" alt="screenshot_visible_2026-04-30_17-06-27" src="https://github.com/user-attachments/assets/a1c8793f-aae9-44ed-803f-04a436d5fedd" />
    </td>
    <td align="center" width="50%">
      <strong>📝 Create Poll</strong><br/><br/>
   <img width="2848" height="1572" alt="screenshot_visible_2026-04-30_17-14-55" src="https://github.com/user-attachments/assets/1e63b7cd-6ce2-4ef4-a07b-1ecae1771c22" />
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <strong>🗳️ Voting</strong><br/><br/>
   <img width="2848" height="1572" alt="screenshot_visible_2026-04-30_17-17-31" src="https://github.com/user-attachments/assets/b962d4ce-2b4e-42e4-9f8e-29774f78538d" />
    </td>
    <td align="center" width="50%">
      <strong>✅ CI/CD Results</strong><br/><br/>
    <img width="1426" height="830" alt="image" src="https://github.com/user-attachments/assets/ae849647-7b8a-412e-92b8-0fb1532a5c4a" />
    </td>
  </tr>
</table>

## Mobile responsive screenshots

Below is a mobile view screenshot demonstrating the responsive layout on narrow screens. Replace the placeholder with a real phone-sized screenshot captured from the dev tools or a device.

<div align="center">
<img width="389" height="700" alt="2026-04-30_18-25-47" src="https://github.com/user-attachments/assets/23b9e24d-e978-4e81-9db3-dc2976486253" />

</div>


## Deployed Contract

- Network: `Stellar Testnet`
- Contract address: `CCI25FHNRMJU2TLWL2LFZIBLASRYV4ROE5L7AGNEIXTQDLUT4V7P6IG3`
- Contract explorer: https://stellar.expert/explorer/testnet/contract/CCI25FHNRMJU2TLWL2LFZIBLASRYV4ROE5L7AGNEIXTQDLUT4V7P6IG3

## Verifiable Contract Call

- Deploy tx hash: `5b521528af7541b5eaf1b89fb5b2a0db2343ac59036e489d2703f075e910aff0`
- Stellar Expert link: https://stellar.expert/explorer/testnet/tx/5b521528af7541b5eaf1b89fb5b2a0db2343ac59036e489d2703f075e910aff0
- Sample `create_poll` tx hash: `511a6899317357d96cf0dbcc9c84f65b697ada58206863346dcfcab14a186b77`
- Stellar Expert link: https://stellar.expert/explorer/testnet/tx/511a6899317357d96cf0dbcc9c84f65b697ada58206863346dcfcab14a186b77

## Live Demo

https://online-live-poll.vercel.app/

## Setup

Run all commands from the `onvote` project directory.

1. Install dependencies:

```bash
npm install
```

2. Build the Soroban contract:

```bash
npm run contract:build
```

3. Sync the compiled contract WASM into the frontend (used to load the contract spec/ABI at runtime):

```bash
npm run wasm:sync
```

4. Optionally create a local env file:

```powershell
Copy-Item .env.example .env.local
```

5. Start the frontend:

```bash
npm run dev
```

6. Build for production:

```bash
npm run build
```

## Tests

Run the automated tests:

```bash
npm test
```

For submission, include a screenshot of the terminal output showing **3+ tests passing**.

## Environment Variables

```env
VITE_STELLAR_RPC_URL=https://soroban-testnet.stellar.org
VITE_STELLAR_NETWORK_PASSPHRASE=Test SDF Network ; September 2015
VITE_STELLAR_CONTRACT_ID=CCI25FHNRMJU2TLWL2LFZIBLASRYV4ROE5L7AGNEIXTQDLUT4V7P6IG3
VITE_STELLAR_READ_ACCOUNT=
VITE_STELLAR_EXPLORER_URL=https://stellar.expert/explorer/testnet
VITE_POLL_CONTRACT_WASM_URL=/contracts/poll_contract.wasm
```

## Testnet Notes

- A connected wallet must be funded on Stellar Testnet before it can send contract transactions
- If a wallet has not been created on Testnet yet, fund it with Friendbot first and then retry
- The app can still read poll data without a funded wallet by using a temporary read account

## Scripts

- `npm run dev` starts the frontend
- `npm run build` creates a production build
- `npm run lint` runs ESLint
- `npm test` runs the Node.js test suite
- `npm run contract:build` builds the Soroban contract
- `npm run wasm:sync` copies the compiled WASM into `public/contracts/` for the frontend to load the contract spec
- `npm run contract:deploy` uploads and deploys the contract to testnet

## Deploy (Vercel / Netlify)

This is a standard Vite build.

- Node.js: use Node `^20.19.0` or `>=22.12.0` (required by Vite 8)
- Build command: `npm run build`
- Output directory: `dist`
- Set the env vars from the section above (at minimum `VITE_STELLAR_CONTRACT_ID` if you deploy a new contract)

## Demo Video (1 minute)

https://drive.google.com/file/d/1SRK_eF2qJyIfuN-KMlgzCpeacAeYJ23t/view?usp=sharing

Walkthrough:

1. Open the deployed site and show the “Read from contract” panel updating.
2. Connect a wallet (Freighter or any supported wallet).
3. Create a poll (show “awaiting-signature” → “pending” → “success”).
4. Vote on the poll and show the event feed / vote count updating.
5. Open the contract/tx on Stellar Expert via the links in the UI.

## Project Structure

- `src/` contains the React frontend
- `src/lib/stellar.js` contains wallet, RPC, contract, and event helpers
- `src/lib/pollCache.js` contains the basic poll cache helpers
- `src/lib/pollLogic.js` contains pure helper functions used by the UI
- `poll_contract/` contains the Soroban contract
- `scripts/` contains deployment helpers
- `tests/` contains the automated test suite

## Additional Docs

- Frontend guide: [FRONTEND.md](./FRONTEND.md)
- Contract guide: [poll_contract/README.md](./poll_contract/README.md)

## Submission Notes

- GitHub repository: `https://github.com/Sagar522290/livepoll.git`
- The project includes multiple meaningful commits in git history
- The contract is deployed on testnet and called from the frontend
- Real-time event integration and visible transaction status are implemented
- Before final submission, update the checklist at the top with your live demo link, demo video link, and test screenshot
