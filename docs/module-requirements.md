# Ashfall NeoForge Edition Module Requirements

The pack manifest declares module requirements instead of hard-coding every module file by hand.

```json
{
  "moduleArtifactFamily": "neoforge",
  "moduleRequirements": [
    {
      "id": "echoashfallprotocol",
      "version": "1.0.0",
      "required": true
    }
  ]
}
```

The launcher resolves the default artifact name as `<module>-<version>-neoforge.jar`. Individual requirements can override `assetName`, `path`, `sha256`, `size`, `side`, or `artifactFamily`.
