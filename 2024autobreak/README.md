# Contents 

This archive contains Cadnano source files, scaffold sequences, and staples for all designs in the paper:
- Cadnano designs with "_original" and "_redesign" suffixes correspond to the unoptimized and optimized designs described in the paper.
- Cadnano designs with the "_prebroken" suffix do not have any staple breaks applied by the autobreak algorithm.
- The "staples" subfolder contains "csv" and "xlsx" versions of the staple sequences for each design. The sequence contents are identical, but the xlsx files have stylized formatting to show the staple colors that correspond to the heatmap and thermodynamic plots in the paper.


## Cadnano design files

- Cadnano source files have a `.json` extension and are named according to the manuscript figure where the design first appears. 
- Cadnano designs with `_original` and `_redesign` suffixes correspond to the unoptimized and optimized designs described in the paper. 
- Cadnano designs with the `_prebroken` suffix do not have any staple breaks applied by the autobreak algorithm. 

## Staple sequences

All staple sequences can be found in `staple_sequences.xlsx`. 

The xlsx files have stylized formatting to show the staple colors that correspond to the heatmap and thermodynamic plots in the paper. 

## Design names and scaffold pairings

| Design name                | Scaffold file |
|----------------------------|---------------|
| Fig3A_10x10_original.json  | p7560.txt     |
| Fig3A_10x10_prebroken.json | p7560.txt     |
| Fig3A_10x10_redesign.json  | p7560.txt     |
| Fig3B_4x16_original.json   | p8064.txt     |
| Fig3B_4x16_prebroken.json  | p8064.txt     |
| Fig3B_4x16_redesign.json   | p8064.txt     |
| Fig3C_8x8_original.json    | p8064.txt     |
| Fig3C_8x8_prebroken.json   | p8064.txt     |
| Fig3C_8x8_redesign.json    | p8064.txt     |
| Fig3D_16x4_redesign.json   | p8064.txt     |
| Fig3D_16x4_original.json   | p8064.txt     |
| Fig3D_16x4_prebroken.json  | p8064.txt     |
| FigS13_4x16_stag.json      | p8064.txt     |

## Scaffold sequence files

|Filename  |  GenBank ID  |	Usage              |
|----------|--------------|--------------------|
|p7560.txt | FJ565687.1   |	Fig3A_10×10 blocks |
|p8064.txt | FJ565688.1   | All other designs  |


## Reproducing the autobreak analysis

After installing the pyOrigamiBreak package in a Python virtual environment, the following shell commands can be used to regenerate the autobreak score reports. 

    autobreak -readonly -seq p7560 -i Fig3A_10x10_original.json
    autobreak -readonly -seq p7560 -i Fig3A_10x10_redesign.json
    autobreak -readonly -seq p8064 -i Fig3B_4x16_original.json
    autobreak -readonly -seq p8064 -i Fig3B_4x16_redesign.json
    autobreak -readonly -seq p8064 -i Fig3C_8x8_original.json
    autobreak -readonly -seq p8064 -i Fig3C_8x8_redesign.json
    autobreak -readonly -seq p8064 -i Fig3D_16x4_redesign.json
    autobreak -readonly -seq p8064 -i Fig3D_16x4_original.json
    autobreak -readonly -seq p8064 -i FigS13_4x16_stag.json

Additionally, files with the `_prebroken` suffix do not have any staple breaks applied by the autobreak algorithm, and therefore can be used to generate your own redesigned block versions: 

    autobreak -seq p7560 -i Fig3A_10x10_prebroken.json
    autobreak -seq p8064 -i Fig3B_4x16_prebroken.json
    autobreak -seq p8064 -i Fig3C_8x8_prebroken.json
    autobreak -seq p8064 -i Fig3D_16x4_prebroken.json

Note that due to randomized starting conditions, the scores that you observe using these commands may differ slightly from the scores that we achieved. However, running the algorithm in "readonly" mode on the actual designs we used should generate identical scores.
