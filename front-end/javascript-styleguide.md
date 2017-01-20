# JavaScript Style Guide


## Table of contents

1.  [Whitespace](#whitespace)
2.  [Formatting](#formatting)
3.  [Naming Conventions](#naming-conventions)
4.  [Comments](#comments)
5.  [File Organization](#organization)
6.  [Variables](#variables)
7.  [Notes on performance](#performance)
8.  [Sources](#sources)


<a name="whitespace"></a>
## Whitespace


<a name="formatting"></a>
## Formatting


<a name="naming-conventions"></a>
## Naming Conventions


<a name="comments"></a>
## Comments


<a name="organization"></a>
## File Organization


<a name="variables"></a>
## Variables


<a name="performance"></a>
## Notes on performance
- use chrome DevTools [intro to the timeline](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/timeline-tool)
- caching selectors
- removing reference to detached elements
- adding/removing event listeners
- avoid DOM read/write loops
- no unused variables
- throttle and debounce
- stores measurements and only measure again after a debounced resize event
  - each measurement forces style recalculation which forces layout


<a name="sources"></a>
## Sources
