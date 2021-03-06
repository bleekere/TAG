# 2.1 (December 2018)

### New features:

- [AlexandriaStep for use in Calabash](https://huygensing.github.io/TAG/TAGML/CALABASH-README)
- [TAGML Syntax highlighting in Sublime Text 3](https://huygensing.github.io/tagml-sublime-syntax/)

#### [New/Changed commands for the command-line app](https://huygensing.github.io/alexandria/commands)
- about
- add
- commit
- export-dot
- export-svg
- export-png
- export-xml 

### Bugfixes:

- The first markup is now always the root markup for the default layer, even if new layers are defined on that markup.
- This means that this first markup tag must correspond with the last closing markup tag, and suspending/resuming of this markup is not allowed.

### Still to realize:

- Whitespace: "In TAGML Whitespace is insignificant unless specified otherwise"
- Data typing (RichText)
- Comments: store and export
- Namespaces: export
- Linking elements

# 2.0 (July 2018)

### TAGML Syntax elements realized in this release:

- Encoding text: escaping
- Adding markup
- Adding annotations
- Milestones
- Comments (parsing only)
- Namespaces (parsing only)
- Data typing (String, Number, Boolean, List, Nested annotation)
- Encoding non-linearity
- Overlapping and self-overlapping markup
- Discontinuity
