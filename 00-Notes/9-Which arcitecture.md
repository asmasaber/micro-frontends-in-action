### Revisiting the terminology
  - Integration techniques
  ![Frontend Proxy](/Images/TheIntegrationTechniques.png)
  We can group them into two categories: 
    - ***Routing and page transitions***
    How does a user get from a page owned by Team A to a page owned by Team B.

      ##### *Techniques*
      | Links      | Application Shell | 
      | :---        |    :----:   |
      | Easy      | Fetchs the target markup from a server and then replace the current page with the new one| 
      | Cleanest   |a central piece of JavaScript in the browser|
      | Can host micro-apps under different domains   | It determines which team’s application should be active based on the browser's URL|
      
    - ***Composition***
      - Fragment: 
        - includable micro frontend
        - provided and consumed usning standardized format

      ##### *Techniques*
      | Server-side      | Client-side | 
      | :---        |    :----:   |
      | makes sense when teams generate their markup server-side      |  A solid approach is leveraging the ***Custom Elements API*** from the Web Components spec.| 
      | A central piece of infrastructure like a web server will perform the markup assembly   | Micro frontends can communicate via Custom Events or an event bus/broadcasting solution.|
     

      | Iframe      | Ajax | 
      | :---        |    :----:   |
      | Using iframes in responsive design doesn’t work without JavaScript |  ***hybrid approach*** that does not fit into one of our client- or server-side integration buckets| 
      | having a lot of iframes on a site is resource-intensive   | It does not come with a canonical way to handle (de)initialization and communication but, Using Web Components together with Ajax for internal updating is also a good fit. |
      | provides a high level of technical ***isolation*** | |

    ##### ***High-level architectures***
     ![Frontend Proxy](/Images/DifferentArchitectures.png)
      - ***Linked Pages***
        - no central infrastructure or shared code is required
        - debugging is straightforward
        - new developers instantly understand what’s going on.
        - But from a user experience point of view, there’s room for improvement
      - ***Server Routing***
        - This is identical to the Linked Pages approach, but with the difference that `all requests pass through a shared web server or reverse proxy`
      - ***Linked SPAs***
        - switch from delivering static server-generated pages to implementing a client-rendered single-page app for the pages they own
        - The transitions between team boundaries are still hard navigations
      - ***Single Universal SPAs***
        - identical to the other “linked” architectures. 
        - The contract between the teams is still a set of shared URL patterns. 
        - A navigation across team boundaries results in a reload of the page. 
        - But when implemented well, these reloads should be more seamless compared to a Linked SPA architecture, where the browser needs to execute a bunch of JavaScript before the user can see the content
      - ***UNIFIED SPA***
        - a single-page application (shell app) composed of other single-page applications
        - all page transitions are soft navigations
        
      - ***UNIFIED UNIVERSAL SPA***
        - Unified SPA model + Universal Rendering
        - each team builds a single- page app with universal rendering capabilities
        - app shell also needs to be universal.
        -  comes with the most complexity

    #### Comparing complexity 
      ![Frontend Proxy](/Images/Complexity.png)

    #### Heterogeneous architectures
      some teams are dsoing links and pages, whereas some other teams share an app shell to deliver a Unified SPA. This way, `you only increase the complexity in the areas where it’s needed.`
      Drawbacks:- 
        - There is no go-to architecture for a new team. Teams need to analyze and dis- cuss their use cases beforehand
        - Integrating fragments from different teams might get harder. Teams need to deliver their includable micro frontend in a format that works for the page that includes it.
  
  ### The Documents-to-Applications Continuum


