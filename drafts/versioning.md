# Versioning

**Strict semantic versioning:** https://semver.org/

**Changelog:** https://keepachangelog.com/

### Notes

- Start with 0.x.x versioning. Consider each minor as breaking, but patch as non-breaking for the 0.x.x range.
- 1.0 is attained only after a reasonable public API time elapse or usage diversity. 
- When dealing with the mono-repo model, for dependencies try as much as possible to stay on the head without
  specifically versioned deps. 
- When the above has become too tedious, or is time critical, for a short-term, version it with the git repos directly.
  Both `cargo` and `npm` accept version tagged git repos directly as their dependency.  
- Long-term strategy is also for the project owner, or if it's an abandoned project, the owner of the depending project
  to take charge to keep it rolling.
- Changelog for every project is optional, but recommended from the beginning, but mandatory starting with 
  the first breaking change. 
