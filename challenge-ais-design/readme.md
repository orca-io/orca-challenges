Challenge - AIS design
=====

> The automatic identification system, or AIS, transmits a ship’s position so that other ships are aware of its position. The International Maritime Organization and other management bodies require large ships, including many commercial fishing vessels, to broadcast their position with AIS in order to avoid collisions. Each year, more than 400,000 AIS devices broadcast vessel location, identity, course and speed information. Ground stations and satellites pick up this information, making vessels trackable even in the most remote areas of the ocean.[1]


Task
-----

Design an AIS representation for Orca that balances the given considerations. The goal of the representation is to show other vessels nearby in the user's marine chart to help the user:

a) Avoid collisions, close encounters and respect right of way[2]
b) Understand the general traffic conditions at a given area prior to arrival/entry in the area

Details
-----

### The user persona

The user is a recreational boater. The user understands the principles of AIS. The user conducts a combination of small daily boat trips around his/her harbour, and longer distance trips – such as crossing the British Channel.

### Considerations

1. Vessel types should be differentiated to allow the user to easily identify and respect right of way priority
2. The representation must work on top of the Orca charts and minimize obstruction of legibility of the chart's content. A link to interactive Orca chart will be given on request. 
3. The system must work well across many chart zoom levels. From small to large scale (ex: Viewing the British Channel crossing and viewing the detailed layout at a marina)
4. The system must work well when many vesels are present in a confined location around the user's boat, and when there are few vessels around the user's boat
5. The system may show contextual information to assist the user identifying closest point of approach with vessels nearby


Notes
-----

We value simplicity and elegance as opposed to complex solutions.

Present the final result with realistic vessel density under multiple realistic conditions. Use MarineTraffic[3] or similar tools to evaluate what is representative traffic density at various locations. 

While its reasonable to expect the user to be able to click on a vessel to query it for details, this functionality does not need to be designed. The task only asks for a system to visualize vessels in the Orca map.


Deliverable
-----

1. Document the steps you've taken to research the problem.
2. Document the varios iterations you've done – even those discarded.
3. Present the final result in whatever form you'd like.


References
-----

- [1] https://globalfishingwatch.org/faqs/what-is-ais
- [2] https://www.boatus.org/study-guide/navigation/rules
- [3] https://www.marinetraffic.com/
