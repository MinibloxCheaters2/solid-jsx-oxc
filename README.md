# solid-jsx-oxc

> [!IMPORTANT]
> M\*cOS users are garbage, change my mind.
> Whoever made this without doing cross compilation so more than M\*cOS was supported should be publicly executed.

A high-performance JSX compiler for SolidJS built with [OXC](https://oxc.rs/) and Rust.

## Features

- [x] Works on everything but M*cOS (die)
- [x] Everything else from upstream
- [x] upstream devs wrote this with ChatGPT (expect bugs if true)

## Supported Features

| Feature | Status |
|---------|--------|
| Basic elements & attributes | ✅ |
| Dynamic attributes | ✅ |
| Event delegation (`onClick`) | ✅ |
| Non-delegated events (`on:click`) | ✅ |
| Capture events (`onClickCapture`) | ✅ |
| `prop:` prefix | ✅ |
| `attr:` prefix | ✅ |
| `classList` object | ⚠️ (complex cases need more coverage) |
| `style` object | ✅ |
| Refs (variable & callback) | ✅ |
| Spread props | ✅ |
| Built-in components (`For`, `Show`, etc.) | ✅ |
| Directives (`use:`) | ✅ (DOM) / ⚠️ (SSR skipped) (I don't care about SSR) |
| SVG elements | ✅ |
| Fragments | ✅ |
| SSR mode | ✅ |
| `@once` static marker | ❌ |
| Universal mode (`generate: "universal"`) | ⚠️ (currently aliases DOM) |

## Packages

| Package | Description |
|---------|-------------|
| [solid-jsx-oxc](./packages/solid-jsx-oxc) | Core OXC-based JSX compiler |
| [vite-plugin-solid-oxc](./packages/vite-plugin-solid-oxc) | Vite plugin |
| [rolldown-plugin-solid-oxc](./packages/rolldown-plugin-solid-oxc) | Rolldown plugin |
| [babel-plugin-jsx-dom-expressions](./packages/babel-plugin-jsx-dom-expressions) | Original Babel plugin (for reference) |
| [dom-expressions](./packages/dom-expressions) | Runtime library |

## Examples

Just use an example as you would, but replacing references to the packages from here with the one from the `@wq2` group.

## Development

### Prerequisites

- [Rust](https://rustup.rs/) (latest stable)
- [Bun](https://bun.sh/) (or Node.js 18+)

### Building

```bash
# Install dependencies
bun install

# Build the native module
cd packages/solid-jsx-oxc
bun run build

# Run tests
bun run test
```

### Testing

```bash
# Run Rust tests
cd packages/solid-jsx-oxc
cargo test

# Run all tests
bun run test
```

### Publishing

The repository includes an interactive publish script that uses Bun's Terminal API for real-time output:

```bash
# Dry run (default)
bun publish-alpha.ts

# Publish with interactive confirmation
bun publish-alpha.ts --publish

# Publish automatically (no confirmation)
bun publish-alpha.ts --publish --yes

# With 2FA
bun publish-alpha.ts --publish --yes --otp 123456

# Exclude packages
bun publish-alpha.ts --exclude babel-plugin-jsx-dom-expressions --exclude dom-expressions

# Custom tag
bun publish-alpha.ts --tag beta --publish --yes

# Options
#   --tag <name>              Dist-tag (default: alpha)
#   --only <pkg>              Only publish package and deps (repeatable)
#   --exclude <pkg>           Exclude packages (repeatable)
#   --publish                 Actually publish (default: dry-run)
#   --yes                     Skip confirmation
#   --tolerate-republish      Allow republishing same version
#   --allow-dirty             Allow uncommitted changes
#   --otp <code>              2FA code
#   --list                    Show publish order and exit
```

The script generates an interactive HTML report with clickable npm package links at the end.

## License

MIT

## Related Projects

- [SolidJS](https://github.com/solidjs/solid) - A declarative JavaScript library for building user interfaces
- [OXC](https://oxc.rs/) - The JavaScript Oxidation Compiler
- [dom-expressions](https://github.com/ryansolid/dom-expressions) - Original DOM Expressions runtime
