# Reflection

## Introduction

Bla-Bla was developed as a community-driven marketplace designed to support international students in Sydney in buying, selling, and exchanging second-hand items. In addition to core marketplace functionality, the platform incorporated community-oriented features including discussion posts, user profiles, favourites, and direct messaging between buyers and sellers. The primary objective was to create a practical and accessible web application that addressed both economic and social needs within a university environment.

This reflection evaluates the final prototype against those original goals. Drawing on Lighthouse audits, accessibility reviews based on WCAG AA criteria, and technical analysis conducted through source code inspection, it examines the performance, user experience, and functional effectiveness of the application. Rather than focusing solely on completed features, this reflection critically considers the technical decisions, trade-offs, and limitations that influenced the final outcome.

---

## Performance Evaluation

One of the strongest aspects of the final prototype was its use of server-side rendering (SSR) combined with HTMX-driven interactions. This architecture reduced reliance on large client-side JavaScript frameworks while still allowing dynamic content updates. As a result, the application remained responsive across most user workflows, including browsing items, viewing community content, and accessing messaging features.

Desktop Lighthouse testing demonstrated strong overall performance across most pages. Performance scores ranged from 94 to 100, while Accessibility and Best Practices consistently scored between 96 and 100. These results suggest that the application's architecture successfully supported efficient page rendering and interaction under standard desktop conditions.

**[Evidence 1: Lighthouse Desktop Results Table]**
![Desktop lighthouse test results](assets/Desktop-lighthouse-performance-test-results.png)

However, mobile performance testing revealed a different pattern. Performance scores dropped significantly on several pages, with the Home Page scoring 77, the Community Page 76, the Browse Page 75, and the Share an Item Page 76. The primary contributor identified by Lighthouse was a relatively slow Largest Contentful Paint (LCP), indicating that important visual elements required longer to load on mobile devices.

**[Evidence 2: Lighthouse Mobile Results Table]**
![Mobile lighthouse test results](assets/Mobile-lighthouse-performance-test-results.png)

Source code inspection provided further insight into the causes of these results. I identified several large image assets, including fashion.png (1.9 MB) and chair.png (1.46 MB), contributing to a total image payload of approximately 10.4 MB. While these images enhanced visual quality, they increased loading costs and negatively affected mobile performance. In addition, the main stylesheet had grown to approximately 4,795 lines, suggesting that unused or redundant styles accumulated throughout development.

**[Evidence 3: Image and CSS Findings]**
![images](assets/images.png)
![css](assets/css.png)

The architectural review also highlighted controller-heavy business logic within the messaging system. Functions relating to unread messages, conversation creation, inbox management, and message sending were concentrated within controllers rather than separated into dedicated service layers. Although this structure was sufficient for a prototype-scale application, it could introduce maintainability and scalability challenges as the system grows.

These findings demonstrate that performance limitations were largely the result of development priorities. Throughout the project, feature implementation and interface design were prioritised over optimisation. Given additional development time, image compression, CSS refactoring, and greater architectural separation would likely produce meaningful improvements in both performance and maintainability.

---

## User Experience and Accessibility Evaluation

The application was designed to provide students with a familiar marketplace experience while also encouraging community engagement. Core user journeys, including browsing listings, saving favourites, posting community content, and contacting sellers, remained relatively straightforward and required minimal user effort.

The category-based browsing structure supported efficient item discovery, while the integration of marketplace and community features created a broader sense of participation than a traditional buy-and-sell platform. The messaging system also enabled direct communication between users without requiring external contact methods, helping support trust and convenience within transactions.

Despite these strengths, evaluation identified several usability concerns. One issue involved responsive navigation behaviour. When the browser window became narrow, text within the navigation bar became partially obscured. For example, the "Community" navigation item was reduced to only displaying the letters "nity". Although functionality remained intact, the issue reduced interface clarity and could negatively affect first-time users.

**[Evidence 4: Navigation Bar Responsive Issue Screenshot]**
![Nav Bar Issue](assets/Navigation-Bar-Responsive-Issue.png)

Accessibility evaluation was conducted using WCAG AA criteria.

**[Evidence 5: WCAG Evaluation Table]**
![WCAG Evaluation Table](assets/WCAG-Evaluation-Table.png)

Several accessibility requirements were successfully satisfied. All images included alternative text, keyboard navigation was functional throughout the application, page titles were meaningful, form inputs contained labels, and error handling mechanisms provided clear guidance to users. These findings are also reflected in Lighthouse Accessibility scores, which ranged from 96 to 100 across tested pages.

However, the evaluation identified several accessibility shortcomings. The Home Page failed WCAG 1.4.3 (Minimum Contrast) because the "Explore Community" button did not achieve the required contrast ratio. The Browse Page also failed WCAG 3.2.2 (On Input), as changing filter selections immediately altered page content without sufficient user control or warning.

A further issue was identified on the Community Page. Although the favourite button used a native button element, it lacked ARIA state attributes such as aria-pressed. As a result, screen readers could identify the button but could not communicate its current state to users relying on assistive technologies.

**[Evidence 6: Favourite Button Accessibility Issue Screenshot]**
![Button Accessibility Issue Screenshot](assets/Favourite-Button-Accessibility-Issue-Screenshot.png)

These findings suggest that accessibility was generally considered during development, but not consistently integrated throughout the entire design process. Most issues were relatively minor and could be addressed through interface refinement rather than major structural changes.

---

## Retrospective Assessment of Functional Requirements

The final prototype successfully implemented the majority of the functional requirements established during the planning phase. Users could browse listings, create marketplace posts, participate in community discussions, save favourite items, manage profiles, and communicate through an integrated messaging system.

Several planned features were delivered largely as originally envisioned. The marketplace remained the central component of the application, while community functionality expanded opportunities for interaction beyond transactional exchanges. Together, these features supported the project's broader objective of fostering a student-focused exchange platform.

However, retrospective evaluation suggests that some requirements were either underdeveloped or insufficiently prioritised. Certain homepage interactions and browsing enhancements received less refinement than originally intended, while performance optimisation was largely postponed until after core functionality had been completed. In retrospect, the project prioritised breadth of functionality over depth of implementation.

This evaluation highlights the importance of establishing clearer priorities during planning. While a wide range of features was successfully implemented, several areas would have benefited from additional iteration and refinement before deployment.

---

## Lessons Learned and Future Improvements

One of the most significant lessons from this project was the importance of balancing feature development with long-term maintainability. As functionality expanded, implementation decisions were often made incrementally to support immediate development goals. While this accelerated progress, it also introduced architectural complexity that became more apparent during evaluation.

The code audit revealed examples of schema inconsistencies and controller-heavy logic that emerged as new features were added. These findings suggest that architectural planning should evolve alongside functionality rather than being treated as a separate activity. Maintaining stronger separation between controllers, business logic, and database operations would improve maintainability and scalability in future iterations.

Another important lesson involved accessibility and performance optimisation. Although both areas achieved generally positive outcomes, evaluation demonstrated that these considerations were often addressed after features had been implemented rather than being incorporated throughout the development process. Earlier testing against WCAG criteria and performance metrics could have reduced the number of issues identified during final review.

Future development should focus on four priorities. First, image optimisation and stylesheet refactoring would improve mobile performance. Second, accessibility improvements should address colour contrast, ARIA support, and responsive navigation behaviour. Third, introducing a dedicated service layer would improve architectural separation and maintainability. Finally, additional user testing should be conducted to support more evidence-based design decisions and identify usability issues earlier in the development cycle.

---

## Conclusion

The final Bla-Bla prototype successfully achieved its primary objective of providing a student-focused marketplace and community platform. Evaluation demonstrated strong desktop performance, effective core functionality, and generally positive accessibility outcomes. At the same time, the project revealed opportunities for improvement relating to mobile performance, accessibility compliance, and architectural maintainability. These limitations emerged not from isolated implementation errors but from broader development priorities and trade-offs made throughout the project. Ultimately, the project reinforced the importance of continuous evaluation throughout the development process and highlighted how technical and design decisions directly influence the quality of user experiences.
