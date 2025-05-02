# Validation Results of the Taxonomy and Conceptual Model

### Agreement Rate Calculation

- **Yes**: Assign a value of \[1\]
- **Partial**: Assign a value of \[0.5\]
- **No**: Assign a value of \[0\]

**Agreement Rate**: Calculate the average of these values for each criterion, then express it as a percentage of the maximum possible agreement (which is \[1\]).

## Rating Distribution for Taxonomy Validation

| **Index** | **Criteria**                          | **Yes** | **Partial** | **No** | **Agreement Rate** |
|-----------|---------------------------------------|--------:|------------:|------:|-------------------:|
| **C1**    | Alignment with Existing Literature    |       3 |           0 |     0 |             100%   |
| **C2**    | Clarity of Definitions                |       3 |           0 |     0 |             100%   |
| **C3**    | Scope and Completeness                |       2 |           1 |     0 |              83%   |
| **C4**    | Granularity of Categories             |       2 |           1 |     0 |              83%   |
| **C5**    | Consistency Across Dimensions         |       3 |           0 |     0 |             100%   |
| **C6**    | Inter-Categorical Relationships       |       2 |           1 |     0 |              83%   |
| **C7**    | Real-World Applicability              |       3 |           0 |     0 |             100%   |
| **C8**    | Scalability for New Practices         |       2 |           1 |     0 |              83%   |
| **C9**    | Practical Utility                     |       2 |           1 |     0 |              83%   |
| **C10**   | Cross-Dimensional Consistency         |       3 |           0 |     0 |             100%   |
| **C11**   | Terminological Precision              |       3 |           0 |     0 |             100%   |
| **C12**   | Rationale Behind Categories           |       3 |           0 |     0 |             100%   |

## Key Comments, Discussions, Refinements, and Limitations
### Taxonomy

1. **C3: Scope and Completeness (83 % agreement)**
   - **Comment:** Several speculative “as-code” practices—such as Law as Code, Contracts as Code, Management as Code, and DNS as Code—were not captured in our taxonomy.  
   - **Discussion:** These practices currently lack sufficient documentation or widespread recognition in the EaC literature and have yet to establish clear relevance in software-engineering workflows.  
   - **Refinement:** We have catalogued these emerging practices in a supplementary registry, providing brief descriptions to acknowledge their potential future inclusion once further empirical evidence becomes available.

2. **C8: Scalability for New Practices (83 % agreement)**
   - **Comment:** It is not immediately clear how novel “as-code” practices can be integrated into the existing taxonomy.  
   - **Discussion:** While no taxonomy can anticipate every future development, our chosen representation formats (tables, diagrams) are designed for extension.  
   - **Refinement:** We published the taxonomy in a machine-readable JSON schema, enabling practitioners and researchers to add or modify entries programmatically as new practices emerge.

3. **C4 & C6: Granularity of Categories and Inter-Categorical Relationships (83 % agreement)**
   - **Comment:** Some experts felt that (a) category granularity is too coarse and (b) the relationships between categories are under-specified.  
   - **Discussion:** Our categories and their interconnections are anchored in the CNCF Landscape, which provides an industry-standard layering.  
   - **Refinement:** We have added explicit citations to the CNCF documentation and included a mapping table that aligns each taxonomy category with its corresponding CNCF layer, guiding readers to those sources for more detailed breakdowns.

---

## Rating Distribution for Conceptual Model Validation
| **Index** | **Criteria**                                     | **Yes** | **Partial** | **No** | **Agreement Rate** |
|-----------|--------------------------------------------------|--------:|------------:|-------:|-------------------:|
| **C1**    | Empirical Foundation                             |       3 |           0 |      0 |             100%   |
| **C2**    | Clear Representation of Relationships            |       3 |           0 |      0 |             100%   |
| **C3**    | Consistency with Taxonomy                        |       3 |           0 |      0 |             100%   |
| **C4**    | Lifecycle Alignment                              |       2 |           1 |      0 |              83%   |
| **C5**    | Granularity of Interaction Representation        |       2 |           1 |      0 |              83%   |
| **C6**    | Subdomains Accuracy                              |       3 |           0 |      0 |             100%   |
| **C7**    | External Tool Integration                        |       1 |           1 |      1 |              50%   |
| **C8**    | Representation of Overlaps and Dependencies      |       3 |           0 |      0 |             100%   |
| **C9**    | Practical Application                            |       2 |           1 |      0 |              83%   |
| **C10**   | Scalability of the Model                         |       0 |           1 |      2 |              17%   |
| **C11**   | Visual Clarity                                   |       3 |           0 |      0 |             100%   |
| **C12**   | Interdisciplinary Relevance                      |       3 |           0 |      0 |             100%   |

## Key Comments, Refinements, and Limitations
### Conceptual Model
1. **C5: Granularity of Interaction Representation (83 % agreement)**
   - **Comment:** The model’s relationship arrows could be refined to capture more nuanced interactions.  
   - **Discussion:** Earlier drafts attempted exhaustive relationship mapping, which compromised the model’s readability.  
   - **Refinement:** We developed a companion document that enumerates and elaborates every relationship in detail—preserving the clarity of the main diagram while offering deeper insight in the supplement.

2. **C7 & C9: External Tool Integration (50 % & 83 % agreement)**
   - **Comment:** Although the model conceptually references tools (e.g., Terraform, Ansible, Jenkins), it does not clearly demonstrate how practitioners apply these tools in pipelines.  
   - **Discussion:** The primary aim of the conceptual model is to abstractly represent practice interactions, rather than prescribe specific tool usage.  
   - **Refinement:** We created an “Implementation Examples” appendix containing annotated code snippets and CI/CD configurations that concretely illustrate how the model’s relationships are instantiated with popular industry tools.

3. **C10: Scalability of the Model (17 % agreement)**
   - **Comment:** There is little evidence that the model can easily accommodate emerging “as-code” practices beyond those currently established.  
   - **Discussion:** Incorporating new practices requires thorough domain analysis and manual diagrammatic updates—an inherently complex task.  
   - **Limitation:** We acknowledge this constraint and, in future work, plan to encode the model in a machine-readable format (e.g., JSON or a graph database) and explore AI-assisted updates to enhance its extensibility.
