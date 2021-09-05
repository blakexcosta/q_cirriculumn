# Quantum Curriculum Draft



### Curriculum Draft Intro/Overview


- Note: `R:` denotes areas still needed to reserach


  - `{TODO: note on what to do}`  just denotes a todo of cirriculumn that needs to still be done/written/reworked 

- Please note this is just MY notes on subject material and resources I felt are good at describing the topics at hand.

- ### **Instruction, end goals/notes to understand:**


  - the end format is intended be structured like:  `theory` , `walkthrough/soft-exercise` and then `hard-exercise` sections at the end.

    - we want to keep them as separate as possible to avoid bogging down theory portions with *excessive* code. As well as walkthrough's only having relevant theory information when needed (like re-enforcing an important point). The exercises are supposed to be a test of personal skills and applying theory learned and the walkthrough practical's to your own project/exercise.
  - Hands *off* of the keyboard when learning theory. ***DO NOT***  code along with theory if code is used to explain. That is what the walkthrough and exercise portions are for, and they will re-inforce what is needed to be done.
  - **Some smaller details (for staff):**
    - highlight what is to be learned at beginning of theory session. And then also highlight what was done at the end of the theory portion or theory video. This re-enforces goals and objectives and provides some structure for everyone involved.

      - example:

        - Lesson Objectives:

          - (Beginning of lecture): `Objectives: Learn fundamentals of AI Ethics`
          - (End of lecture): `Objectives Accomplished: \n Learn fundamentals of AI Ethics`
    - Keep theory, walkthrough and exercise sections as digestible, bite-sized and succinct as reasonably possible. Goal is to be a *guide* and to lead them through a subject. Not death-by-powerpoint them.

      - Focus on clarity over everything. If even one small thing is learned, that is a success. 
    - Walkthrough's are ***NOT*** the place to bring up new concepts and theory. This should have been covered in the theory lecture/lesson. IF code/ a project was needed to *explain* the theory, then that was the time and the place to do so. ***NOT*** in a walkthrough. 

      - A walkthrough is supposed to be simple (as possible), concise, and practical.


---


- ## **Unit 1 Data Science Fundamentals**
	
	- **Unit/Course Overview**
	- **Project overview**
	- **Jupyter**
		- Anaconda Navigator installation:
	- **Python**
	- **Numpy**
	- **Pandas**
	- **matplotlib**

---


-  ## **Unit 2 Machine Learning/Deep Learning FUNdamentals**
	
	+ **Overview of the Unit/Course**
	+ **Project overview (building some simple predictor like study habits predicting passing rates... but more interesting)**
	+ **AI Ethics**
	+ Intro to deep neural nets?
		+ model validation
		+ import your data:
			 ```python
			import pandas as pd
			from sklearn.tree import DecisionTreeRegressor
			
			#import your data files
			some_data = '../somedatafile'
			
			# Specify Model
			
			# Fit Model
			
			# Build out your predictions
			```
		+ Model validation (this is based https://www.kaggle.com/dansbecker/model-validation)
			+ One of the most important things to do with you model is to actually validate it. You will do this with almost every model you create
			+ DO NOT make predictions on training data and then comparing those predictions to target values in the training data.
				+ this will throw bias in the model and is like cheating on a test. 
					+ This is called **In-Sample** scoring and is **BAD**. DO NOT DO THIS
			+ One of the simplest metrics for guaging model quality is **MAE** or **Mean Absolute Error**
				+ The formula for this is:
					+ `error=actual-predicted`
						+ so for example, if you had a house that was worth $300000 and the model predicted it to be worth $100000, the error would be $200000
				+ with the **MAE** metric take the absolute value of each error. Then we need to convert each error to a positive number and take the average of those absolute errors. This is how we measure model quality. and tells us that **our predictions are off by about x amount**
				+ Fortunately for us python has a module that helps us  do this
			+ **USING MAE**
				```python
				from sklearn.metrics import mean_absolute_error
				
				predicted_home_prices = melbourne_model.predict(X)
				mean_absolute_error(y, predicted_home_prices)
				```
			+	first we need to split the data into training and testing data
				```python
				from sklearn.model_selection import train_test_split
				#split data and set the random state to the same if you need to replicate results
				train_X, val_X, train_y, val_y = train_test_split(X,y,random_state=0)
				melbourne_model = DecisionTreeRegressor()
				melbourne_model.fit(train_X, train_y)
				val_predictions = melbourne_model.predict(val_X)
				print(mean_absolute_error(val_y, val_predictions))
				```
			+	In this specific example, notice that the absolute error for in sampled dat was 5-- and out of sample was over 250000. This is nearly a quarter of our home worth so it's not very usable for our case at the moment
		+ overfitting and underfitting
		+ stochastic gradient descent
		+ activation functions
		+ backpropagation
		+ parameter tuning
	+  Computer Vision ?
		+ could possible break this out into it's own course all together
	+ Natural Language Processing ?
		+ could possibly break this out into it's own course all together
---
- ## **Unit 3 Quantum Theory + Computing Background** (Theory Section)

  - **High level overview/ why important**
  - https://qiskit.org/learn/?learnLevel=Beginner&timeScale=1%20week
    - Coding with qiskit
    - Though there is many hurdles and areas need to grow; Quantum computing has the potential to allow us to solve problems previously thought to be impossible
      - such as quantum chemistry such as calculating the bond length of molecules
        - or quantum algorithms like the Bernstein-Vazirani Algorithm
        - Or even program games based upon quantum computing
      - Our end goal here is to create a universal fault tolerant computer that surpasses the computational power of classical supercomputers
    - We presently have NISQ's (Noisy Intermediate-scale quantum computers)
      - However, they're still too complex to predict
    - Many advancements still require the use of traditional scientific methods with theory and experiments
      - however, the software developer/coder presents a possible solution with possibly allowing us to develop and advancing a quantum software framework. We need things like:
        - tools to study algorithms
        - build things for verification + validation of quantum devices
        - study small quantum codes
        - fault tolerance
        - optimal control theories
        - developing reliable circuit + pulse scheduling schemes to run circuits on real device
  - **Information + Bits**
  - **Qubits** 
  - **Superpositioning**
  - **Quantum Entanglement**
  - **Superdense coding**
  - **Quantum Teleportation**
  - **Quantum Cryptography**
  - **Intro to Q#/ Qiskit**
  - **Quantum Objects (this may not be required, could be bonus)**
  	- High level overview/ why important
  	- Observables
---
- ## **Unit 4 Quantum Toolsets (Q#/Qiskit portion of course)** (Walkthrough Section)

  - **Overview of Unit/Course**
    - **4 pillars of QisKit**
      - Terra - "Earth"
        - foundation on which the rest of software lies.
        - Does/focused on the following:
          - provides the bedrock for composing quantum programs at the circuit + pulse levels
          - optimizing for constraints of a particular devices. 
          - Managing execution of experimental batches on remote devices. 
          - creation of desirable end user experiences, optimization, pulse scheduling, and backend communication
          - Focused on hardware+backend
      - Ignis
        - Focused on fighting fires + errors
        - fixing/controlling quantum "errors"
        - designed around research for improving errors + noise in near-term quantum systems
          - Characterizing errors through tomography
            - AKA diagnostic imaging tool like x-rays, ultrasound, etc.
      - Aqua - "Water"
        - Focused more on building real world applications
        - This is where the algorithms for NISQ are built and used for quantum computing
        - accessible to domain experts in chemistry, AI, optimization, who look at using quantum computers as accelerators for specific computational tasks (without translating the problem into language of quantum machines)
      - Aer
        - Simulators, emulators, debuggers
        - built to help understand limits of classical processors/demonstrating to what extent they can mimic quantum computation. 
        - Used to verify current + near future quantum computers function correctly

    - **Getting started with Qiskit**
      - Just going to paste this here for now (https://qiskit.org/documentation/tutorials/circuits/1_getting_started_with_qiskit.html):
        - Fundamental unit of Qiskit is the **quantum circuit**
        - A basic workflow has 2 stages in Qiskit
          - `Build` - allows you to make quantum circuits that represent the problem you are solving
          - `Execute` - allows you to run them on different backends
        - after jobs have been run, data is collected + postprocessed depending on what our *desired* output is

        - ***NOTE:*** You need to have Anaconda installed. 

          - Python should be at least 3.6
          - Jupyter should also be installed by default
          - As well as matplotlib and their recommendations for visualization tools

        - Uh. Holy crap I need to take a course and learn some new math. Way beyond my skills at the moment. time to learn more. For reference, here was where I left off (was right around this part with building a circuit + circuit basics)
          ![image-20210813203212343](C:\Users\Blake\AppData\Roaming\Typora\typora-user-images\image-20210813203212343.png)
        - After this, you need to get an API key from IBM so you can query their quantum computer. Usually what you will do is run a simulation and then submit it to the supercomputer to run.
        - after you install anaconda, go to terminal and do a `pip install qiskit` 
        - now run jupyter notebook by typing `jupyter notebook`
        - I have notes for the code itself on my local copy
        - Do note you have to create an account on the IBM Quantum Experience website `quantum-computing.ibm.com`
    - **Quantum teleportation**
      - building a circuit on qiskit
      - is a Transfer of quantum states from one qubit to another. Does not mean physically transporting a qubit from one place to another.
        - transfer of quantum information from one qubit to another
      - but why do this?
        - well. because in quantum systems transferring by copying is not allowed. And this is because once you copy you are implicitly doing a measurement. And measurements destroy the quantum state that you're trying to transfer from one qubit to another
        - writing up notebook. initiated walkthrough.
    - **Bernstein-Vazirani Algorithm**
      - say there's a number in a box. and this number is described by 6 bits. so six strings of 0's and 1's. How many tries are needed to guess it correctly?
        - classical computers will need n-tries for n-bits. meaning that you will need 6 tries. Quantum system's can do this in 1 shot with the Bernstein-Vazirani algorithm.
        - say you have a secret number in  a box. This algorithim will be able to guess it.
        - {TODO: fill in rest this area on bernstein Vazirani}
          - [Bernstein-Vazirani Video](https://www.youtube.com/watch?v=sqJIpHYl7oo)
            - *R:* Bernstein-Vazirani algorithm. Didn't get much out of this video to be honest.
            - R: Good resource for Bernstein-Vazirani algorithm
              - [Bernstein-Vazirani GitHub](https://github.com/qiskit-community/qiskit-community-tutorials/blob/master/Coding_With_Qiskit/ep6_Bernstein-Vazirani_Algorithm.ipynb)
  - **Mitigating noise on quantum computers**
    - [Mitigating Noise Video](https://www.youtube.com/watch?v=yuDxHJOKsVA)
    - {TODO: Fill in mitigating noise section}

  

  

  ## **Unit 4 Bonus Sections:**

  - **Quantum Games**
    - [Quantum Games Video](https://www.youtube.com/watch?v=kmCSxfrK_Mg)
    - {TODO: fille in quantum games section}

  - **Contributing to Qiskit project**
    - you can contribute by going to this link [Qiskit Terra Repository](https://github.com/Qiskit/qiskit-terra)
      - click through issues and find one that you like and start contributing. do keep in mind that qiskit `Aer`, `Aqua` and `Ignis` also have their own repositories. I'm putting a list of all the repo's and where they can be found below:
        - [Qiskit Aer](https://github.com/Qiskit/qiskit-aer)
        - [Qiskit Aqua](https://github.com/Qiskit/qiskit-aqua)
        - [Qiskit Ignis](https://github.com/Qiskit/qiskit-ignis)
        - [Qiskit Terra... again here](https://github.com/Qiskit/qiskit-terra)
      - Do keep in mind that these instructions follow with the standards set with `Qiskit Terra`. Though they follow very similar patterns to contributing to other, non-related projects. Contributing is important to the qiskit/quantum computing community as a whole. Not only are you solving an issue within qiskit, but you're also solving it for the entire community.
        - Assignment: find an issue with the `good first issue` tag and work on it!
        -  watch this walkthrough: https://www.youtube.com/watch?v=QjZdvNgYl3s
          - make sure to generally ask permission to work on an issue before just jumping into it as well. You want to make sure that you're not stepping on someone's toes with an issue they've already been working on for a while.
      - {TODO: include steps on contributing. The above video gave good standards on how to contribute}
        - actually.... maybe include this lecture as a bonus instead of a requirement. It's important but not what I would call *absolutely* necessary. It's relatively advanced in comparison to some of the other essentials

  

  ---

  ## **Unit 5 Quantum Assignments (Assignments):

  - {TODO: Writeup assignments for each theory/ walkthrough section. a couple examples/ideas in bullets listed below}

    - Assignment 1 (Making a quantum circuit)
    - Assignment 2 (Contributing to the qiskit project + solving an issue or coding out a new feature)
    - Assignment 3 (Making a quantum game)
    - etc.

    

  ---

  

  ## Appendix of all Resources/links:

  - [Qiskit website](https://qiskit.org/)
  - [1 Minute Qiskit overview](https://qiskit.org/learn/?learnLevel=Beginner&timeScale=1%20minute)
  - [Qiskit medium article Overview](https://medium.com/qiskit/qiskit-and-its-fundamental-elements-bcd7ead80492)
  - [IBM Quantum Circuits Blog](https://www.ibm.com/blogs/research/2018/05/quantum-circuits/)
  - [Qiskit Documentation](https://qiskit.org/documentation/tutorials/circuits/1_getting_started_with_qiskit.html)
  - [Qiskit Online Video Series Jupyter Notebook, Bernstein-Vazirani Algorithm](https://github.com/qiskit-community/qiskit-community-tutorials/blob/master/Coding_With_Qiskit/ep6_Bernstein-Vazirani_Algorithm.ipynb)
  - [Quantum Games Video](https://www.youtube.com/watch?v=kmCSxfrK_Mg)
  - [Qiskit Aer Repository](https://github.com/Qiskit/qiskit-aer)
  - [Qiskit Aqua Repository](https://github.com/Qiskit/qiskit-aqua)
  - [Qiskit Ignis Repository](https://github.com/Qiskit/qiskit-ignis)
  - [Qiskit Terra Repository](https://github.com/Qiskit/qiskit-terra)



---

## Random:

- Other course ideas:
	- unity/ml-agents
	- screeps
	- crystal programming language 
	- blockchain/ ethereum smart contracts
	- basics of web apps for data scientist?
	- lambda labs might be something to check out


Resources built/based off of information from:

https://www.youtube.com/watch?v=mMwovHK2NrE&t=191s