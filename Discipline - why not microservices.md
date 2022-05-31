Discipline

Why microservices by default isn't a great bet.

---

tl;dr: microservices don't solve problems, they only make them more apparent. Packages are an alternative.

---

Ad hominem

- Microservices na Yelp
  - Big established company with its own decade-old monolith, 300 to 500 engineers
  - Big monolith was being broken to pieces when I came in.
  - Search was the first one, other followed
  - Everyone loved being on a microservice to avoid the painful deployment process
- Microservices na Fractal
  - Small startup with ~10 engineers
- Pacotes da Doist
  - Medium start-up, 50 engineers, ~10 backend, ~10 more contributers from other teams

---

Engineering is about trade-offs and optimization.

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

    Nobody can make your code slow or clunky, but now you need to have a mailing list for your downstream consumers.

  - Customs
    - Freedom to choose your own philosophy
    - Everyone needs to be onboarded

    You can have monoids of endofunctors, but only the indoctrinated will help you.

---

- Microservices is a tech heavy solution for coordination problems
  - Not independence, a different type of dependence
  - Designing a system becomes designing the organization that ships and maintains it.
  - Conway's law and Inverse Conway maneuvers
  - Requires immense discipline and choreography
  - Great if you want to, or need to, outsource competency

XXX asottile's video about Stripe moving off of Python onto Java to make things simpler.

---

Microservices is commoditization

Commoditization is the process of converting products or services into standardized, marketable objects.

Inevitable when involving with more than a few hundred engineers.

---

Microservices is linking at the network layer

---

Packages

Still commoditization, still lots of discipline, a bit more plasticity.

---

