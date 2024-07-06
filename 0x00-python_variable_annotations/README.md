```markdown
# ALX Backend Python - Variable Annotations

This repository contains various tasks related to Python variable annotations. Below is a list of the tasks and their descriptions.

## Tasks

### 0. Basic Annotations - Add
**File:** `0-add.py`
- **Description:** Write a type-annotated function `add` that takes two floats `a` and `b` and returns their sum as a float.
- **Usage:**
  ```python
  add = __import__('0-add').add
  print(add(1.11, 2.22) == 1.11 + 2.22)
  print(add.__annotations__)
  ```

### 1. Basic Annotations - Concat
**File:** `1-concat.py`
- **Description:** Write a type-annotated function `concat` that takes two strings `str1` and `str2` and returns a concatenated string.
- **Usage:**
  ```python
  concat = __import__('1-concat').concat
  print(concat("egg", "shell") == "eggshell")
  print(concat.__annotations__)
  ```

### 2. Basic Annotations - Floor
**File:** `2-floor.py`
- **Description:** Write a type-annotated function `floor` that takes a float `n` and returns the floor of the float as an integer.
- **Usage:**
  ```python
  floor = __import__('2-floor').floor
  print(floor(3.14) == 3)
  print(floor.__annotations__)
  ```

### 3. Basic Annotations - To String
**File:** `3-to_str.py`
- **Description:** Write a type-annotated function `to_str` that takes a float `n` and returns the string representation of the float.
- **Usage:**
  ```python
  to_str = __import__('3-to_str').to_str
  pi_str = to_str(3.14)
  print(pi_str == str(3.14))
  print(to_str.__annotations__)
  ```

### 4. Define Variables
**File:** `4-define_variables.py`
- **Description:** Define and annotate variables:
  - `a`: an integer with value `1`
  - `pi`: a float with value `3.14`
  - `i_understand_annotations`: a boolean with value `True`
  - `school`: a string with value `"Holberton"`
- **Usage:**
  ```python
  a = __import__('4-define_variables').a
  pi = __import__('4-define_variables').pi
  i_understand_annotations = __import__('4-define_variables').i_understand_annotations
  school = __import__('4-define_variables').school
  ```

### 5. Complex Types - List of Floats
**File:** `5-sum_list.py`
- **Description:** Write a type-annotated function `sum_list` that takes a list of floats `input_list` and returns their sum as a float.
- **Usage:**
  ```python
  sum_list = __import__('5-sum_list').sum_list
  print(sum_list([3.14, 1.11, 2.22]) == 6.47)
  print(sum_list.__annotations__)
  ```

### 6. Complex Types - Mixed List
**File:** `6-sum_mixed_list.py`
- **Description:** Write a type-annotated function `sum_mixed_list` that takes a list of integers and floats `mxd_lst` and returns their sum as a float.
- **Usage:**
  ```python
  sum_mixed_list = __import__('6-sum_mixed_list').sum_mixed_list
  print(sum_mixed_list([5, 4, 3.14, 666, 0.99]) == 679.13)
  print(sum_mixed_list.__annotations__)
  ```

### 7. Complex Types - String and Int/Float to Tuple
**File:** `7-to_kv.py`
- **Description:** Write a type-annotated function `to_kv` that takes a string `k` and an int/float `v` and returns a tuple. The first element is `k`, and the second element is the square of `v` as a float.
- **Usage:**
  ```python
  to_kv = __import__('7-to_kv').to_kv
  print(to_kv("eggs", 3))
  print(to_kv("school", 0.02))
  print(to_kv.__annotations__)
  ```

### 8. Complex Types - Functions
**File:** `8-make_multiplier.py`
- **Description:** Write a type-annotated function `make_multiplier` that takes a float `multiplier` and returns a function that multiplies a float by `multiplier`.
- **Usage:**
  ```python
  make_multiplier = __import__('8-make_multiplier').make_multiplier
  print(make_multiplier(2.22)(2.22) == 4.9284)
  print(make_multiplier.__annotations__)
  ```

### 9. Let's Duck Type an Iterable Object
**File:** `9-element_length.py`
- **Description:** Annotate a function's parameters and return values with appropriate types.
- **Usage:**
  ```python
  element_length = __import__('9-element_length').element_length
  print(element_length.__annotations__)
  ```

### 10. Duck Typing - First Element of a Sequence
**File:** `100-safe_first_element.py`
- **Description:** Augment the function with correct duck-typed annotations.
- **Usage:**
  ```python
  safe_first_element = __import__('100-safe_first_element').safe_first_element
  print(safe_first_element.__annotations__)
  ```

### 11. More Involved Type Annotations
**File:** `101-safely_get_value.py`
- **Description:** Add type annotations to a function using TypeVar.
- **Usage:**
  ```python
  safely_get_value = __import__('101-safely_get_value').safely_get_value
  print(safely_get_value.__annotations__)
  ```

### 12. Type Checking
**File:** `102-type_checking.py`
- **Description:** Use `mypy` to validate and apply necessary changes.
- **Usage:**
  ```python
  zoom_array = __import__('102-type_checking').zoom_array
  print(zoom_array.__annotations__)
  ```

## Repository Structure

```plaintext
.
├── 0-add.py
├── 1-concat.py
├── 2-floor.py
├── 3-to_str.py
├── 4-define_variables.py
├── 5-sum_list.py
├── 6-sum_mixed_list.py
├── 7-to_kv.py
├── 8-make_multiplier.py
├── 9-element_length.py
├── 100-safe_first_element.py
├── 101-safely_get_value.py
├── 102-type_checking.py
├── README.md
```

## How to Run

1. Clone the repository:
    ```sh
    git clone https://github.com/your-username/alx-backend-python.git
    cd alx-backend-python/0x00-python_variable_annotations
    ```

2. Run the individual task files:
    ```sh
    python3 0-main.py
    python3 1-main.py
    # and so on...
    ```

## Author
Ian Wainaina Kamau
```

