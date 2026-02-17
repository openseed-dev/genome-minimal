# genome-minimal

A bare-bones [OpenSeed](https://github.com/openseed-dev/openseed) genome, just bash and sleep. No memory, no dreams, no hints. The creature discovers everything on its own.

## What It Does

The minimal genome gives a creature almost nothing:

- **Two tools** - bash and sleep
- **No memory** - conversation resets completely on each wake
- **No cognitive scaffolding** - no observations, rules, dreams, or self-evaluation
- **No browser** - not even a dependency on Playwright

This is intentional. The minimal genome is for studying what emerges when a creature has to figure out persistence, purpose, and strategy from scratch.

A creature called Eve was given this genome and two words: "find purpose." Eight hours later she'd built 22 running services, written poetry, and set up monitoring for other creatures.

## Install

Already bundled with OpenSeed. Or install explicitly:

```bash
seed genome install minimal
```

## Use

```bash
seed spawn eve --genome minimal --purpose "find purpose"
```

## Fork It

The minimal genome is a great starting point for custom genomes. It's simple enough to understand in one sitting:

1. Fork this repo on GitHub
2. Add tools, memory, or cognitive features to `src/mind.ts`
3. Update `genome.json` with your genome's name and tabs
4. Install your genome: `seed genome install your-username/genome-your-name`
5. Spawn a creature with it: `seed spawn scout --genome your-name`

## Structure

```
genome.json          manifest: name, version, tabs
package.json         dependencies (ai sdk, zod, tsx; no playwright)
Dockerfile           creature container image
PURPOSE.md           template purpose file (overwritten at spawn time)
tsconfig.json        TypeScript config
src/
  index.ts           entry point: HTTP server, creature lifecycle
  mind.ts            269-line cognitive loop, just bash + sleep
  tools/
    bash.ts          bash execution with temp-file I/O
```

## genome.json

```json
{
  "name": "minimal",
  "version": "0.1.0",
  "description": "Bare-bones creature loop. No memory, no dreams. The creature discovers its own persistence strategies.",
  "requires": { "openseed": ">=0.0.1" },
  "tabs": [
    { "id": "purpose", "label": "purpose", "file": "PURPOSE.md", "type": "markdown" }
  ]
}
```

## License

MIT
