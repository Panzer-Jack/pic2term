# img-ascii-term
Convert images to colorful ASCII art for terminal display.

## Features
- Converts images to ASCII strings you can print in any terminal
- Truecolor output via `chalk` with an option to disable color
- Maintains aspect ratio with a tunable output width and custom charset
- Supports common formats: jpg, jpeg, png, gif, bmp, webp
- Ships as an ESM package; works in Node.js environments that support `import`

## Requirements
- Node.js 22 or newer
- `pnpm` for local development (enforced via `preinstall`)

## Installation
```bash
pnpm add img-ascii-term
```

## Quick start
```typescript
import { convertImageToAscii } from 'img-ascii-term'

const ascii = await convertImageToAscii('./logo.png', {
	width: 120,
	colored: true,
	charset: ' .:-=+*#%@',
})

console.log(ascii)
```

## API
### `convertImageToAscii(imagePath: string, options?: ConvertImageOptions): Promise<string>`
Converts an image file into an ASCII art string. Throws if the file does not exist or the format is unsupported.

#### `ConvertImageOptions`
- `width` (number): Output character width. Default `80`.
- `colored` (boolean): Enable truecolor output. Default `true`.
- `charset` (string): Characters ordered from light to dark. Default `' .:-=+*#%@'`.

## Playground
Use the included sample to preview output in your terminal:
```bash
pnpm install
pnpm start
```
This builds the package and runs [playground/index.js](playground/index.js), which converts `playground/ciallo.png`. Adjust the image path or options there to experiment.

## Development
- `pnpm dev` — build in watch mode
- `pnpm build` — produce ESM output in `dist`
- `pnpm typecheck` — run TypeScript without emitting
- `pnpm start` — build then run the playground example

## Notes
- Output looks best in terminals that support 24-bit color; set `colored: false` if you need monochrome.
- The package uses `canvas` under the hood; ensure the optional native dependencies for your platform are available if `pnpm install` reports issues.
