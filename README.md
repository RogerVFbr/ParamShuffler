# Parameter Shuffler

Python script to execute a function under multiple combination of parameters and store or provide results 
in an organized way. Makes use of Python's **multiprocessing** module for speed and **tqdm** module for progress 
monitoring.  

## Getting Started

### Prerequisites

Have Python 3 installed and pip install TQDM module (https://tqdm.github.io/) by running the following on your 
computer's command line terminal:

```
pip install tqdm
```

### Installing

Just copy the **param_shuffler.py** file to you project folder and import the module by typing the following line on top
of the project file you wish to use it on:

```
import ParamShuffler
```

## Usage

### 0. Define a function to be tested

Typically, you will use this module to test a function under multiple parameter combinations and later interpret the 
results. Let's define a simple function with 2 parameters, **a** and **b**:

```
def test_function(a, b):
    return a * b
```

### 1. Instantiate a ParamShuffler module

Instantiate a ParamShuffler module by passing the function object you wish to test and assigning it to a variable (ps). 
Remember **not** to use opening and closing parenthesis after passing the function.

```
ps = ParamShuffler(test_function)
```

### 2. Create parameter combination dictionary

Create a dictionary where the keys must correspond to the function parameter names. The dictionary values must contain 
the iterables that will provide the parameter combinations to be used on the function executions.

```
params = {
    'a': range(1, 4), 
    'b': [5, 9, 11]
}
```

### 3. Run ParamShuffler

Run the given method against all possible parameter combinations provided and return a **list of dicionaries**: 

```
results = ps.run(params)
```
Each dictionary will contain the parameter combination used on the execution and it's associated result. Each 
dictionary key corresponds to a parameter as configured in the parameter combination dictionary, plus a 'result' key
that will contain the associated function output.

### 4. Print formatted *(optional)*

Use the built-in **print** function to visualize the resulting data in table form:

```
ps.print(results)

Outputs:

╔═════╦══════╦══════════╗
║  a  ║  b   ║  result  ║
╠═════╬══════╬══════════╣
║  1  ║  5   ║  5       ║
║  1  ║  9   ║  9       ║
║  1  ║  11  ║  11      ║
║  2  ║  5   ║  10      ║
║  2  ║  9   ║  18      ║
║  2  ║  11  ║  22      ║
║  3  ║  5   ║  15      ║
║  3  ║  9   ║  27      ║
║  3  ║  11  ║  33      ║
╚═════╩══════╩══════════╝
```

### 5. Save results *(optional)*

Save the acquired data to a **csv file** for later analysis:

```
ps.save_to_csv(results)
```

## Authors

* **Roger Freret** - [Github](https://github.com/RogerVFbr)

