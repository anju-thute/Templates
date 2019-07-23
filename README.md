# EXCEADS-Templates
Templates for inclusion in EXCEADS

Repository directory organization:
* Type of Template
  - Instance of Template
    - JSON file
    - Documentation in Markdown
    - PNG or other "cartoon" of template (optional)
* dev
  - Similar to the above structure for development of new templates

## Contents
#### Disease  
* [SEIR](https://github.com/NSSAC/EXCEADS-Templates/blob/master/disease/seir/seir.md)
* [Ebola](https://github.com/NSSAC/EXCEADS-Templates/blob/master/disease/ebola/ebola.md)

#### Population  
* [Montgomery County, VA](https://github.com/NSSAC/EXCEADS-Templates/blob/master/population/VA_montgomery_county/montgomery_county_va.md)

##### Population - traits
* [Influenza traits for treatment, prophylaxis, and newly infected individuals](https://github.com/NSSAC/EXCEADS-Templates/blob/master/population/_node_traits/Isymp_treat_prophylax/Isymp_treat_prophylax.md)  

#### Initializations
* [agebased_prevaccination](https://github.com/NSSAC/EXCEADS-Templates/blob/master/initialization/agebased_prevaccination/agebased_prevaccination.md)
* [initial_infection_number](https://github.com/NSSAC/EXCEADS-Templates/blob/master/initialization/initial_infection_number/initial_infection_number.md)  
* [initial_infection_percent](https://github.com/NSSAC/EXCEADS-Templates/blob/master/initialization/initial_infection_percent/initial_infection_percent.md)

#### Triggers
* [day](https://github.com/NSSAC/EXCEADS-Templates/blob/master/trigger/day/day.md)  
* [infected_school_children_number](https://github.com/NSSAC/EXCEADS-Templates/blob/master/trigger/infected_school_children_number/infected_school_children_number.md)  

##### trigger helpers 
* [prophylax_household_helper](https://github.com/NSSAC/EXCEADS-Templates/blob/master/trigger/prophylax_household_helper/prophylax_household_helper.md)  
* [count_symptomatic_helper](https://github.com/NSSAC/EXCEADS-Templates/blob/master/trigger/count_symptomatic_helper/count_symptomatic_helper.md)  

#### Interventions
* [close_school_duration](https://github.com/NSSAC/EXCEADS-Templates/blob/master/intervention/close_school_duration/close_school_duration.md)    
* [prophylax_household](https://github.com/NSSAC/EXCEADS-Templates/blob/master/intervention/prophylax_household/prophylax_household.md)  
* [treat_symptomatic_with_health_seeking_delay](https://github.com/NSSAC/EXCEADS-Templates/blob/master/intervention/treat_symptomatic_with_health_seeking_delay/treat_symptomatic_with_health_seeking_delay.md)  


    
## Documentation of the EXCEADS specific tags
Documentation of the "exceads" specific tags in the templates

```
  "exceads": {
    "requires": {
      "allOf": ["diseaseModelTemplate1.json"]
    }
  }
```
Explicit dependency of the template on existence of other templates (through filename for now)

More examples here please!

How do we want to do:
* Grouping of templates??
* Specify upper and lower bounds
* Type of input widget (eg text box, slider, etc. )

