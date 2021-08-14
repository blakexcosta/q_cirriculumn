# Quantum Curriculum Draft


- Please note this is just MY notes on subject material and resources I felt are good at describing the topics at hand
- **Unit 1 Data Science Fundamentals**
	- **Unit/Course Overview**
	- **Project overview**
	- Jupyter
		- Anaconda Navigator installation:
	- Python
	- Numpy
	- Pandas
	- matplotlib
-  **Unit 2 Machine Learning/Deep Learning FUNdamentals**
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
- **Unit 3 Quantum Theory + Computing Background** 

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
  - **Installing Qiskit**
    - 
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

- **Unit 4 Quantum Toolsets (Q#/Qiskit portion of course)**

  - **Overview of Unit/Course**

    - 

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

          - **Build** - allows you to make quantum circuits that represent the problem you are solving
          - **Execute** - allows you to run them on different backends

        - after jobs have been run, data is collected + postprocessed depending on what our *desired* output is

        - ***NOTE:*** You need to have Anaconda installed. 

          - Python should be at least 3.6
          - Jupyter should also be installed by default
          - As well as matplotlib and their recommendations for visualization tools

        - Uh. Holy crap I need to take a course and learn some new math. Way beyond my skills at the moment. time to learn more. For reference, here was where I left off (was right around this part with building a circuit + circuit basics)

          ![image-20210813203212343](C:\Users\Blake\AppData\Roaming\Typora\typora-user-images\image-20210813203212343.png)

          

  - **Project overview (maybe a crpyto cipher or something?)**

  - choose one of the following to teach/review:
  	- qiskit 
  		- https://qiskit.org/
  	- Or Quantum development kit (Q#)
  		- https://azure.microsoft.com/en-us/resources/development-kit/quantum-computing/
  	
  - Resources/links:

    + https://qiskit.org/

    - https://qiskit.org/learn/?learnLevel=Beginner&timeScale=1%20minute
    - https://medium.com/qiskit/qiskit-and-its-fundamental-elements-bcd7ead80492
    - https://www.ibm.com/blogs/research/2018/05/quantum-circuits/
    - https://qiskit.org/documentation/tutorials/circuits/1_getting_started_with_qiskit.html

    

- Other course ideas:
	- unity/ml-agents
	- screeps
	- crystal programming language 
	- basics of web apps for data scientist?
