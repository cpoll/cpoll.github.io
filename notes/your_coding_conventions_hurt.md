# Your coding conventions are hurting you 
[http://www.carlopescio.com/2011/04/your-coding-conventions-are-hurting-you.html](http://www.carlopescio.com/2011/04/your-coding-conventions-are-hurting-you.html)
AKA the "object thinker" article

- A lot of architecture is like doric columns painted on a building. Looks OO and flexible from afar, but that's a veneer on procedural thinking.
- Urges reading 'The Early History of Smalltalk'
- "The basic principal of recursive design is to make the parts have the same power as the whole." For the first time I thought of the whole as the entire computer and wondered why anyone would want to divide it up into weaker things called data structures and procedures. Why not divide it up into little computers, as time sharing was starting to? But not in dozens. Why not thousands of them, each simulating a useful structure?  - The Early History of Smalltalk
- Objects should be smart; hide data, expose behaviour. Methods are goals: Something you want to happen, unconcerned about implementation.
- To the contrary, most modern 'OO' programming is just old-style with fancier constructs; just "assignment-style" operations done with procedures.
- OO concepts are more important to learn than OO mechanics.
- Good naming is important: Thinking of a good name promotes discovery, if you can't think of one you might not know enough about the problem/solution domains. The metaphor might be wrong, the abstraction misleading.
    - Class/interface names should have more time spent on them. If you can't think of one, name your functions first, and try to figure out what's keeping them together (maybe they don't belong together).
- Watch out for procedural fake-OO: -er, -able, -Object, I-. [This is an old theme, I've read this elsewhere]
- Managers are bad, they usually just deal with data structures. If the Manager is the smart procedure, tie it to the structures.
- Helper classes aren't great, they just weaken encapsulation. The proper OO thing to do is find the correct cohesive concepts. 
- Don't call a nail 'hammerable'
- Bad OO is 'Runnable' strategy pattern, (or IRunnable) for threading. Better is 'Activity', because Thread depends on Activity, but Activity does not depend on Thread. 
- .NET Marshalling is an implementation detail, we should talk about appdomain affinities: MarshalByRefObject -> AppDomainAffine
- I- is a trap: IDollar is worse than Currency, the former is the typical naive approach of slapping I onto the concrete class.
    - IList -> RandomAccessContainer (and while we're at it, a List is a random and sequential access container, so ArrayList is nice)
    - IEnumerable -> Sequence
    - IValidatable (which allows invalidation) -> Constraint
