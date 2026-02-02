# Parts of a System Design Interview

The purpose of a system design interview is to **evaluate your ability to design
a system to solve a complex problem, in a real-world setting**

- **Problem Solving**: Your ability to identify and prioritize the core challenges
- **Solution Design**: Your ability to create scalable architectures with balanced
  trade-offs
- **Technical** Excellence: Your ability to demonstrate deep knowledge and expertise
  (in some, not all) areas
- **Communication**: Your ability to clearly explain complex concepts to stakeholders

## Requirements/Defining the problem space ~5 minutes

The goal is to **clearly understand the problem & define the scope of the design**.
ASK LOTS OF QUESTIONS.

The goal of questions is to **shrink** the problem space

- Working broad/vague to narrow/specific
- Defining the system constraints

### Functional & Non-Funtional Requirements

What is in and out of scope? **Take your interviewer on a tour of your thinking**.
Once you identify these things, clarify with your interviewer what they want to focus
on

#### Functional

- State your assumptions and decisions so the interviewer can follow your thinking
- Who are our clients?
- Do we need to interact with existing systems/services? What are they?
- Greenfield?

#### Non-Functional

- Who is this for?
- Why?
- What are the Business Objectives?
- Is this linked to users experience
  - CAP Theorem | Pick 2/3
    - Consistency: All nodes across different geographic locations see the same data
    - Availability: Every request recieves a response
    - Partition Tolerance: System operates despite network failuers
- Speed?
- Security?
- Cost?

### Design the system at a high level

Layout the largest pieces of the system i.e DB, API etc. and illustrate how they
they work together to achieve our systems requirements that we defined previously

- You can start by choosing the right API for your use-case and explain why
