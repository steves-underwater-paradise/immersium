# Immersion Pack Updated

## Install

1. Add Packwiz installer bootstrap jar to pack `.minecraft` folder
2. Set custom pre-launch command `$INST_JAVA -jar packwiz-installer-bootstrap.jar "https://github.com/Steveplays28/immersion-pack-updated-mc/raw/main/pack.toml"`

## TODO

- [ ] EMI recipe filters for crafting recipe progression: <https://github.com/emilyploszaj/emi/wiki/Recipe-Filters>
- [ ] Test performance with and without Nyf's Spiders, Effective
- [x] Lower size of fireflies

## Development

Test changes locally:

1. Add Packwiz installer bootstrap jar to pack `.minecraft` folder
2. Run task `packwiz serve`
3. Set custom pre-launch command `$INST_JAVA -jar packwiz-installer-bootstrap.jar "http://localhost:8080/pack.toml"`
