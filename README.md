# edicts

# Architecture

## Naming Convention

Code smells:
- `Misc`
- `Util`
- `Helper`
- `New`
- `Next`
- `Common`

**"Miscellanious", "Utilities" and "Common" tend to be poorly defined collections of unrelated logic.** These classes, modules or folders are a dumping ground for lazy engineers - _or_ a symptom of poor architecture. 

**"Helper" methods, modules and classes also regularly cause tight coupling**; the same behaviour being reused in multiple places throughout a solution.

Solve by considering each discrete component and moving it alongside the code it uses. Not everything has to be DRY, however if you find yourself replicating the same code many times consider moving your domain boundaries.

For example a `Utils` folder contains a `JsonSiteConfigFileReader` which loads and parses a JSON file to a strongly-typed configuration object. If this is used only once within your code inside a piece of domain logic (like `SiteLayoutFactory`, move the config reader alongside this code. If this is used many times, consider "Configuration" to be a first-order concern and restructure the file reader to within a `Configuration` namespace.

**"New" and "Next" age rapidly**. Future engineers browsing a codebase may mistakenly assume that the "NewCaptcha" module is current, even though it was superseded 3 years ago by a sensibly named "CaptchaService".
