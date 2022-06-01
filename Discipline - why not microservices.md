Discipline

Why microservices by default isn't a great bet.

---

tl;dr: microservices don't solve problems, they only make them more apparent. Packages can be a less demanding alternative.

---

Ad hominem

- Yelp
  - Big company
  - Decade-old monolith, lots of microservices
  - ~400 engineers
- Doist
  - Medium company
  - Decade-old monolith, a few microservices
  - ~50 engineers, ~10 backend, ~10 more contributers from other teams
- Trust Fractal
  - Small company
  - Greenfield, lots of microservices
  - ~10 engineers

---

Engineering is about trade-offs and optimization.

---

Nightmares: 
  - Huge codebase
  - Separation of concerns
  - Deploying
  - Scaling
  - Bulkheading

Let's make them impossible!

---

- Microservices is independence!
    - Runtime
      - Scale to your own needs
      - You're now a distributed system
  
      You can service requests in whichever way you want, but some team you never heard of can take your service down.

    - Tech
      - Use the right tool for the job
      - Expertise is fragmented
  
      You can use Prolog in your microservice, but debugging is done through committee.

    - Structure
      - Other teams won't impact your internal structure
      - Any externally-visible structure change becomes a coordination concern

      Nobody can make your code slow or clunky, but now you need to have a mailing list of downstream consumers to change your API.

  - Customs
    - Freedom to choose your own philosophy
    - Everyone needs to be onboarded

    You can have monoids of endofunctors, but only the indoctrinated will help you.

  - Scope
    - Have tight codebases that do one thing right
    - Have many services with various degree of overlap

    You can always spin up new services, but eventually some are left running with no consumers.

---

Microservices is commoditization

Commoditization is the process of converting products or services into standardized, marketable objects.

Hard to avoid when involving data stewardship with more than a few hundred engineers.

---

- Microservices is a tech heavy solution for coordination problems
  - Not independence, a different type of dependence
  - Designing a system becomes designing the organization that ships and maintains it.
  - Conway's law and Inverse Conway maneuvers
  - Great if you want/new to outsource competency
  - Everything is choreography

Choreography is the new nightmare.

---

Microservices is linking at the network layer

How about we try linking at the function level?

---

Packages are the classic commodities

Focused on code, not stewarding data

---

- Packages are dependencies!
    - Runtime
      - Constrained to the same process space
      - Not a distributed system (no more retries or sagas!)

    - Tech
      - Contained to one ecosystem
      - Expertise is shared and compounded
  
    - Structure
      - Other teams can impact your internal structure
      - API changes can each be fully owned by a single party

    - Customs
      - You need to comply to some practices
      - Onboarding is much cheaper

    - Scope
      - It's hard to understand that part of the codebase should do what
      - Dead code is trivially found with commonplace tooling

---

Nightmares:
  - Huge codebase
    - Factor parts out to packages
  - Separation of concerns
    - Be diligent about architecture
  - Deploying
    - Focus on package bumps
  - Scaling
    - Use per-endpoint process pools
  - Bulkheading
    - Ration process-level globals

Diligence was the hardest in the old nightmare.

---

Engineering is about trade-offs and optimization.

What's easier to optimize for in your context?
- Diligence
- Choreography