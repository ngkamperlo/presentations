---
marp: true
html: true
theme: default
paginate: true
style: |
  .columns {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 1rem;
  }
  .vert {
    vertical-align: middle
  }
  .fa-twitter { color: aqua; }
  .fa-linkedin { color: blue; }
  .fa-window-maximize { color: skyblue; }
  .fa-th-large {
    color: blue;
  }
  .qrcode {
    width: 150px;
    height: 150px;
  }

  @import 'https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.2.1/css/all.min.css'

---

<div class="columns">
<div>

## Associate Director of Engineering<br>**GWI**</br>

<i class="fa-brands fa-twitter"></i> Twitter: @ngkamperlo
<i class="fa-brands fa-linkedin"></i> LinkedIn: [https://linkedin.com/in/ngkamperlo](https://linkedin.com/in/ngkamperlo)
<i class="fa fa-window-maximize"></i> Blog: [https://medium.com/ngkamperlo](https://medium.com/ngkamperlo)
<i class="fa-brands fa-github"></i> GitHub: [https://github.com/ngkamperlo](https://github.com/ngkamperlo)
</div>

<div>
<div class="qrcode">
My book on MFEs 🤘

![Image](./img/book.png)

</div>
</div>
</div>



---

# ***Unifying UI*: Harnessing Web Components in Micro-Frontends**

---

# Our Journey with MFEs so far
- In 2019, we embarked on a journey with MFEs to tackle the challenges of scaling our codebase and making our teams more autonomous.
- We started Single SPA as our framework, today we consider switching to Module Federation.
- Our main focus at the start was to create a seamless experience between our Elm and React-based applications, ensuring smooth interoperability.
- We introduced BlackBox pattern to address mini apps implementation

---

# Challenges with Common UI Components
- Needed common functionality by both Elm and React-based applications.
- We decided to implement the functionality once
  - either in React or Elm
  - wrap the output in web components
- Saved time but
- Introduced complexity in our codebase

---

# MFE - Web component communication
- The MFE transmits data to the common component through its **HTML attributes**
- The MFE retrieves data from the common component using the **browser’s custom events**

---

# Developing an Internal Storybook for Web Components
- To streamline our workflow, we set up an internal storybook for managing web components.
- This central hub provided several advantages: 
  - it enabled quick development and WYSIWYG functionality
  - ensured everyone was aware of the latest changes
  - better communication among team members

---

# Need for Single-Page Mini Apps
- As our MFEs evolved, we realized the need for single-page mini-apps.
- These were 
  - too small for a new MFE and
  - too big for a web component
  - and able to capture the full viewport of the browser. 

---

# Solution #1: The BlackBox Pattern for Mini Apps
- We used the BlackBox pattern to create single-page mini apps as MFEs.
- These black-box apps communicate with other applications through custom events and can be rendered or hidden from the DOM as needed. 

---

# Pros and Cons of Solution #1
- Pros:
  - entire single-page mini app’s code was contained in one repository
  - simplified maintenance
  - communication with each MFE through simple browser events
- Cons: 
  - BlackBox pattern may not work as effectively for Elm-based applications, 
  - FE engineers need to create complex wiring with their MFEs

---

# Solution #2: Web Components with Independent Repositories for Mini Apps
- We created single-page mini apps as web components
- regardless of their size
- provided each one with its own Git repository

---

# Pros and Cons of Solution #2
- Pros: 
  - Each mini app’s code was contained in a single repository, making it easy to track and maintain.
- Cons: 
  - FE engineers may need to set up more sophisticated connections when implementing these mini apps in their MFEs. 
  - The lack of static typing for TypeScript means that potential errors can only be caught during runtime.

---

# Elm's Farewell Party
- As our development priorities and technology stack evolved, we made the decision to discontinue the usage of Elm in our main platform
- **Elm**: "I thought we had something special!" 
- **React**: "It's not you, it's us. We just need to streamline our development process."
😂
---

# Solution #3
- Involves embedding single-page mini-apps into their most related micro-frontend.
- This works for ***our*** specific scenario of sharing the same domain between an MFE and a common component. 
- In general it's not a recommended approach - don't try this at home 🏡

---

# Pros and Cons of Solution #3
- Pros: 
  - Single code repository simplifies development and organization. 
  - Reduce dependencies between repos
- Cons: 
  - May introduce complex CI pipelines for proper building, testing, and deployment. 
  - May introduce complexity around MFE communication

---

# Next Steps: Solution #4
- We're also considering elevating the single-page mini-apps to a higher level of independence by turning them into standalone MFEs. 

---

# Pros and Cons of Solution #4
- Pros: 
  - Each mini-app benefits from having its own code repository, allowing for 
  - better separation and management of the individual components
- Cons: 
  - Communication between MFEs should be carefully implemented

---

# The Future of Mini Apps
- We're considering implementing Solution 4
- although its implementation effort might be significantly bigger compared to Solution 3

---

# Transition to a React-only Approach
- As we transition to a React-only approach, it’s crucial to explore new solutions that align with our evolving technology stack. 
- We're excited about the opportunities this shift presents.
- At last ***static typing via Typescript!***

---

# The Role of Module Federation
- We are considering to switch from Single SPA to Module Federation
  - Module Federation enables the seamless sharing of components across applications.
  - Is almost the industry standard around code splitting.

---

# Key learnings 1/2
- Common UI components via web components: reducing code duplication.
- Communication between MFEs
  - HTML attributes and 
  - custom browser events.
- Internal storybook
  - streamlines development
  - improves communication
  - keep everyone updated

---

# Key learnings 2/2

- Transitioning to a React-only approach opens up new opportunities and strategies, like catching errors on build time.
- Evaluating each solution's pros and cons, considering factors like team preferences, performance requirements, and maintainability, is crucial for making informed decisions in the MFE world.
- Our journey with web components has equipped us with essential tools to tackle complex UI challenges, and we're excited to apply these learnings to our future work.

---

<div class="columns">
<div>

# Thank You! 🤘
# Naim Gkamperlo

<i class="fa-brands fa-twitter"></i> Twitter: @ngkamperlo
<i class="fa-brands fa-linkedin"></i> LinkedIn: [https://linkedin.com/in/ngkamperlo](https://linkedin.com/in/ngkamperlo)
<i class="fa fa-window-maximize"></i> Blog: [https://medium.com/ngkamperlo](https://medium.com/ngkamperlo)
<i class="fa-brands fa-github"></i> GitHub: [https://github.com/ngkamperlo](https://github.com/ngkamperlo)

</div>

<div>

[Github repo](https://github.com/ngkamperlo/blackbox)
![Image](./img/frame.png)

</div>
</div>