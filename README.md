# IUCN Red List of Threatened Species

_This dataset does not contain any data since [IUCN Red List terms and conditions](https://www.iucnredlist.org/terms/terms-of-use#4.%20No%20Reposting%20or%20Redistribution) do not allow open publication of their data on other platforms without permission. Read the [etl readme](etl/README.md) for more information on how to build this dataset._

From [the IUCN Red list website](https://www.iucnredlist.org/about/background-history):

Established in 1964, the International Union for Conservation of Nature’s Red List of Threatened Species has evolved to become the world’s most comprehensive information source on the global extinction risk status of animal, fungus and plant species.

The IUCN Red List is a critical indicator of the health of the world’s biodiversity. Far more than a list of species and their status, it is a powerful tool to inform and catalyse action for biodiversity conservation and policy change, critical to protecting the natural resources we need to survive. It provides information about range, population size, habitat and ecology, use and/or trade, threats, and conservation actions that will help inform necessary conservation decisions.

## Versions
 - 0.0.1 Start with `species` and `assessment` entity domains 

## Data source

All data comes from the IUCN Red List website. The website offers data in several ways which are documented in the [etl/README.md](etl/README.md) file.

## Data model

[This wikipedia module docs](https://en.wikipedia.org/wiki/Module:Iucn) helped understanding the Red List's data model.

Each species has an `taxonId` (or `internalTaxonId`). A species is described in an assessment, identified by a `assessmentId`. Each time a species gets a new assessment, a new assessmentId is generated and linked to the species. See for example the Giant Panda [currently](https://www.iucnredlist.org/species/712/121745669) (121745669) and a [previous assessment](https://www.iucnredlist.org/species/712/13069561) (13069561).

A `taxonId` can be removed from the list. For example when a previous species is split in two separate species. Both may get a new `taxonId` and the old one is removed. The house sparrow (149100) was split into a new house sparrow (103818789) and Italian sparrow (103819014).

IUCN Red List is a list of species. IUCN seems to use the term taxon as a synonym for species (e.g. in `taxonId`). It's not exactly: species is one of many ranks of taxons ([source](https://biologydictionary.net/taxonomy/)). We chose to use `species` over `taxon` as the entity domain. It's a more specific name for its content.
