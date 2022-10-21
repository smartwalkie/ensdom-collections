
# ENS Collections

ENS Collections are categories of ENS names based on specific patterns or predefined lists. This repository is an effort towards bringing all collections together into one place and standardizing their definition in order to facilitate consistent integrations across platforms and marketplaces. This is a fork from https://github.com/Zimtente/ens-collections 

This repo is maintained by: @ensbuy and is used to display clubs on sales.ensdom.com.

### Make your own club
We want to allow the ENS community to have maximum flexibility in their clubs. We will allow any pull request to make a new club as long as it is not a duplicate or superset of several clubs. Once a club is created by you, any further edits will also be merged without questions. 

### Club Conflicts
If someone else wants to change names in a club, they should request a conversation from the creator and we will allow the merge. 
If a club is no longer maintained or the creator is not contactable, after 30 days, we will pass on the ownership to the nex requested party. 

### Easy way to submit
Non technical users have an easy way to submit their clubs here: https://docs.google.com/forms/d/e/1FAIpQLSfmu9U3xJZSxuwysnLD9dTkwI1Qb3-LC7Dx4IJwK-Kv9rV97w/viewform

### Metadata
The metadata for all collections in `ens-collections.json`:

- **`name`: collection name, e.g. "10K Club"**
- **`slug`: short, lowercase, url-friendly abbreviation (use hyphens instead of spaces), e.g. "10k-club"**
- **`description`: one sentence description**
- `twitter`: twitter username 
- `website`: full website url
- `chat`: link for group chat, e.g. discord/telegram
- `logo`: logo file, use slug for filename, e.g. "three-letters.png"
- **`csv`: array of csv files, use slug for filename, e.g. ["three-letters.csv"]**

<sub>**bold** = required field.</sub>


### CSV files
The .csv should include all names in the collection in ascending alphanumeric order. There are two columns: name and token ID. The names should not include the .eth extension and should be normalized using [standard ENS normalization](https://docs.ens.domains/contract-api-reference/name-processing#normalising-names). New collections can be submitted without token IDs, or use the provided script to generate them.

```
name,token
vitalik,79233663829379634837589865448569342784712482819484549289560981379859480642508
ens,42033647921836720708986079437023664695436352815832009766988496528855301124570
0001,38764329101403256878217503524140705778209985981144907919668889447405219871633
```

 
&nbsp;
&nbsp;
  

# Contributing

Please create issues or pull requests to contribute to this repo.

### Proposing a New Collection
Here is a quick checklist when submitting a new collection:

- The collection must be significantly different from any existing collection. 
- Provide all the required metadata fields (see above).
- CSVs should be properly formatted and use the slug for filename. New collections can be submitted without token IDs.
- (Optional) Logo files should be PNG with square dimensions that work with a circular crop (like Twitter). Logo files should be at least 500x500px, and no more than 1200x1200px. Logo files should use the slug for filename.


### Example Collection Proposal:
**Metadata content:**
```
{
  "name": "10k Club",
  "slug": "10k-club"
  "description": "Names with 4 digits, 0000-9999.",
  "twitter": "10kClubOfficial",
  "website": "https://10kClub.com",
  "chat": "https://discord.gg/aUemBKUuZ5",
  "logo": "10k-club.png",
  "csv": ["10k-club.csv"]
}
```

**.CSV content:**
```
name,token
0000,105307555225596823162770746791279321249474694422393704130067750948958748271609
0001,38764329101403256878217503524140705778209985981144907919668889447405219871633
0002,37929174533718175565910670676525701091954781139941253617179119590462796771323
...
```

### Adding or Removing Names from a Collection

To modify an existing collection, please create an issue or pull request and provide:

- Explanation why the item should be added/removed from a collection
- Collection Name
- Name of the item
- (Optional) Token ID of the item



&nbsp;
&nbsp;


# Utils

**Install**

`npm install`

### Generate Token IDs from Names

This takes any CSV file where the first column is the ENS name. The name will be normalized (.eth removed) and the token ID will be added as the second column in outfile.csv. Use this outfile for the collection CSV. It can replace the input file as well.

`npm run get-tokens utils/example-names.csv outfile.csv`


**How to convert a name into a token ID:**  
https://docs.ens.domains/dapp-developer-guide/ens-as-nft

### Verify All Lists and Logos

This verifies that all CSV files and logo files that are specified in `ens-collections.json` exist. 

`npm run verify-collections`
