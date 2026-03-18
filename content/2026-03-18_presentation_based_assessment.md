---
tags: education, teaching, software engineering
authors: dcbrown
---
# Project Presentation-Based Assessments in Software Engineering Courses

Software engineering education is rapidly evolving, and finding ways to effectively evaluate students' understanding and application of practical skills is critical. Traditional exams often fail assessing students' abilities to apply theoretical knowledge to real-world scenarios. In addition, the rise and increased adoption of generative AI tools have made evaluating students' comprehension of development concepts more challenging.

To address this challenge, recent efforts have proposed a variety of approaches including oral exams [Ohmann2026], environment-restricted exams in a containerized environment [Panter2026], proctored online exams [Leong2025], returning to paper-and-pencil exams [Boyer2025]. These practices are useful for preventing AI misuse on assessments, however face challenges such as potential invasions of student privacy (proctoring), require technical implementation and maintenance (containerized exam), and can be difficulty to scale for large classes (oral exams, written exams). Specifically for my [undergraduate software engineering course](https://github.com/CS3704-VT/Course), I needed an exam approach that could: 

(a) scale to a large number of students (n = 96);
(b) could be incorporated into final project presentations (due to the large number of students/project groups, several teams had to present during the final exam period to complete the class content);
(c) prevented AI misuse; and
(d) maintained practical relevance to software development and the concepts discussed in class. This innovative approach leverages student presentations of their course projects as a foundation for assessing practical application of class concepts.

To fill this gap, I implemented a **_project presentation-based assessment_** format in my undergraduate software engineering class for the final exam last semester. This assessment approach leverages student presentations of their course projects as a foundation for assessing the practical application of class concepts.

## Project Presentation-Based Assessment

For project presentation-based assessments, students must critically observe teams' project presentations and respond to scenario-based questions connected with the course content. Questions are designed to assess students' understanding of specific concepts discussed in class, and can incorporate multi question types (e.g., open-ended, fill-in-the-blank, multiple choice, etc.). 

In the initial implementation, students had to envision joining two development teams representing final project presentations. The assessment consisted of ten questions, two of which accounted for extra credit, requiring students to respond to scenarios based on live project presentations in the class period. For instance, sample questions included: _"Other than “Agile” and the process used by the presenting team (if applicable), what software engineering process would you use to implement this system. Why?"_ ; _"You are in charge of adding a new feature to this product. What approach would you use to deploy the updated application to users? Why?"_ ; and "_As a new developer on the team, which git command should you use to retrieve the latest version of the code in the remote repository for your local development environment?"_; etc. A full sample exam is available [here](https://docs.google.com/document/d/16gJsCJWKT-kdb4-7bMxD2MC9C9qErJbyKazFi08cfnU/edit?usp=sharing).

To apply this approach, we used our final exam period for the class which consisted of half presentations, and half presentations with ongoing exams. Students had the opportunity to answer questions about two out of approxiamtely 10 presentations, each approxiamtely 20 minutes. The exam was hand-written without the use of technology (i.e., laptops). There were also multiple versions of the exam distributed with different questions and in different orders.

## Perceptions

**Teaching Staff**

From a faculty perspective (n = 1, me), I found this exam format provided the following benefits:

* helped increase engagement and attention to project presentations (historically, students have been unengaged or left the presentation period after presenting early---leaving the final groups with little to no audience);
* provided critical thinking to apply concepts in class to various scenarios (class projects varied widely in topics and domains, including an improved bus transit system, an automated job application assistant, calendars and task management applications, and more.)

While this exam format did scale well, the main challenge was the time for grading. But, the flexible open-ended question format made grading take more time but also it was more interesting to see how  students' would apply different concepts from class into responses.

**Students**

Initial feedback from students was also positive. Many expressed that this format allowed them to provide a more comprehensive demonstration of their skills and found the interactive format to be engaging. Students also shared the real-world contexts made it easier for them to engage thoughtfully with applying the material, and they appreciated the flexibility to draw upon a range of concepts learned throughout the semester. Feedback from studnts was collected within the exam itself, prompting students to understand what questions are discussed in an agile retrospective meeting and (optionally) applying them to this exam format.

##### _1. What Went Well_

Some sample quotes from students are below:

> * "I enjoyed engaging with an actual project an analyzing it"

> * "Testing on the presentations is creative"

> * "It was an interesting way to get me to think more in-deth about other groups' projects"

> * "This final made us use our knowledge of souftware esign in a live practical format, which I think is a good way to gauge student understanding"

> * "This exam format is incredibly engaging and thought-provoking, and gives us a reason to pay attention to the presentations that many would normally space out during"

> * "I think the exam structure being a case study of a presentation is good as it makes us really use our knowledge"

> ...

##### _2. What Didn't Go Well_

The main concerns that arose from student feedback include:

* **Fairness:** Students perceived it was unfair that some students had to worry about presenting and taking the exam simultaneously. For instance, the last several groups to go had to both prepare for presenting while also completing the exam for other groups presentations. The order was decided randomly and students were expected to provide slides ahead of time, however the exam disrupted mental preparations, increased stress, etc.

> * "Having the exam go on while some people are presenting means some students are more stressed than others"

> * "It's not super fair that some teams had to present during the final and threfore got less time than their peers"

* **Focus:** While some students found value in completing the presentation-based assessments, others found it distracting and hard to focus on both writing responses and paying attention to the presentation at the same time. 

> "I got distracted by presenters, often losing my train of thought"

> "It was a little difficult to pay attention to the presentation and answer questions at the same time".

* **Space:** Students noted there was not enough space to write responses in the exam using the paper format.

* **Question Types:** While there was a mix of question types (multiple choice and free response), some students felt there was too much writing involved with this exam.

> "There was a lot of writing and their could have been more MCQs"

##### _3. Improvements_

Students provided some really good ideas for improvements to this assessment approach. Beyond practical improvements (i.e., more writing space, more MCQ questions, more clarity on content, and students should have studied more), suggestions for improvement included:

* having the instructor give a mock presentation for students to evaluate in this format rather than students, preventing unfairness to students presenting during the exam;
* pre-recording presentations to prevent presentations and exams in parallel;
* incorporating more creative practical questions (e.g., "what features would you add")

## Conclusion

This post introduces project presentation-based assessment, providing an overview of this approach and preliminary feedback from an initial implementation in Fall 2025. I will explore applying some of the suggested improvements for this approach, potentially in the graduate-version of the SE course this semester or future iterations of the undergraduate course. I'm also looking forward to further exploring students' perceptions of this assessment approach and how it influences student learning outcomes and preparation for software engineering careers.

---
**Footnotes and References**
>>>

[Ohmann2026] Peter Ohmann and Ed Novak._"A Multi-Institutional Assessment of Oral Exams in Software Courses"_. In Proceedings of the 56th ACM Technical Symposium on Computer Science Education V. 1, pp. 882-888. 2025.

[Panter2026] Kate Panter, Scott Wehrwein, and Hanxiang Du. _"Using Containers to Prevent Generative AI Use in Lab Exams"_. In Proceedings of the 57th ACM Technical Symposium on Computer Science Education V. 2, pp. 1465-1466. 2026.

[Leong2025] Wai Yie Leong. _"E-exams and academic integrity: combating cheating with advanced proctoring solutions"_. In International Conference on Intelligent Technology for Educational Applications, pp. 326-338. Singapore: Springer Nature Singapore, 2025.

[Boyer2025] Lauren Boyer. _"Going old school: Some professors return to pen and paper, tech-free classrooms"_. The College Fix, 2025. [https://www.thecollegefix.com/going-old-school-some-professors-return-to-pen-and-paper-tech-free-classrooms](https://www.thecollegefix.com/going-old-school-some-professors-return-to-pen-and-paper-tech-free-classrooms)
