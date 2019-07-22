### Ebola Virus Disease model
Susceptible, Exposed, Infectious, Recovered, Hospitalized, Funeral (community and from Hospital) and Deceased
An extension of the classic **Legrand** ebola model, with addition of splitting out community and hospital based funerals and an explicit recovered and deceased state.

![Ebola Virus Disease Diagram - Legrand extended](LegrandModel_extended.png)

This model allows for specifying the probabilities of being hospitalized, recovering, and dying.  As well as how infectious hospitalized patients are as well as the deceased during community funeral practices.

Specifically:  
* Infectivity during community funerals  
* Infectivity during hospitalization  
* Probability of Hospitalization (I to H)  
* Probability of dying in the community (I to Fc)  
* Probability of recovering in the community (I to R)  
* Probability of dying while hospitalized (H to Fh)  
* Probability of recovering while hospitalized (H to R)  

based on: [EpiHiper-Schema/test/003/diseaseModelTemplate2.json](https://github.com/NSSAC/EpiHiper-Schema/blob/master/test/003/diseaseModelTemplate2.json)
on July 18
