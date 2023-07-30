# Purpose
The purpose of this project is to organize information contained in textbooks and papers about diseases relevant to veterinary medicine and use this information to generate useful tools for students to learn about these diseases. The first objective is to embed the information in a database and use this database to retrieve this information and pass it to language models so we can organize it in a relational database format. The second objective is to develop tools using this relational database.

Basically, we want this:
```
EPIDEMIOLOGY
The disease is sporadic but common in cattle.
Occasional cases occur in pigs, horses, goats,
dogs, and humans. Although actinomycosis
occurs only sporadically, it is important
because of its widespread occurrence and
poor response to treatment. It is recorded in
most countries of the world.
A. bovis is a common inhabitant of the
bovine mouth and infection is presumed to
occur through wounds to the buccal mucosa
caused by sharp pieces of feed or foreign
material. Infection may also occur through
dental alveoli and may account for the more
common occurrence of the disease in young
cattle when the teeth are erupting. Infection
of the alimentary tract wall is probably
related to laceration by sharp foreign bodies.
```

To become something like this:

```python
epidemiology_data = {
    "disease": "actinomycosis",
    "common_in": ["cattle"],
    "occasional_cases_in": ["pigs", "horses", "goats", "dogs", "humans"],
    "importance": "widespread_occurrence_and_poor_response_to_treatment",
    "recorded_countries": "most_countries_of_the_world",
    "infection_source": {
        "source_1": {
            "organism": "A. bovis",
            "source_type": "bovine_mouth"
        },
        "source_2": {
            "organism": "A. bovis",
            "source_type": "dental_alveoli",
            "presumed_infection": "young_cattle_with_erupting_teeth",
        },
        "source_3": {
            "organism": "A. bovis",
            "source_type": "alimentary_tract_wall",
            "presumed_infection": "laceration_by_sharp_foreign_bodies",
        },
    }
}
```

Then we can create cool learning tools, like:
- Clinical trial generator: a tool that creates clinical trials that makes sense and are unique every time they are generated!
- Differential diagnosis explorer: a tool that, given information about a specific case, gives you all possible differentials diagnosis and why.
- Disease map: a mind map that connects diseases, showing how they are connected and how closely related they are.
- Farm simulator: a tool that integrates the clinical trial generator in a farm enviroment, giving the student to experience 

# Challenges
One of the challenges in this is that the information is written in a narrative style, so we have to extract the key facts and organize them in a structured way, but each disease has its own particularities and format. We will likely need to develop custom models for each disease to extract the information correctly, but that makes automating some things for the tools a little difficult. We may need to use a language model output in the tools pipeline, which would add a cost to the tool usage (which is not the intent of this project).
