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
* Ordering and grouping of elements (eg which of the text boxes should come first in the GUI, do some belong under a common header, eg coverage of vaccine by age-group)

## Template Validation Rules and mapping of attributes in EXCEADS :

* ann:label is mapped to name of the template and cannot exceed more than 100 characters.
* ann:description is mapped to description of the template and cannot exceed more than 2000 characters.

* Every user input under userInput array, should have exceads block - a JSON object which can have following attributes :
  - If section has "minValue", then it's value cannot be empty. Specify the value in number
  - If section has "maxValue", then it's value cannot be empty. Specify the value in number
  - If section has "sweep", then it's value cannot be empty. Specify the value in boolean i.e. true/false
  - If section has "calibrate", then it's value cannot be empty. Specify the value in boolean i.e. true/false

* Every template has generic exceads block - a JSON object (at the level of template, userInput, requirements etc.) which can have following attributes :
  - name (Optional) - This is not being used currently since we are using ann:label to map the name attribute for the template.
  - shortName - Short Name of the Template
  - groupName - This is an array of strings which specifies that this template belongs to which all groups.
  - referenceImage - This attribute is specific to Disease Model, in case Parallel PNG is not present for the corresponding template, this is to be taken up as an Image Represntation for the Disease Model
