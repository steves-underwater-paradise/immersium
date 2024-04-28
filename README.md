# Immersium

Creativity and mobility based modpack with a focus on immersion, running on Minecraft `1.20.1` with the [Fabric Loader](https://fabricmc.net).  
The Distant Horizons build included in this modpack has serverside support, compiled from [пшш's fork](https://gitlab.com/s809/minecraft-lod-mod).

## Installation

### Client

1. Download the Prism Launcher instance (which contains the Packwiz Installer bootstrap) from the repository's [releases tab](https://github.com/steves-underwater-paradise/immersium/releases/latest)
2. Change the RAM allocation (6GB+ is recommended)
3. Run the Prism Launcher instance (files will auto download from this GitHub repository using Packwiz)
4. Head over to the [usage section](#usage) for more info

### Server

The server uses Docker Compose for easy installation. Make sure you have [Docker](https://www.docker.com) and [Docker Compose](https://docs.docker.com/compose) set up.  
Portainer is recommended, as it is the easiest installation method.

1. Copy the [Docker Compose script](docker-compose.yaml)
2. Change the RCON password
3. Change the data directory (if you're getting permission errors when running the server, make sure to create these directories if they don't exist)
4. Head over to the [multiplayer usage section](#multiplayer) for more info

## Usage

### Singleplayer

1. Download the modpack's instance, see the [`installation guide`](#installation)
2. Tweak Minecraft (`options.txt` or in game) and Distant Horizons settings to your liking (`config/DistantHorizons.toml` or in game via `Options->DH button` or `Mod Menu->Distant Horizons->Config`)
3. Load a singleplayer world

### Multiplayer

1. On the server PC, use Portainer or Docker Compose to create the Docker server from the [Docker Compose script](docker-compose.yaml) (make sure to change the RCON password and the data directory)
2. Accept the EULA (`eula.txt`)
3. Enable serverside support in Distant Horizons' config (`config/DistantHorizons.toml`)
4. Tweak the Minecraft server's properties (`server.properties`) and Distant Horizons settings to your liking (`config/DistantHorizons.toml`)
5. Start the server (the server will run on the default Minecraft port `25565`)
6. On the client PC, download the modpack's instance, see the [`installation guide`](#installation)
7. Tweak Minecraft and Distant Horizons settings to your liking (`config/DistantHorizons.toml` or in game via `Options->DH button` or `Mod Menu->Distant Horizons->Config`)
8. Join your server

### Recommended JVM arguments

Modified from Aikar's flags.

Client:

```jvm_args
-XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+UseG1GC -XX:+ParallelRefProcEnabled -XX:MaxGCPauseMillis=200 -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=8M -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=4 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:SurvivorRatio=32 -XX:MaxTenuringThreshold=1 -Dusing.aikars.flags=<https://mcflags.emc.gs> -Daikars.new.flags=true -XX:G1MixedGCCountTarget=2 -XX:+UseNUMA -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:NmethodSweepActivity=1 -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:ThreadPriorityPolicy=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:G1HeapWastePercent=18 -XX:GCTimeRatio=99 -XX:AllocatePrefetchStyle=3
```

Server:

GraalVM is used by default on the server, as specified in the [Docker Compose script](docker-compose.yaml).  
See also the [GraalVM section](#graalvm).

```jvm_args
JVM_OPTS: -XX:G1MixedGCCountTarget=2 -XX:+UseNUMA -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:NmethodSweepActivity=1 -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:ThreadPriorityPolicy=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:G1HeapWastePercent=18 -XX:GCTimeRatio=99 -XX:AllocatePrefetchStyle=3 -Dgraal.WriteableCodeCache=true
```

#### GraalVM

These JVM arguments improve performance with GraalVM.

```jvm_args
-Dgraal.WriteableCodeCache=true
```

#### Experimental

Enables JVMCI, which may improve performance over a lot of runs.

```jvm_args
-XX:+EnableJVMCI -XX:+UseJVMCICompiler
```

## Contributing

To report bugs/crashes, or give suggestions, head over to the repository's [issues tab](https://github.com/steves-underwater-paradise/immersium/issues).

### Development

1. Install [Packwiz](https://packwiz.infra.link/installation/)
2. Clone the repository
3. Run the Visual Studio Code task (or the terminal command) `packwiz serve` (the Packwiz server will now run locally on port `8080`)
4. Download the modpack's instance, see the [`installation guide`](#installation)
5. Change the pre-launch command to `$INST_JAVA -jar packwiz-installer-bootstrap.jar "http://localhost:8080/pack.toml"` (default pre-launch command is `https://github.com/steves-underwater-paradise/immersium/raw/1.20.1/pack.toml`)

## Attribution

### Loqui

[![Loqui](https://github.com/rotgruengelb/some-badges/raw/46c46090db41c2bea2b1e864c32702e6c9a2adb0/Loqui/loqui_badges/cozy_vector.svg)](https://loqui.imb11.dev)

This modpack bundles [Loqui](https://loqui.imb11.dev):

> Providing free, open-source, and community-driven translations for ALL Minecraft mods.

Loqui should take <5MiB of storage/bandwidth on first startup to download translations and upload an `en_us` translation index.
Subsequent startups shouldn't take any extra storage/bandwidth, unless the included mods have changed.

Help translate Minecraft mods: [Loqui Lokalise project](https://app.lokalise.com/public/892314276620448bc4e5c0.98736537).
