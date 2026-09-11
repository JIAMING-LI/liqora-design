# Prototype assets

All external assets are served locally. No runtime CDN calls or new npm dependency.

- `reicon.svg`: 15 Outline icons from [Reicon 1.2.4](https://registry.npmjs.org/reicon/-/reicon-1.2.4.tgz), selected from its published per-icon `O` paths without redrawing. [Reicon website](https://reicon.dev/) and [MIT license](reicon-LICENSE). Replaces the prior Feather sprite.
- `geist-latin.woff2`: the default Geist variable Latin font from [Efferd's dashboard](https://efferd.com/blocks/dashboard), verified in the page CSS; [source font asset](https://efferd.com/_next/static/media/caa3a2e1cccd8315-s.p.3b6cae6d.woff2). [Geist OFL license](geist-OFL.txt), [upstream](https://github.com/vercel/geist-font).
- `spy.png`: [official Robinhood token logo](https://cdn.robinhood.com/ncw_assets/logos/0x117cc2133c37b721f49de2a7a74833232b3b4c0c.png). Resolved from `tokenSymbol=SPY` in the [official assets API](https://api.robinhood.com/rhj/assets), documented under [Stock Token APIs](https://docs.robinhood.com/chain/stock-token-apis/). The official SPY token icon currently uses the Robinhood feather; it is intentionally distinct from inventing an SPDR mark.
- `usdg.png`: [USDG token icon](https://framerusercontent.com/images/CtEQkwH2xKYB2x8WTHX8Zja9d4.png) displayed on the [Global Dollar brand page](https://globaldollar.com/brand). Original shape and color retained.
- `robinhood.jpg`: `Robinhood Feather Symbol/Robinhood_Avatar.jpg` from the [official Robinhood Chain brand kit](https://cdn.robinhood.com/robinhood_chain/brand_assets/robinhood-chain-brand-assets-v1.zip); [brand guidelines](https://docs.robinhood.com/chain/brand-guidelines/). Used beside the chain name.
- `uniswap.svg`: `Uniswap_icon_pink.svg` from the [official Uniswap brand kit](https://github.com/Uniswap/brand-assets/raw/main/Uniswap%20Brand%20Assets.zip), linked by [Uniswap Labs](https://about.uniswap.org/). Original pink icon retained.
- `liqora-logo-v2.svg`: user-provided current brand asset, used directly without redrawing.
- `liqora-logo.png`: historical brand raster generated with the built-in Image Gen tool from the historical [v0.4 reference](../designs/03-refined-en.png). Preserved as a brand asset; no custom drawing.

The logos identify assets and platforms only. The mockup includes SPY/USDG, ETH/USDG, NVDA/USDG and CRCL/USDG demo pairs; this does not claim live integration of these pools.

## Additional demo pairs (2026-09-11)

ETH reuses `ethereum.svg`. `nvda.png` and `crcl.png` are the original Robinhood stock-token icons resolved by `tokenSymbol` from the [official assets API](https://api.robinhood.com/rhj/assets): [NVDA logo](https://cdn.robinhood.com/ncw_assets/logos/0xd0601ce157db5bdc3162bbac2a2c8af5320d9eec.png), [CRCL logo](https://cdn.robinhood.com/ncw_assets/logos/0xdf0992e440dd0be65bd8439b609d6d4366bf1cb5.png). The supplied token artwork is retained; no corporate logo is invented or substituted.

## Brand generation prompt

```text
Use case: identity-preserve logo-brand asset extraction. The attached source is the selected Liqora product mock. Recreate ONLY the exact 'liqora.' logo lockup from its top-left header as a clean high-resolution raster UI asset on a fully transparent background. Keep the source's two simple slanted rounded strokes to the left and its lowercase bold geometric sans wordmark 'liqora.' to the right. Primary graphite #24272B, secondary stroke and small dot a restrained medium neutral gray. No green. Flat monochrome treatment, no shadow, no texture, no gradients, no other words or UI. Wide 4:1 natural aspect ratio, closely framed around the logo with about 3% transparent padding. The actual in-app display will be about 122 x 31 pixels; keep strokes crisp and wordmark optically balanced at this small size. Transparent PNG. Preserve brand identity from the source, do not propose a new logo.
```

The first output contained a baked checkerboard and was rejected. Final edit prompt:

```text
Edit this exact Liqora logo asset. Keep its logo identity, wordmark letterforms, proportions, graphite and neutral gray colors identical. Replace the ENTIRE checkerboard background with one completely flat uniform solid porcelain off-white color #FAFAF8, including the spaces inside all letter counters. No transparency, no checkerboard, no patterns, no gradients, no texture or shadows. This is an app header asset on a #FAFAF8 background. Tight crop around the logo, with only 3 percent padding on all four sides; use a natural wide aspect ratio around 4:1. Keep the small gray dot and both slanted strokes. Flat high-resolution logo on the exact uniform background, no additional content.
```

## ETH Gas asset

`ethereum.svg` is the original gray ETH diamond from [ethereum.org brand assets](https://ethereum.org/assets/), downloaded from [the official SVG](https://ethereum.org/images/assets/svgs/eth-diamond-black-gray.svg) on 2026-09-10. Used at 16px beside ETH gas amounts in LP costs and activity. Original artwork/colors are retained.

## Chart badge icons

`trending-up.svg` and `trending-down.svg` are original [Lucide](https://github.com/lucide-icons/lucide/tree/main/icons) paths, also included as symbols in the local sprite. [ISC license](lucide-LICENSE). Retrieved 2026-09-10; no new runtime dependency.
