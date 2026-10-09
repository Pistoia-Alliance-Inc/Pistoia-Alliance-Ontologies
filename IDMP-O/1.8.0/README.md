# merged

The three single file artifacts of IDMP-O v1.8.0, each with one ontology header:

- `IdentificationOfMedicinalProducts-Core.ttl`: the released modules and the extracts of the external terms they
  use, merged. Of the Commons modules it holds the terms IDMP-O uses with their datatype definitions. No
  `owl:imports`, Pellet finds it consistent. The IDMP-O ontology with only the external terms it needs
- `IdentificationOfMedicinalProducts-Full.ttl`: the released modules with every external module of their closure
  inlined. One self contained file with the complete external axiomatisation
- `IdentificationOfMedicinalProducts-Examples.ttl`: the examples, with `owl:imports` of the Core artifact

The repository keeps the same files in its release folder, for example `1.8.0/`.
