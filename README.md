# Quantum Curriculum


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
		+ **MODEL VALIDATION:**
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
		+ overfitting and underfitting
		+ stochastic gradient descent
		+ activation functions
		+ backpropagation
		+ parameter tuning
	+  Computer Vision ?
		+ could possible break this out into it's own course all together
	+ Natural Language Processing ?
		+ could possibly break this out into it's own course all together
- **Unit 3 Quantum Theory**
	- **Quantum Computing**
		- **High level overview/ why important**
		- Information + Bits
		- Qubits 
		- Superpositioning
		- Quantum Entanglement
		- Superdense coding
		- Quantum Teleportation
		- Quantum Cryptography
		- Intro to Q#/ Qiskit
	- **Quantum Objects (this may not be required, could be bonus)**
		- High level overview/ why important
		- Observables
- **Unit 4 Quantum Toolsets (Q#/Qiskit portion of course)**
	- **Overview of Unit/Course**
	- **Project overview (maybe a crpyto cipher or something?)**
	- choose one of the following to teach/review:
		- qiskit
			- https://qiskit.org/
		- Or Quantum development kit (Q#)
			- https://azure.microsoft.com/en-us/resources/development-kit/quantum-computing/

- Other course ideas:
	- unity/ml-agents
	- screeps
	- crystal programming language 
	- basics of web apps for data scientist?
