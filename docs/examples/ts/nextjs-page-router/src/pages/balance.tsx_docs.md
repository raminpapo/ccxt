# Documentation: examples/ts/nextjs-page-router/src/pages/balance.tsx

## File Metadata

- **Path**: `examples/ts/nextjs-page-router/src/pages/balance.tsx`
- **Size**: 1,348 bytes
- **Lines**: 47
- **Type**: Unknown
- **Extension**: .tsx


## Original Source Code

```
import ccxt, { Balances } from 'ccxt'

// This is for showcase purposes in prod move this to environment variable like process.env.BINANCEUSDM_API_KEY
const apiKey = ""
const secret = ""

export async function getServerSideProps () {
  const exchange = new ccxt.kraken({ apiKey, secret })
  const balances = await exchange.fetchBalance()
  // remove undefined values to prevent serializing error
  Object.keys(balances).forEach(key => balances[key] === undefined && delete balances[key])
  return {
    props: {
      balances,
    },
  }
}

export default function Balance({balances}: {balances: Balances}) {
  return (
    <main className={`flex min-h-screen flex-col items-center justify-between p-24`}>
      <table>
        <thead>
          <tr>
            <th>Currency</th>
            <th>Free</th>
            <th>Used</th>
            <th>Total</th>
          </tr>
        </thead>
        <tbody>
          {Object.keys(balances).map((currency: string) => (
            balances[currency].free !== undefined && (
              <tr key={currency}>
                <td>{currency}</td>
                <td>{balances[currency].free}</td>
                <td>{balances[currency].used}</td>
                <td>{balances[currency].total}</td>
              </tr>
            )
          ))}
        </tbody>
      </table>
    </main>
  )
}

```

## High-Level Overview

This is a Unknown file located at `examples/ts/nextjs-page-router/src/pages/balance.tsx`.

**Functions defined**: getServerSideProps, Balance

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 41
- Comment lines: 2
- Blank lines: 4

### Main Components

**Functions** (2):
- `Balance()`
- `getServerSideProps()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `ccxt` (imported)



## Testing & Execution

**To execute this Unknown file:**

