### UIs Integration via links & iframes
-  Integrate UIs from different teams via **links** and **iframes** from a micro frontends perspective introduce **minimal coupling** between the teams
- there is no`gold standard` or `best integration technique.` **It’s all about making the right trade-offs for your use case**.


### Getting started
Teams start setting up their applications, deployment processes
1. ***Choosing Technology***
    - Being able to choose the technology that’s best for the job is one of the benefits of micro frontends. 
    It takes into account that not all tasks are the same. Building a high-traffic landing page has different requirements than developing an interactive tractor configurator.
    - When teams use similar stacks, it’s easier to exchange best practices, get help, or move developers between teams also save up-front costs because you could share the basic application setup
2. ***Independent Deploys***
![Independent Deploys](/Images/IndependentDeploys.png)
   

### used Tools
  - ***@microfrontends/serve***
  a modified version of the great zeit/serve server


### Page transition via links
- ***Data ownership***
   - decide which team should owns the base data and this team should build tools that enable others to add new or update existing ones.

- ***Contract between the teams***
  - `URL` will be the contract between the teams. 
  - Teams that own a page `publish` their `URL patterns`.
  - The others can `use` the patterns to create a link.

    > Each team bring their CSS files, Since micro frontends is all about decoupling and maintaining team autonomy, we have to be careful—even with styling.
- ***Dealing with changing URLs***
  - **You can `manually` notify all other teams**
   But when the number of teams and URLs grows, you’ll want to `automate` this process.
  - **A team that wants to change its URL could provide an `HTTP redirect` to solve this.** 
  However, letting your end users jump through redirect chains is `not always optimal`.
  - A more `robust mechanism` that has proven valuable for the projects we’ve worked on is that **every team provides a machine-readable directory of all their URL patterns**.
  A JSON file in a known location usually does the trick.

- ***The benefits***
  - Loose Coupling
  - High Robustness
    when one application application goes down, others still work.
    Because the applications `share nothing`


- ***The drawbacks***
  - not always optimal from the user’s point of view
  - no way of combining data from two different teams into one view
  - a lot of technical redundancy and overhead

- ***When do links make sense?***
  - integration that relies on links only is not sufficient in most cases.
  - They play well with other integration techniques.


### Composition via iframe

With iframes, it’s possible to embed one page into another page while maintaining the same loose coupling and robustness properties that the link integration provides.

- ***The benefits***
  - work in every browser.
  - provide strong technical isolation.
  - Scripts and styles can’t leak in or out
  - bring a lot of security features to shield the team’s frontends against each other.

- ***The drawbacks***
  - layout constraint
    - The outer document needs to know the exact height of the iframe’s content to avoid scrollbars or whitespace
    - this will be challenge for responsive site.
    - there are JavaScript libraries exist to automatically update the iframe size when its content changes
  - performance overhead
    -  Adding an iframe to a page is a costly operation from the browser’s perspective
    -  Every iframe creates a new browsing con- text, which results in extra memory and CPU usage.
  - bad for accessibility
    - Iframes break the semantics of the page.
    - screen readers have a hard time conceptualizing the iframe
  - bad for search engines
    - A crawler would index our product page as two distinct pages


- ***When do iframes make sense?***
  - You shouldn’t use iframes if you are building a customer-facing site where loading performance, accessibility, and SEO matter.
  - But for internal tools, they can be an excellent and straightforward option to get started with a micro frontends architecture.