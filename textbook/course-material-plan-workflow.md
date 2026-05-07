
We built the textbook using **backward design** and **constructive alignment**: start by defining what students should be able to do, then align chapters, tasks, and assessment evidence to those outcomes. Vanderbilt describes backward design as deciding on learning goals and assessment before planning instruction, and UNSW describes constructive alignment as aligning learning outcomes, activities, and assessment tasks. 

- **Reusable Textbook Design Workflow for Any Subject**
    
    - **1. Define the course promise**
        
        - Write one sentence answering:
            
            - What should students be able to do by the end?
                
            - What kind of subject is this?
                
            - What kind of performance should the book support?
                
            
        - Example pattern:
            
            - This textbook teaches students to move from **X** to **Y** by doing **Z**.
                
            
        
    - **2. Define scope**
        
        - Create two lists:
            
            - **In scope**
                
            - **Out of scope**
                
            
        - Use this rule:
            
            - A topic belongs only if it directly supports the end performance of the course.
                
            
        - This prevents the classic textbook disease: giant wandering blob with chapter titles and no spine.
            
        
    - **3. Write course-level learning outcomes**
        
        - Make them measurable.
            
        - Each outcome should describe what students must **demonstrate**.
            
        - UNSW defines learning outcomes as clear, specific, measurable statements about what students should be able to do. 
            
        
    - **4. Sequence the chapters or modules**
        
        - Arrange chapters from:
            
            - foundational understanding
                
            - to guided performance
                
            - to integrated application
                
            
        - Use prerequisite logic:
            
            - students need enough conceptual structure before analysis
                
            - enough analysis before design
                
            - enough design before implementation
                
            
        - We used that logic to move **basic conceptual data modeling earlier** while keeping the full ERD chapter later.
            
        
    - **5. Separate conceptual artifacts from implementation artifacts**
        
        - For any subject, ask:
            
            - What is the **conceptual model**?
                
            - What is the **implementation-ready version**?
                
            
        - Keep them separate when combining them would confuse learners.
            
        - In our case:
            
            - **ER Diagram** = logical model in Crow’s Foot notation
                
            - **Database Design Diagram** = implementation-ready design with tables, PKs, FKs, data types, and nullability
                
            
        
    - **6. Define chapter objectives**
        
        - For each chapter, write what students should be able to do after completing that chapter.
            
        - Chapter objectives should directly support one or more course-level outcomes.
            
        - This keeps chapters from becoming random content bins with decorative headings.
            
        
    - **7. Define learning tasks**
        
        - For each chapter, list the tasks students must complete to show they met the chapter objectives.
            
        - Learning tasks are demonstrations of learning.
            
        - They can be hierarchical.
            
        - Pattern:
            
            - task set
                
                - subtask
                    
                - subtask
                    
                
            
        - Examples:
            
            - classify
                
            - analyze
                
            - build
                
            - revise
                
            - justify
                
            - test
                
            - submit
                
            
        
    - **8. Add the knowledge needed for each task**
        
        - Use three categories:
            
        - **Concept**
            
            - What something **is**
                
            - A defined idea, category, or class
                
            - Usually nouns or noun phrases
                
            - Examples:
                
                - variable
                    
                - thesis
                    
                - ecosystem
                    
                - primary key
                    
                
            
        - **Principle**
            
            - What is **generally true** about the relationship among concepts
                
            - A rule, generalization, or decision guide
                
            - Helps students make correct judgments in new situations
                
            - Usually written as a full statement
                
            - Examples:
                
                - Strong thesis statements make a defensible claim.
                    
                - A primary key should uniquely identify each row.
                    
                - Cause should be distinguished from correlation.
                    
                
            
        - **Procedure**
            
            - How to **do** something
                
            - An ordered sequence of steps or actions
                
            - Used to complete a task reliably
                
            - Usually written as a method
                
            - Examples:
                
                - Identify the claim, locate evidence, test relevance, then draft the argument.
                    
                - Create parent tables first, then child tables, then test valid and invalid inserts.
                    
                
            
        - Merrill’s Component Display Theory explicitly distinguishes **facts, concepts, procedures, and principles** as different content types. 
            
        
    - **9. Use a standard chapter template**
        
        - Each chapter should normally include:
            
            - purpose
                
            - chapter objectives
                
            - key concepts
                
            - key principles
                
            - core procedures
                
            - worked examples
                
            - common mistakes
                
            - learning tasks
                
            - assessment or deliverable
                
            - project checkpoint or transfer task
                
            
        - Standard templates reduce drift and make the book easier to draft, revise, and scale.
            
        
    - **10. Check alignment**
        
        - Review the map using this chain:
            
            - course outcome
                
            - chapter objective
                
            - learning task
                
            - supporting concepts, principles, procedures
                
            - assessment evidence
                
            
        - If a chapter section does not support that chain, cut it or move it.
            
        - UNSW’s alignment guidance is blunt and useful here: activities and assessment should align with intended outcomes. 
            
        
    - **11. Distinguish drafts from rules**
        
        - Mark:
            
            - what is confirmed
                
            - what is proposed
                
            - what still needs review
                
            
        - This prevents you from canonizing a half-baked draft into “the plan” by accident. A surprisingly common academic goblin.
            
        
    - **12. Save reusable planning artifacts**
        
        - Keep these files for any subject:
            
            - scope spec
                
            - chapter sequence
                
            - course-to-chapter map
                
            - chapter task map
                
            - concepts / principles / procedures guide
                
            - authoring instructions for AI or collaborators
                
            
        - These become your reusable textbook build system.
            
        
    
- **What we specifically did in this project**
    
    - defined the textbook promise and scope
        
    - sequenced the chapters from foundations to implementation
        
    - separated **ER Diagram** from **Database Design Diagram**
        
    - decided to use **Crow’s Foot notation** for the ERD
        
    - moved **basic conceptual data modeling earlier** in the sequence
        
    - mapped:
        
        - course-level objectives
            
        - chapter objectives
            
        - chapter learning tasks
            
        
    - clarified the difference between:
        
        - concepts
            
        - principles
            
        - procedures
            
        
    - turned the chapter sequence into a reusable Markdown planning artifact
        
    
- **Reusable master template**
    
    - **Course promise**
        
        - This textbook teaches students to move from **[starting point]** to **[target performance]** by doing **[core disciplinary work]**.
            
        
    - **Scope**
        
        - In scope
            
        - Out of scope
            
        
    - **Course-level outcomes**
        
        - CLO-1
            
        - CLO-2
            
        - CLO-3
            
        
    - **Chapter map**
        
        - Chapter title
            
            - Purpose
                
            - Chapter objectives
                
            - Learning tasks
                
            - Concepts
                
            - Principles
                
            - Procedures
                
            - Deliverable or assessment evidence
                
            
        
    - **Artifact rules**
        
        - Conceptual artifact(s)
            
        - Implementation artifact(s)
            
        - Rules for keeping them separate
            
        
    - **Standard chapter template**
        
        - purpose
            
        - objectives
            
        - explanation
            
        - examples
            
        - mistakes
            
        - tasks
            
        - deliverable
            
        
    
- **One-line rule for reusing this workflow**
    
    - Start with what learners must **do**, then define what they must **know**, then sequence the book so each chapter makes the next performance possible. 
        
    
