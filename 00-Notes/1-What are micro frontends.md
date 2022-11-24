

### What are micro frontends?
The micro frontends architecture is all about being able to work in small autonomous teams that have everything they need to create value for the customer.
- It is not a concrete technology.
- It is an organizational and architectural approach 
- Divides the application into vertical slices.
  - Each slice is built from the database to the user interface and run by a dedicated team.
  - The different team frontends integrate in the customer’s browser to form the final page. 
- The most significant difference between micro frontends and other architectures is **team structure.**
- What makes the micro frontends approach different from other architectures. **It’s the way we think about and build features.**
*Teams have end-to-end responsibility for a given functionality.*

### Three main reasons why companies adopt a micro frontends architecture:

- **A team includes all skills needed to develop a feature.**
*No coordination between separate frontend and backend teams is required.* 
- **Each team owns its complete stack from frontend to database.**
*Teams can decide to update or switch their frontend technology independently.*
- **Every team ships their features directly to the customer.**
*No pure API teams or operation teams exist.*



![The big picture](/Images/TheBigPicture.png)


### Systems and teams
- One system is owned by one team.
- Each system is autonomous.
*which means it can function even when the neighboring systems are down.*
- Every team should have a descriptive name and a clear user-focused mission.
- Cross-functional Teams are formed around a customer need and not based on technologies like frontend and backend.
- Teams can choose the technology stack that fits best for the job at hand.
- The applications are loosely coupled and only integrate in the frontend (e.g.,
via links).

![Specialist vs cross-functional Teams](/Images/SpecialistVSCrossFunctionalTeams.png)

### Frontend integration

> We can think of **fragments** as embeddable mini applications that are isolated (self-contained) from the rest of the page.

![Frontend integration](/Images/FrontendIntegration.png)

- a set of techniques you use to assemble the user interfaces (pages and fragments) of the teams into an integrated application. 
- Depending on your architectural choices, you have different options to solve these categories.
- We can group these techniques into three categories:
  ###### 1. ROUTING AND PAGE TRANSITIONS
    - Integration on page level
    You can implement this by having a `shared application shell` or using a `meta-framework like single-spa`. 
  ###### 2. COMPOSITION
    - The process of getting the fragments and putting them in the right slots
      - Server-side composition (like SSI,ESI,Tailor or Podium)
      - Client-side composition (like iframes, Ajax, or Web Components)
  ###### 3. COMMUNICATION
    - How does a page trigger the update of an included fragment..
  

### Shared topics
  - To ensure a good end result and avoid redundant work, it’s important to address topics like web performance, design systems, and knowledge sharing from the start.
  - Having a shared `design system` helps to achieve a consistent look and feel across all team frontends.
  - The micro frontends model typically comes with more code for the browser. It’s vital to address web `performance` from the start.

### What problems do micro frontends solve?
- **Optimize for feature development (increase development speed) by**
  1. communication inside a team is much faster and less formal. 
  2. Iteration is quicker—no waiting for other teams.
  3. no discussion about prioritization.
- **No more frontend monolith**
  Compared to a front- end monolith, building and maintaining a smaller frontend has benefits. A micro frontend
  1. Is independently `deployable`.
  2. Isolates the `risk of failure` to a smaller area.
  3. Is narrower in scope and thereby `easier to understand`.
  4. Has a smaller codebase that can help when you want to `refactor` or replace it.
  5. Is more `predictable` because it does not share state with other systems.

- **Be able to keep changing**
  - Being able to adopt a new technology when it makes sense is an essential asset for your teams and your company. `(Dealing with LEGACY & LOCAL DECISION MAKING)`

- **The benefits of independence**
  - Pages and fragments are `SELF-CONTAINED`.
  - Share as little as possible to enable faster feature development, `SHARED NOTHING`.


### The downsides of micro frontends
  1. Redundancy
  2. Consistency
  3. Heterogeneity
  4. More frontend code
      it’s extra essential to have an eye on web performance from the start.


### When do micro frontends make sense?
  1. Good for medium-to-large projects
     - Micro frontends architecture is a technique that makes scaling projects easier
     - When the team exceeds 10 people, it’s worthwhile considering a team split
  2. Works best on the web
      - Composing and replacing functionality on the fly is not possible for Native applications
  3. Productivity versus overhead
      - SETUP
        - need to find good team boundaries
        - need to establish common rules
      - ORGANIZATIONAL COMPLEXITY
        - Running a distributed system adds its complexity on top.
        - will probably need an extra shared service for your frontend integration
        - 
### Where micro frontends are not a great fit
  1. If you only have a handful of developers and communication is not issue


> ***Coupling*** describes how much one team needs to know about the other team’s system to make the integration work.